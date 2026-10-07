# 06 — The AI SDR / BDR / Qualification Agent System

We sell AI readiness, so our own funnel should run on AI that we built. That way every prospect
conversation doubles as a demo: *"The email you replied to was researched and written by the same kind
of agent we'd build for you, and a human (me) reviewed it."*

## 1. Architecture

```
                         ┌──────────────────────────────────────────┐
                         │                 HUBSPOT                   │
                         │   system of record: companies, contacts,  │
                         │   deals, properties, tasks, timeline      │
                         └───────▲──────────────▲──────────────▲─────┘
                                 │              │              │
   ┌─────────────┐   ┌───────────┴───┐   ┌──────┴───────┐   ┌──┴────────────┐
   │   APOLLO    │──►│ 1 RESEARCHER  │──►│ 2 SDR WRITER │──►│ APOLLO        │──► prospect inbox
   │ search +    │   │ (BDR research)│   │ (sequences)  │   │ SEQUENCES     │
   │ enrichment  │   └───────────────┘   └──────────────┘   │ (send, track) │
   └─────────────┘           ▲                              └──────┬────────┘
         web, help center,   │                                     │ replies
         job posts, WhatsApp │                              ┌──────▼────────┐
                             │                              │ 3 REPLY TRIAGE│──► Beto (Slack/WA)
                             │                              └──────┬────────┘
   website / WhatsApp ──────────────────────────────────────►┌──────▼────────┐
   self-serve scorecard                                      │ 4 QUALIFIER   │──► books meeting
                                                             │ (concierge)   │    (HubSpot Meetings)
                                                             └──────┬────────┘
                                                             ┌──────▼────────┐   ┌───────────────┐
                                                             │ 5 MEETING PREP│──►│ 6 PROPOSAL    │
                                                             │ & CRM SCRIBE  │   │   DRAFTER     │
                                                             └───────────────┘   └───────────────┘
                                   ┌───────────────────────────┐
                                   │ 7 PIPELINE MONITOR (daily)│ stale deals, SLAs, nudges
                                   └───────────────────────────┘
```

**Build stack (recommended)**
- **Orchestration:** n8n (self-hosted or cloud) for schedules, webhooks, and Apollo/HubSpot nodes, with
  the agent logic in small Python services. Or run everything as Python using the Claude Agent SDK if
  you'd rather keep it all in code.
- **Models:** Claude Sonnet 5.5 for research synthesis and writing. Claude Haiku 4.5 for high-volume
  classification (reply triage, tagging). Claude Opus 5.5 for proposals and readout drafts.
- **Data:** Apollo API (organization/people search, enrichment, add-to-sequence) and HubSpot API
  (CRM objects, notes, tasks, workflows, meetings). Web fetching for help centers and websites.
- **Channels:** Apollo sequences on **secondary sending domains** (see [07 §1](07-outbound-playbook.md#1-deliverability-protect-it-before-scaling-volume)).
  WhatsApp Business API for opted-in leads only. Web chat widget on evolvecx.io.
- **Logs:** every agent writes a timeline note to HubSpot, so you can see what it did and why.

## 2. The seven agents

### 1) Researcher (BDR research): *"know the account before we touch it"*
- **Trigger:** weekly batch of new Apollo accounts that match the ICP filters ([02 §5](02-icp.md#5-apollo-search-recipes)).
- **Does:**
  1. Enriches the company (size, industry, country, funding, technologies, job postings).
  2. Finds the help center (`help.`, `ayuda.`, `soporte.`, `/faq`, Zendesk/Intercom/Freshdesk-hosted),
     counts articles, samples "last updated" dates, and flags contradictions or very long articles.
  3. Checks for a site chatbot (vendor and behavior) and a WhatsApp entry point.
  4. Scans job posts for CX roles (a volume signal) and AI/automation roles (an intent signal).
  5. Computes the `icp_fit_score` ([02 §4](02-icp.md#4-account-fit-score-0100-used-by-the-ai-research-agent))
     and an **outside-in readiness pre-score**, the public-evidence subset of the scorecard.
  6. Picks 2–3 contacts (P1 + P2) and writes a 5-bullet research brief with sources.
- **Writes:** company and contact properties plus `research_brief` in HubSpot.
- **Prompt:** [agents/01-researcher.md](agents/01-researcher.md)

### 2) SDR Writer: *"give first, ask small"*
- **Trigger:** company has `icp_fit_score ≥ 50` and a research brief.
- **Does:** writes a 4-step email sequence plus 2 LinkedIn messages per contact, in the contact's
  language (es-MX or en-US), built on **one specific finding** from the research brief (for example,
  "38% of your help-center articles haven't been updated since 2024").
- **Human-in-the-loop:** for the first 2 weeks, Beto approves 100% of messages (approval queue as
  HubSpot tasks). After that, Standard accounts auto-send. Priority accounts (fit ≥ 70) are always reviewed.
- **Prompt:** [agents/02-sdr-writer.md](agents/02-sdr-writer.md)

### 3) Reply Triage: *"no reply waits more than 2 hours"*
- **Trigger:** a new reply in Apollo/inbox.
- **Classifies:** `interested` · `question` · `objection` · `referral` (talk to X) · `not_now` (date) ·
  `not_interested` · `unsubscribe` · `ooo` · `bounce`.
- **Does:** updates HubSpot. Stops the sequence on any human reply. Drafts a response (never auto-sent
  for `interested` / `objection`; Beto sends). Handles `unsubscribe` and `ooo` automatically. Creates the
  referral contact and drafts the intro. Schedules `not_now` follow-ups.
- **Prompt:** [agents/03-reply-triage.md](agents/03-reply-triage.md)

### 4) Qualifier (concierge on web chat, WhatsApp, and email): *"the Readiness Check starts here"*
- **Trigger:** an inbound chat or WhatsApp opt-in, a scorecard submission, or a positive reply handed
  over from triage.
- **Does:** runs the **lite AI Readiness Scorecard** conversationally (8 questions), computes the band,
  checks the Tier 0 gate and BANT-AI, answers FAQs from an approved knowledge file (this agent uses
  our own AI-friendly Process Records), and books the intake through HubSpot Meetings. Discloses that
  it's an AI assistant. Hands off to Beto on request or when stakes are high (pricing negotiation,
  complaints, existing clients).
- **Prompt:** [agents/04-qualifier.md](agents/04-qualifier.md)

### 5) Meeting Prep & CRM Scribe
- **Before each meeting:** a one-page brief to Beto (account, people, research, scorecard answers,
  hypotheses on the top 3 gaps, suggested questions, likely objections).
- **After each meeting:** turns the transcript/notes (from Google Meet + Gemini notes, or
  Fireflies/Granola) into HubSpot updates: deal stage, BANT-AI, next steps, tasks, and the follow-up
  email draft.

### 6) Proposal Drafter
- **Trigger:** deal enters *Readout Delivered*.
- **Does:** fills the proposal/SOW template from deal properties (score, gaps, recommended path,
  sizing) and the pricing rules in [04-pricing.md](04-pricing.md). It can't invent discounts. Anything
  outside the rate card is flagged for Beto.
- **Prompt:** [agents/05-proposal-drafter.md](agents/05-proposal-drafter.md)

### 7) Pipeline Monitor
- **Daily:** flags deals with no activity beyond the stage SLA ([05 §2](05-sales-cycle.md#2-stage-definitions)),
  missing next steps, readouts without proposals after 48h, and existing clients near renewal without
  a Readiness Check. Sends a 5-line morning digest to Beto.

## 3. Guardrails (non-negotiable)

| Guardrail | Rule |
|-----------|------|
| **Truthfulness** | Every claim about a prospect must trace back to a source in the research brief. No source, no claim. Our own proof points come only from the approved list (agents/proof-points.md) |
| **AI disclosure** | The concierge identifies itself as EvolveCX's AI assistant. Emails are sent under Beto's name, which he approves and owns |
| **Consent & compliance** | Opt-out in every email. Honor it immediately, globally, in HubSpot. WhatsApp only after opt-in. Follow CAN-SPAM, Mexico's LFPDPPP, and the local rules of each target country. No scraping of personal data beyond business contact information |
| **Pricing** | Agents can quote only published rate-card ranges. Discounts and custom terms go to a human |
| **Volume caps** | ≤ 40 new contacts/day per sending inbox, sequence steps ≥ 3 business days apart |
| **Escalation** | Existing clients, complaints, legal or security questions, and anything about a contract go to Beto immediately |
| **Logging** | Every agent action is logged to the HubSpot timeline with the prompt version |

## 4. Rollout

| Week | Milestone |
|------|-----------|
| 1 | Deliverability setup (domains, warm-up). HubSpot properties and pipelines. Approved proof points list |
| 2 | Researcher live on 50 accounts. Manual review of briefs for quality |
| 3 | SDR Writer live with 100% human approval. Reply Triage live |
| 4 | Self-serve scorecard + Qualifier on the website. WhatsApp opt-in flow |
| 5–6 | Meeting Prep + CRM Scribe. Proposal Drafter |
| 7+ | Auto-send for Standard accounts. Pipeline Monitor. Weekly prompt iteration from reply data |

## 5. How we measure the agents

| Agent | KPI |
|-------|-----|
| Researcher | % of briefs rated "accurate & useful" by Beto (target ≥ 90%); research cost/account |
| SDR Writer | Reply rate, positive reply rate, % of drafts approved without edits |
| Reply Triage | Classification accuracy on a weekly sample (≥ 95%); median time-to-response |
| Qualifier | Scorecard completion rate; booked intakes; show rate; handoff appropriateness |
| Proposal Drafter | % of proposals sent with minor edits only; time from readout to proposal |

> The agent metrics are also a sales asset: *"Our concierge qualifies X% of inbound without a human."*
