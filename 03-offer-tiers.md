# 03 — Offer Architecture: the AI-Ready Ladder

```
            ┌───────────────────────────────────────────────────────────────┐
 TIER 3     │  HYBRID OPERATIONS — AI + human layer, priced per outcome     │  ongoing
            ├───────────────────────────────────────────────────────────────┤
 TIER 2     │  BUILD & LAUNCH — dual process maps, bots (WhatsApp/voice),    │  project
            │  fine-tuning, launch   ──►  + KB & BOT CARE retainer           │  + monthly
            ├───────────────────────────────────────────────────────────────┤
 TIER 1     │  AUTOMATION BLUEPRINT — which contacts to automate, which      │  project
            │  need humans, which technology                                 │
            ├───────────────────────────────────────────────────────────────┤
 TIER 0     │  AI READINESS CHECK — processes + systems score (free)         │  free
            └───────────────────────────────────────────────────────────────┘
   side path:  FOUNDATIONS — KB & process rebuild for clients who score "not ready"
```

Each tier has a **gate**. A client moves up only when the previous tier's exit criteria are met. That
protects delivery quality (no bot gets built on a broken KB) and keeps the ladder honest.

---

## Tier 0: AI Readiness Check (free)

**Promise:** "In 10 business days you'll know whether your CX operation is AI-ready, what's blocking
it, and what to do first."

**Scope.** Two pillars, scored with the [AI Readiness Scorecard](frameworks/ai-readiness-scorecard.md):

| Pillar A: Documented processes (Knowledge) | Pillar B: Systems & data |
|---|---|
| Is there a KB? Is it operational (used daily by agents, searchable, owned)? | Is there a CRM/helpdesk? Which one? |
| What % of contact reasons have a documented process? | Are contacts tagged by reason? How clean is the tagging? |
| How often do processes change? | How much history exists (months and number of conversations) to mine intents and build test sets? |
| When a process changes, does the KB get updated? How fast, and who owns it? | Does the CRM have native AI? Is it licensed? Is it on? What's the containment? |
| Are there contradictions between the KB, macros, and what agents actually do? | Are the systems that bots need to *act* in (order status, payments, accounts) accessible via API? |

**How we deliver it**
1. 45-minute intake call, or the intake run by the AI qualification agent (see [06](06-ai-sales-agent.md))
2. Client completes the scorecard questionnaire (about 20 minutes)
3. Optional but encouraged: read-only access or an export of 1 month of tickets plus the KB
4. EvolveCX analyst sample-audits 20 KB articles and 100 tickets
5. 45-minute readout with Beto: score, top 5 gaps, recommended next step

**Deliverables:** Readiness Score (0–100) with a per-pillar breakdown, a one-page gap list, and a
recommended path: *Ready* → Tier 1 · *Ready with prep* → Foundations + Tier 1 · *Not ready* →
Foundations.

**Gate (who qualifies for the free check):** ≥ 5,000 contacts/month **or** ≥ 10 agents, and a
decision-maker attends the readout. Everyone else gets the **self-serve online scorecard**: a lite
version with instant results, used as a lead magnet.

**Effort cap:** about 12 analyst hours. If the client wants deeper analysis, it becomes a paid Tier 1.

---

## Side path: Foundations (KB & process rebuild)

For clients who score *Not ready* or *Ready with prep*. **This is where the "not ready" answer still
turns into revenue.** It's also a BPO strength we already list on the one-pager ("we build KBs and
process documentation from scratch").

- Audit and restructure the KB (dedupe, fix contradictions, set ownership)
- Map the top N contact reasons using the dual-mapping method
- Set up KB governance: change-request flow, owners, review cadence, freshness SLAs
- Clean up tagging and dispositions in the CRM so future data is usable

Priced per process mapped plus a governance setup fee. See [04-pricing.md](04-pricing.md).

---

## Tier 1: Automation Blueprint (project)

**Promise:** "A contact-by-contact plan for what AI should handle, what it should assist with, what
stays human, and on which technology. With the business case."

**Entry gate:** Readiness Score ≥ 60, or Foundations completed.

**Scope**
1. **Intent discovery.** Mine 3–6 months of tickets and conversations and cluster them into contact
   reasons (LLM-assisted clustering plus human validation). Output: the top 20–40 reasons, covering
   about 80% of volume, with volume share, AHT, CSAT, and re-contact rate.
2. **Automation Suitability scoring.** Score each reason on volume, decision determinism, customer
   effort, customer impact, brand/relationship risk, hallucination tolerance, data/action access,
   and process stability. See the [Automation Suitability Matrix](frameworks/automation-suitability-matrix.md).
   Each reason gets a mode:
   - **A, AI resolves:** binary, rule-based, high-volume, low consequence
   - **B, AI with guardrails:** AI resolves but confirms, cites the source, or needs approval for actions
   - **C, AI assists a human:** copilot drafts, summarizes, retrieves; a human decides
   - **D, Human-led:** high impact, judgment, emotion, regulatory
3. **Technology selection** per use case: (1) the client's native CRM AI, (2) an EvolveCX build,
   (3) the client's in-house development, or a combination. Uses the decision tree in the matrix doc.
4. **Business case:** projected containment by wave, cost per contact before and after, CSAT
   guardrails, staffing curve.
5. **Roadmap:** Wave 1 (quick wins, mode A, 4–6 weeks), Wave 2 (mode B), Wave 3 (voice / complex).

**Deliverables:** Blueprint deck + suitability matrix (spreadsheet) + tech recommendation + Tier 2 SOW.

**Duration:** 2–4 weeks depending on the number of channels and reasons.

**Exit gate to Tier 2:** Client approves the Wave 1 scope, a tech path is chosen, API/sandbox access
is confirmed for the needed actions, and a client process owner is named.

---

## Tier 2: Build & Launch (project), then KB & Bot Care (retainer)

**Promise:** "Your processes mapped twice, once for the AI and once for your people, and bots live on
WhatsApp, chat, or voice, tuned until they hit the agreed containment and quality bar."

**Scope**
1. **Dual Process Mapping** for every in-scope reason. See [frameworks/dual-process-mapping.md](frameworks/dual-process-mapping.md):
   - **AI-friendly map:** atomic, structured, explicit preconditions, decision tables, allowed actions,
     forbidden statements, escalation triggers, canonical answers. Built to reduce hallucinations.
   - **Human-friendly map:** step-by-step SOP with context, the "why", screenshots, examples, and tone
     guidance. Built for training and ramp.
   - Both are generated from **one source of truth**, so they never drift apart.
2. **Bot build:**
   - **Text:** WhatsApp Business API, web chat, in-app, email auto-resolution
   - **Voice:** inbound IVR replacement / voicebot with natural turn-taking, handoff to a human with
     context
   - Integrations for actions (look-ups and transactions), authentication flows, and handoff with full
     context to the human layer
3. **Evaluation & fine-tuning:**
   - Build a **test set** from real historical conversations (≥ 200 per intent group)
   - Measure resolution accuracy, groundedness (answers only from approved content), policy compliance,
     tone, escalation correctness
   - Iterate on prompts, retrieval, KB content, and guardrails until the launch bar is met
4. **Launch:** shadow mode (AI drafts, humans send), then a canary of 10% of traffic, then 50%, then
   100% of in-scope intents. Includes 30 days of hypercare.
5. **Change management:** agent training on the new flows and the human-friendly SOPs.

**Launch bar (default, adjustable in the SOW):** ≥ 90% correct resolution on the test set, ≥ 98%
groundedness, 0 critical policy violations, CSAT for AI-resolved conversations no worse than 5 points
below the human baseline.

### KB & Bot Care (retainer, starts at go-live)
Bots decay when processes change. Care keeps the KB and the bots aligned:
- Process change intake (SLA: change live in 48h standard, 24h urgent)
- Weekly conversation review: hallucination and escalation audits, gap mining, new intents
- Monthly performance report: containment, accuracy, CSAT, top failure reasons
- Quarterly optimization sprint: move the next intents from mode C to B or from B to A

---

## Tier 3: Hybrid Operations (AI + humans, per outcome)

**Promise:** "One partner for every contact. AI resolves what it should, and our bilingual team
resolves the rest in the same conversation, with full context. You pay per resolved contact."

**Scope:** everything in Tier 2 plus Care, plus:
- The human layer: EvolveCX agents handle mode C/D contacts and every AI escalation
  (chat, WhatsApp, voice, email, back-office, KYC, collections)
- A single queue and routing design: AI first, then human with the context passed along
- Combined QA: AI-assisted QA across 100% of conversations, both bot and human
- Workforce management sized to the residual volume, which shrinks as containment grows
- Joint quarterly business review: containment roadmap, cost per contact, CSAT

**Pricing:** per resolved contact (AI rate and human rate), with a monthly minimum. Seat-based remains
available as a fallback. See [04-pricing.md](04-pricing.md).

**Why it wins:** the client has one owner for the whole contact. Nobody blames the bot vendor or the
BPO separately, and nobody has to manage the handoff between them.

---

## Upgrade paths & credits

| From → To | Incentive |
|-----------|-----------|
| Tier 0 → Tier 1 | Readout includes a Blueprint proposal valid for 30 days |
| Tier 1 → Tier 2 | 50% of the Blueprint fee is credited to Build if signed within 60 days |
| Tier 2 → Tier 3 | Build fee financed into the outcome rate (optional) for 12-month Tier 3 contracts |
| Current BPO client → Tier 3 | Free Readiness Check + discounted Blueprint, then convert the seat contract to outcome pricing |
