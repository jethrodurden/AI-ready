# Framework: Dual Process Mapping (Tier 2 / Foundations)

**Principle: one source of truth, two renderings.**
Humans and AI need different things from a process document. Humans need context, the "why", and
examples. AI needs explicit conditions, closed decision rules, and clear limits. Writing two separate
documents makes them drift apart, and drift is what causes hallucinations. So we author **one
structured Process Record** and render it into:

- **AI-friendly map:** what the bot or agent is grounded on
- **Human-friendly SOP:** what agents train on and consult

```
             ┌─────────────────────────┐
             │   PROCESS RECORD (SoT)  │  ← owned, versioned, dated
             │   structured fields     │
             └───────────┬─────────────┘
          render         │          render
     ┌───────────────────┴───────────────────┐
     ▼                                       ▼
 AI-FRIENDLY MAP                       HUMAN-FRIENDLY SOP
 (atomic, rules, limits)               (narrative, why, visuals)
```

## 1. Why AI-friendly mapping reduces hallucinations

LLM agents usually hallucinate for one of these reasons:

| Cause | Fix built into the AI-friendly format |
|-------|---------------------------------------|
| Missing information, so the model fills the gap | Explicit **"If information is not in this record, say X and escalate"** |
| Ambiguous language ("usually", "in some cases", "depends") | Banned words. Every condition is a closed rule in a decision table |
| Contradictory sources (old article vs. new macro) | One record per intent, with a version, effective date, and owner. Superseded versions are removed from retrieval |
| Long multi-topic docs, so the wrong section gets retrieved | **Atomic**: one intent per record, with chunk-friendly headings |
| The model improvises actions | **Allowed actions** listed explicitly, with preconditions. Everything else is forbidden |
| The model promises things | A **"Never say / never promise"** list (amounts, dates, approvals) |
| Edge cases | **Escalation triggers** listed explicitly, plus the handoff message |

## 2. Process Record schema (source of truth)

```yaml
id: PAY-004
intent: change_payment_date
version: 3
effective_date: 2026-09-01
owner: "CX Ops – Payments"            # a named person or role
review_by: 2026-12-01
channels: [whatsapp, chat, voice]
mode: B                                # from the Automation Suitability Matrix

customer_phrases:                      # how customers actually ask (from real tickets)
  - "puedo cambiar mi fecha de pago"
  - "quiero pagar otro día"
  - "can I move my payment date"

purpose: >                             # rendered for humans only
  Customers whose income date changed often ask to move their due date. Moving it reduces
  late payments, so we allow it once per loan within the rules below.

preconditions:
  - customer_authenticated: true
  - loan_status: [active]
  - not_in_collections: true

required_data:
  - loan_id
  - current_due_date
  - requested_new_date

decision_table:
  - if: "requested_new_date is within 1–10 days after current_due_date AND date_changes_used == 0"
    then: "approve via tool change_due_date; confirm new date"
  - if: "date_changes_used >= 1"
    then: "decline politely; explain one change per loan; offer human if customer insists"
  - if: "requested_new_date is before current_due_date OR > 10 days later"
    then: "explain allowed window; offer valid dates"
  - if: "loan_status != active OR in collections"
    then: "escalate to human: collections queue"

allowed_actions:
  - tool: get_loan(loan_id)
  - tool: change_due_date(loan_id, new_date)   # only when decision_table says approve

never:
  - "Promise fee waivers or interest changes"
  - "Change the date without explicit customer confirmation of the new date"
  - "Discuss other customers' accounts"

escalate_when:
  - "Customer mentions hardship, job loss, illness → human (hardship queue)"
  - "Customer disputes a charge → human (disputes)"
  - "Tool error twice → human with summary"
  - "Customer asks for a human"

canonical_answers:
  approved_es: "Listo, {nombre}. Tu nueva fecha de pago es el {fecha}. Te llegará la confirmación por correo."
  declined_es: "Solo es posible cambiar la fecha una vez por crédito, y ya se utilizó. Si lo necesitas, te comunico con un asesor."

unknown_info_response_es: "No tengo esa información confirmada. Te comunico con un asesor para revisarlo."

human_notes:                           # rendered for humans only
  tips:
    - "Customers often ask this right after payday changes. Ask if they also want reminders."
  screenshots: [link-to-backoffice-screen]
  common_mistakes:
    - "Changing the date before authenticating"

change_log:
  - {version: 3, date: 2026-09-01, change: "Window changed from 7 to 10 days", by: "Product"}
```

## 3. AI-friendly rendering rules

1. **One intent per document.** The title is the intent plus the most common customer phrasing.
2. **Order:** preconditions → required data → decision table → allowed actions → never → escalation →
   canonical answers.
3. **Closed language only.** Ban: *usually, normally, sometimes, it depends, etc., as appropriate*.
4. **Numbers, dates, and amounts** are written exactly, never "a few days".
5. **Every record ends with** the unknown-info response and the escalation triggers.
6. **No history or narrative** (no "purpose", no tips). That stays in the human version.
7. **Only the current version** is retrievable. Old versions are archived out of the index.
8. **Test before publish:** every change runs the intent's regression test set (see Care).

## 4. Human-friendly rendering rules

1. **Starts with "why"**: the purpose and the customer context.
2. **Numbered steps with screenshots** of the actual tools.
3. **The decision table becomes a flowchart** (swimlane if multiple teams are involved).
4. **Examples:** one good conversation and one bad one.
5. **Tone guidance** and empathy cues for emotional intents.
6. **Common mistakes** and the QA criteria that apply.
7. **Max 1 page per intent.** Link out for depth.

## 5. Governance (what keeps both versions accurate)

| Element | Standard |
|---------|----------|
| Owner | A named owner per record (client side) and a KB editor (EvolveCX side) |
| Change request | Any process change goes through a form, then the record is updated, then both renderings are regenerated, then regression tests run, then publish |
| SLA | Standard: 48h. Urgent (regulatory/incident): 24h. Critical: bot intent paused immediately, routed to humans |
| Freshness | Each record has a `review_by` date. Stale records get flagged in the monthly report |
| Drift check | Weekly sample of agent and bot conversations vs. the record. Mismatches open change requests |

## 6. Productization

- **Template pack:** Process Record YAML/Sheet, AI rendering template, human SOP template (Docs/Notion)
- **Authoring assist:** an internal LLM tool turns a recorded process walkthrough (agent shadowing
  call) plus existing docs into a draft Process Record. An analyst validates it with the client owner.
- **Unit of sale:** price per Process Record (both renderings plus test set), in complexity tiers.
  See [04-pricing.md](../04-pricing.md).
