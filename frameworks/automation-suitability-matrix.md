# Framework: Automation Suitability Matrix (Tier 1)

**Question it answers:** for each contact reason, should AI resolve it, assist with it, or stay away,
and with which technology?

Score every contact reason (intent) found during intent discovery. The output is a **mode** (A/B/C/D),
a **priority** (what to automate first), and a **tech path**.

## 1. The eight variables

Each variable is scored 1–5. For the "risk" variables, **higher means riskier** (worse for automation).

| # | Variable | Question | 1 | 5 | Type |
|---|----------|----------|---|---|------|
| V1 | **Volume** | Share of total contacts | < 0.5% | > 8% | Value |
| V2 | **Decision determinism** | Is the answer binary/rule-based, or does it need judgment? | Pure judgment / negotiation | Black-and-white rule or lookup | Feasibility |
| V3 | **Data & action access** | Can the bot get the facts and perform the action via API? | Needs human access to internal tools | Full read/write API | Feasibility |
| V4 | **Process stability** | How often does the policy behind this reason change? | Weekly | Stable for 6+ months | Feasibility |
| V5 | **Customer effort / emotion** | How stressed or emotionally loaded is the customer? | Routine, neutral | Distress, anger, hardship, grief | Risk |
| V6 | **Customer impact (consequence of error)** | If the bot answers wrong or hallucinates, what does the customer lose? | Minor inconvenience | Money, health, legal standing, account access | Risk |
| V7 | **Brand & relationship risk** | Could a bad automated interaction cost the relationship or make headlines? | None | Churn of a high-value customer / public incident | Risk |
| V8 | **Regulatory exposure** | Is this governed by a regulator, or does it need a licensed or accountable human? | None | Regulated decision (credit, KYC, disputes, collections conduct, medical) | Risk |

## 2. Scores

```
Feasibility  F = (V2 + V3 + V4) / 3            → 1..5 (higher = easier to automate)
Risk         R = max(V6, V8) × 0.6 + avg(V5, V7) × 0.4  → 1..5 (higher = more dangerous)
Value        V = V1                             → 1..5
```

> `R` uses **max** of impact and regulation because one severe consequence outweighs several mild ones.
> Hallucination tolerance is captured by V6: a hallucination is only as costly as the consequence
> of a wrong answer.

## 3. Mode assignment

```
                         RISK (R)
                 low (≤2.5)         high (>2.5)
             ┌──────────────────┬──────────────────┐
 FEASIBILITY │  A · AI RESOLVES │  B · AI WITH     │
  high (≥3.5)│  end to end      │  GUARDRAILS      │
             ├──────────────────┼──────────────────┤
  low (<3.5) │  C · AI ASSISTS  │  D · HUMAN-LED   │
             │  (copilot), fix  │  (AI summarizes  │
             │  feasibility gap │   & routes only) │
             └──────────────────┴──────────────────┘
```

| Mode | What AI does | What humans do | Typical examples (fintech/BNPL) |
|------|--------------|----------------|-----------------------------|
| **A · AI resolves** | Answers and acts end to end; escalates on explicit triggers | Audit samples weekly | Payment due date, balance, how to download a statement, store/merchant list, password reset link, order/loan status, "where's my card" with tracking |
| **B · AI with guardrails** | Resolves, but with confirmation steps, cited sources, limits on actions, and mandatory human approval above thresholds | Approve exceptions; review flagged conversations | Refund within policy, payment-date change within rules, address update after authentication, plan/membership change, simple fee reversal under $X |
| **C · AI assists** | Drafts replies, summarizes history, retrieves the right SOP, fills forms | Decide and send | Complex technical troubleshooting, multi-system investigations, B2B merchant issues |
| **D · Human-led** | Triages, authenticates, summarizes, routes to the right specialist with context | Own the conversation | Disputes and chargebacks, fraud claims, collections hardship and negotiation, KYC rejections, complaints escalated to regulators (CONDUSEF), medical questions, VIP churn saves |

**Hard overrides (regardless of score):**
- V8 = 5 (regulated decision): never mode A. At most B, with a human approving the decision.
- V5 = 5 (distress) **and** V6 ≥ 4: mode D.
- The customer explicitly asks for a human: route to a human (keep it 1–2 turns, no loops).
- V4 = 1 (weekly change) with no KB governance: mode C until Foundations governance is in place.

## 4. Priority (what to automate first)

```
Priority = V × F × (6 − R)        (range 1..125)
```

Sort descending. Wave 1 is the top mode-A intents until about 30–40% of volume is covered. Wave 2 adds
mode B. Mode C becomes copilot rollout for the human layer. Mode D stays with humans, and AI handles
triage and summary only.

## 5. Worked example (illustrative BNPL client)

| Intent | V1 | V2 | V3 | V4 | V5 | V6 | V7 | V8 | F | R | Mode | Priority |
|--------|----|----|----|----|----|----|----|----|---|---|------|----------|
| "When is my next payment?" | 5 | 5 | 5 | 5 | 1 | 2 | 1 | 1 | 5.0 | 1.6 | **A** | 110 |
| "Purchase declined at checkout" | 5 | 4 | 4 | 4 | 3 | 3 | 3 | 1 | 4.0 | 3.0 | **B** | 60 |
| "Verification code not arriving / lost phone" | 4 | 3 | 3 | 4 | 3 | 4 | 3 | 3 | 3.3 | 3.6 | **D** → move to B after an auth API | 32 |
| "I want to dispute a charge" | 3 | 2 | 2 | 4 | 4 | 5 | 4 | 5 | 2.7 | 4.6 | **D** | 11 |
| "Can I extend my payment? (hardship)" | 3 | 2 | 3 | 3 | 5 | 5 | 4 | 5 | 2.7 | 4.8 | **D** (override) | 10 |
| "How do I download my contract?" | 3 | 5 | 4 | 5 | 1 | 1 | 1 | 1 | 4.7 | 1.0 | **A** | 70 |

*(The "lost phone / verification code" row comes from real Dec-2024 ticket patterns. It's a high-volume
reason where the blocker is feasibility, specifically authentication access, rather than risk. That
makes it a good Wave 2 candidate once identity-verification APIs are available.)*

## 6. Technology selection (per intent group)

Ask in order. The first "yes" wins, unless a later question disqualifies it.

```
1. Does the client already license native AI in their CRM (Zendesk AI agents, Intercom Fin,
   Agentforce, HubSpot Breeze, Kustomer AI…) AND does it support the channel (WhatsApp/voice),
   the language quality (es-MX), and the actions needed?
      └─ YES → NATIVE CRM AI. We configure, write the AI-friendly KB, tune, and run Care.
               (Fastest, lowest risk, the client keeps the platform.)
2. Does the client have an in-house AI/engineering team with a roadmap for this?
      └─ YES → CLIENT BUILD. We supply AI-friendly process maps, test sets, eval, and the human layer.
3. Otherwise, or if native AI fails on channel/language/actions/cost:
      └─ EVOLVECX BUILD. LLM agent on WhatsApp Business API / web chat / voice, grounded on the
         AI-friendly KB, with tools for client APIs, plus handoff to our human layer.
```

**Disqualifiers to check for every option:**

| Criterion | Why it matters |
|-----------|----------------|
| Channel support (WhatsApp, voice) | Many native CRM bots are weak on WhatsApp and voice in LATAM |
| Spanish quality (es-MX tone, slang, code-switching) | Customers abandon robotic Spanish |
| Action/tool support | Answering questions only caps containment at about 20–30% |
| Pricing model | Some native AI charges per resolution. Compare against our outcome rate (verify current vendor pricing) |
| Data residency / PII / PCI scope | Payment data, health data |
| Handoff quality | Context must pass to the human without the customer repeating themselves |
| Lock-in and observability | Can we export transcripts, run evals, and audit decisions? |

**Positioning note:** we're **technology-agnostic**. Recommending the client's native AI when it's the
right fit builds trust, and it still generates Build, Care, and Hybrid Ops revenue for us.

## 7. Deliverable format

A spreadsheet with one row per intent and these columns:
`intent, example_utterances, volume_share, AHT, CSAT, recontact_rate, V1..V8, F, R, priority, mode,
tech_path, blockers, wave, owner`. A template is in the Blueprint kit. The research agent can pre-fill
V1 from the ticket export.
