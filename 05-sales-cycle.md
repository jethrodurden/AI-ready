# 05 — The Full Sales Cycle

**Rule of thumb:** AI does the research, writing, triage, intake, and admin. **Humans own every
conversation where trust or money is decided:** the readout, the proposal, and the negotiation.

## 1. Funnel overview

```
 ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌───────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐
 │ 1 TARGET │→ │2 ENGAGE  │→ │3 QUALIFY │→ │4 READINESS│→ │5 READOUT │→ │6 PROPOSE │→ │7 CLOSE   │→ │8 EXPAND  │
 │ & RESEARCH│ │(SDR/BDR) │  │ (BANT-AI)│  │  CHECK    │  │(+Blueprint│ │& NEGOTIATE│ │& ONBOARD │  │(ladder up)│
 └──────────┘  └──────────┘  └──────────┘  └───────────┘  └──────────┘  └──────────┘  └──────────┘  └──────────┘
   AI agent      AI + Beto      AI agent     Analyst + AI    Beto           Beto + AI      Beto           AM + AI
                 (LinkedIn)                                               (draft)
```

## 2. Stage definitions

| # | Stage | Owner | Entry criteria | Key activities | Exit criteria | SLA |
|---|-------|-------|----------------|----------------|---------------|-----|
| 1 | **Target & Research** | 🤖 Research agent | Account matches ICP (fit ≥ 50) | Pull Apollo firmographics/technographics; crawl help center and site chatbot; check WhatsApp; job posts; compute fit score and **outside-in readiness pre-score**; pick 2–3 contacts | Account + contacts in HubSpot with research brief | Weekly batch |
| 2 | **Engage** | 🤖 SDR agent (email) + 👤 Beto (LinkedIn, priority accounts) | Research brief exists | 4-touch email sequence, 2 LinkedIn touches, optional call or WhatsApp after opt-in. See [07](07-outbound-playbook.md) | Positive reply, scorecard completed, or meeting booked | Reply triage < 2 business hours |
| 3 | **Qualify** | 🤖 Qualification agent (web/WhatsApp/email) | Positive reply or inbound lead | Run lite scorecard questions, confirm gate (volume ≥ 5k or ≥ 10 agents), identify role/authority, book intake | Qualified → **Readiness Check Scheduled**; not qualified → self-serve + nurture | Same day |
| 4 | **Readiness Check** | 👤 Analyst + 🤖 analysis assist | Intake booked, decision-maker identified | 45-min intake; questionnaire; KB/ticket sample audit; AI clustering of ticket sample | Score + gap list + recommendation ready | ≤ 10 business days |
| 5 | **Readout** | 👤 Beto | Scorecard complete | 45-min readout: score, top 5 gaps, "if you launched a bot tomorrow", recommended path, investment range | Client agrees to a proposal for Tier 1 or Foundations | Proposal ≤ 48h after readout |
| 6 | **Propose & Negotiate** | 👤 Beto (🤖 drafts proposal/SOW) | Agreed next step | Proposal built from template + readout data; pricing per [04](04-pricing.md); handle objections | Verbal yes | 2–3 weeks |
| 7 | **Close & Onboard** | 👤 Beto + 👤 Delivery lead | Verbal yes | Contract/SOW, kickoff, access requests, project plan | Kickoff held | Kickoff ≤ 10 days after signature |
| 8 | **Expand** | 👤 Account manager + 🤖 monitoring | Tier delivered | Tier exit-gate review; usage/performance signals trigger the next-tier proposal | Next-tier deal created | QBR every quarter |

## 3. Qualification framework: "BANT-AI"

Used by the qualification agent and in human calls. Each item is scored 0–2. **≥ 7 of 10 means sales-qualified.**

| Letter | Question | 2 points | 1 point | 0 points |
|--------|----------|----------|---------|----------|
| **B**udget | Is there budget or pressure to cut CX cost / fund AI this year? | Budget/initiative exists | Exploring | None |
| **A**uthority | Is the contact the CX/Ops decision-maker or a direct report? | DM | Champion with DM access | Neither |
| **N**eed | How many contacts per month, and what's the main pain? | ≥ 10k + clear pain | 5–10k | < 5k |
| **T**iming | When do they want AI or a fix in production? | < 6 months | 6–12 months | No plan |
| **AI** status | Do they have a CRM/KB, and have they tried AI? | CRM + tried AI (underwhelmed) | CRM, no AI yet | No CRM |

> An "AI tried and underwhelmed" lead is the **best** lead. They've already experienced the problem
> our Readiness Check diagnoses.

## 4. HubSpot configuration

### Pipelines
**Pipeline A, "AI-Ready" (new business):**
`Lead Researched → In Sequence → Engaged → Qualified (SQL) → Readiness Check In Progress → Readout Delivered → Proposal Sent → Negotiation → Closed Won – Tier X → Closed Lost`

**Pipeline B, "Expansion" (existing accounts):**
`Readiness Check Offered → Check In Progress → Readout Delivered → Blueprint Proposed → Blueprint Won → Build Proposed → Build Won → Care Active → Hybrid Ops Proposed → Hybrid Ops Won`

Deal types: `Tier0-Check` ($0, tracked for conversion), `Foundations`, `Tier1-Blueprint`, `Tier2-Build`,
`Care-Retainer` (recurring), `Tier3-HybridOps` (recurring), `BPO-Seats` (legacy).

### Custom properties
**Company**
| Property | Type | Source |
|----------|------|--------|
| `icp_fit_score` | Number 0–100 | Research agent |
| `outside_in_readiness` | Number 0–100 | Research agent |
| `helpdesk_platform` | Dropdown | Apollo + research |
| `native_ai_status` | Dropdown: none / licensed-off / live-weak / live-strong / unknown | Research + qualification |
| `public_kb_url` / `kb_article_count` / `kb_pct_stale_12m` | URL / Number / % | Research agent |
| `whatsapp_bot_present` | Bool | Research agent |
| `est_monthly_contacts` | Number | Research → confirmed at qualification |
| `buying_signals` | Multi-select | Research agent |
| `research_brief` | Rich text | Research agent |

**Contact**
| Property | Type |
|----------|------|
| `persona` | Dropdown: P1 economic / P2 champion / P3 technical / P4 finance |
| `scorecard_lite_answers` | Text (JSON) |
| `readiness_band` | Dropdown: AI-Ready / Ready with prep / Foundations first / Not ready |
| `bant_ai_score` | Number 0–10 |
| `last_ai_touch_summary` | Text |

**Deal**
| Property | Type |
|----------|------|
| `readiness_score_full` | Number |
| `pillar_a_score` / `pillar_b_score` | Number |
| `top_gaps` | Text |
| `recommended_path` | Dropdown |
| `projected_containment` / `baseline_cost_per_contact` | % / Currency |

### Lead scoring (HubSpot score property)
- +20 completed the self-serve scorecard · +15 replied positively · +10 band "Ready with prep" or
  "AI-Ready" · +10 persona P1 · +10 ICP fit ≥ 70 · +5 per pricing/site visit (max 15) · −20 persona
  not P1–P4 · −30 company < 50 employees
- **MQL ≥ 40, then the qualification agent reaches out. SQL means BANT-AI ≥ 7.**

### Automations (HubSpot workflows)
1. New company with `icp_fit_score ≥ 50` → add to Apollo sequence (Standard or Priority by score).
2. Reply classified *Interested* → create deal at *Engaged* → notify Beto in Slack/WhatsApp.
3. Scorecard submitted → set `readiness_band` → if gate met, send booking link for the full check;
   otherwise, nurture.
4. Deal enters *Readout Delivered* → task: proposal within 48h → AI drafts proposal from deal properties.
5. Deal *Closed Won Tier N* → create *Expansion* deal for Tier N+1 with a close date at the tier's exit gate.
6. Existing client renewal 90 days out → create *Readiness Check Offered* deal.

## 5. Funnel targets (first 90 days, steady state)

| Metric | Target |
|--------|--------|
| Accounts researched / month | 100 |
| Contacts in sequence / month | 250 |
| Reply rate (any) | ≥ 6% |
| Positive reply rate | ≥ 2% |
| Self-serve scorecard completions / month | 30 |
| Readiness Checks started / month | 6–8 (incl. existing clients) |
| Check → Readout show rate | ≥ 85% |
| Readout → paid proposal accepted | ≥ 40% |
| Average first paid deal (Blueprint/Foundations) | $8–12k |
| Paid → Build conversion (within 90 days) | ≥ 50% |
| Sales cycle, first touch → first paid | ≤ 60 days |

## 6. Objection handling (cheat sheet)

| Objection | Response |
|-----------|----------|
| "We already have AI in Zendesk/Intercom." | "Great, then the check is even faster. Most teams with native AI see about 20% containment because the KB wasn't written for AI. We'll show you where yours is losing contacts." |
| "We're building in-house." | "Then you'll want the Blueprint and AI-friendly process maps anyway. We're tech-agnostic, and our human layer takes what your bot escalates." |
| "You're a BPO. Why would you reduce your own seats?" | "Because we're paid per resolution, not per seat. Our margin goes up when AI works. Here's the math." |
| "AI will hallucinate with our customers." | "That's exactly why we score every contact for consequence-of-error before automating it, and why disputes, hardship, and KYC stay human." |
| "No budget." | "The check is free and takes about 2 hours of your team's time. If the gaps aren't worth fixing, you'll know that too." |
| "Send me info." | "I'll send you your outside-in readiness pre-score. We already ran it on your public help center." |
