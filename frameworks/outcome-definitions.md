# Framework: Outcome Definitions & Contract Guardrails (Tier 3)

Outcome pricing only works if both sides agree, **before launch**, on what counts as an outcome. This
document is the contract appendix.

## 1. Billable outcome types

| Outcome | Definition (all conditions must be met) |
|---------|------------------------------------------|
| **AI Resolution** | A conversation handled end to end by AI where (a) the customer didn't request or get transferred to a human, (b) there was no re-contact on the same reason within **72h** on any channel, and (c) the CSAT response (if any) is not 1–2/5. |
| **Human Resolution** | A conversation closed by an EvolveCX agent (including AI escalations) with no re-contact on the same reason within 72h, and a correct disposition per QA. |
| **Assisted Resolution** (optional) | A human resolution where AI drafted or resolved the majority of the work (mode C). Billed at the human rate minus a discount, or bundled. |
| **Back-office outcome** | Per completed unit: KYC case reviewed, investigation closed, document validated, backlog case contacted and resolved. Defined per process. |
| **Revenue outcomes** (collections/sales) | Per amount recovered (% of recovery) or per qualified sale/activation. Defined per program. |

**Not billable:** abandoned conversations under 2 customer messages, spam, internal tests, duplicates,
and contacts that hit a client-system outage (logged as *client-caused*).

## 2. Measurement

- **Source of truth:** the client's CRM/helpdesk, with a disposition taxonomy agreed in the Blueprint.
- **Re-contact match:** same customer ID plus the same intent cluster within 72h.
- **Monthly reconciliation:** EvolveCX sends the outcome report by business day 3. The client has 5
  business days to dispute, sampling at least 50 conversations.
- **Audit rights:** the client can review any billed conversation.

## 3. Commercial guardrails

| Guardrail | Standard term |
|-----------|---------------|
| **Monthly minimum** | Covers the fixed cost of Care plus the minimum human staffing. Typically 60–70% of projected billings |
| **Volume bands** | Rates step down at higher volumes (see pricing) |
| **Baseline period** | 30–60 days of measurement before outcome billing starts (billed at seat/hour or a fixed fee) |
| **Quality floor** | If AI-resolved CSAT drops more than 5 points below the human baseline for 2 consecutive weeks, the intent reverts to human handling (at the human rate) until fixed |
| **Re-contact credit** | A resolution that later re-contacts is credited back on the next invoice |
| **Change-of-process clause** | Material client process changes go through Care. Containment targets are re-baselined if the client changes policy |
| **Client-caused failure** | API outages, unannounced policy changes, or missing access exclude those contacts from targets |
| **Term** | 12 months recommended, 90-day minimum (aligned with the current BPO terms) |
| **Price review** | Quarterly: as containment rises, the blended cost per contact falls automatically. Rates are reviewed annually |
| **Shared savings (optional)** | Beyond a target cost per contact, savings are split 70/30 client/EvolveCX |

## 4. Reporting (monthly, per client)

- Contacts by channel and intent; AI vs human vs assisted resolution counts
- Containment rate, re-contact rate, CSAT/QA by resolver type
- Cost per contact (blended) vs baseline
- Top escalation reasons and top hallucination/accuracy findings
- Next quarter's automation roadmap (intents moving from D→C→B→A)
