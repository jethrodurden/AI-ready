# Framework: AI Readiness Scorecard (Tier 0)

Two pillars, 100 points in total. Each question is scored 0–4, then weighted. The AI qualification
agent asks the **bold** questions in conversation (the lite version). Analysts complete the full
version during the free check.

## Pillar A: Documented Processes / Knowledge (50 pts)

| # | Question | 0 | 2 | 4 | Weight |
|---|----------|---|---|---|--------|
| A1 | **Do you have a knowledge base your agents use daily?** | No KB / docs scattered in chats and drives | KB exists, partially used | Single KB, used in every contact, searchable | 8 |
| A2 | **What % of your contact reasons have a documented, step-by-step process?** | < 30% | 30–70% | > 70% | 10 |
| A3 | **How often do your processes or policies change?** (This is a context question. Frequent change increases the value of governance.) | Weekly+ with no process | Monthly | Quarterly or stable with a process | 4 |
| A4 | **When a process changes, how quickly is the KB updated?** | Rarely, or no one owns it | Within weeks | Within 48h with a named owner | 10 |
| A5 | Is there a named KB owner and a change-request flow? | No | Informal | Yes, with an SLA | 6 |
| A6 | Do the KB, macros, and actual agent behavior match? (sample audit) | Frequent contradictions | Some | Consistent | 6 |
| A7 | Are articles structured (one topic each, clear conditions, dated)? | Long narrative docs | Mixed | Atomic, dated, versioned | 6 |

## Pillar B: Systems & Data (50 pts)

| # | Question | 0 | 2 | 4 | Weight |
|---|----------|---|---|---|--------|
| B1 | **Which CRM/helpdesk do you use for customer contacts?** | None / spreadsheets / WhatsApp on phones | Basic helpdesk | Mature helpdesk/CRM (Zendesk, Intercom, Salesforce, HubSpot, Kustomer…) | 8 |
| B2 | **How many customer contacts per month, and how many months of history do you keep?** | < 2k/mo or < 3 months | 2–10k/mo, 3–6 months | > 10k/mo, 6+ months | 8 |
| B3 | Are contacts tagged by reason/disposition? How reliable is the tagging? | No tagging | Tagged, inconsistent | Consistent taxonomy, > 80% tagged | 8 |
| B4 | **Does your CRM include native AI (bots, agent assist)? Is it turned on?** | No AI | Licensed but off / pilot | Live, and measured | 6 |
| B5 | **If AI is live: what % of contacts does it fully resolve today?** | < 10% / unknown | 10–30% | > 30% with CSAT tracked | 6 |
| B6 | Can a bot *act* (check order/payment/account status, update data) via API? | No APIs | Read-only APIs | Read + write APIs with auth | 8 |
| B7 | Are conversation transcripts (chat, WhatsApp, voice) stored and exportable? | No | Partially (e.g., no voice transcripts) | All channels, exportable | 6 |

> **Note on "enough contacts to train an AI agent":** Modern AI agents aren't trained on CRM records.
> They're *grounded* in the KB and connected to systems through tools. Historical conversations matter
> for three things: (1) **discovering intents** and their volumes, (2) building **test sets** to measure
> accuracy before launch, and (3) setting the **baseline** we measure outcomes against. That's why B2,
> B3, and B7 weigh as much as the CRM itself. Rule of thumb: 3+ months of history and ≥ 5,000 tagged
> conversations make a reliable Blueprint.

## Scoring

`Score = Σ (answer / 4 × weight)`, giving 0–100.

| Band | Score | Meaning | Recommended path |
|------|-------|---------|------------------|
| 🟢 **AI-Ready** | 75–100 | Knowledge and systems can support automation now | Tier 1 Blueprint → Tier 2 |
| 🟡 **Ready with prep** | 55–74 | Can start, but gaps will cap containment and raise hallucination risk | Foundations (targeted) + Tier 1 in parallel |
| 🟠 **Foundations first** | 35–54 | Bots built today will hallucinate or under-deliver | Foundations, then re-score |
| 🔴 **Not ready** | 0–34 | Missing a CRM/KB baseline | Foundations + systems setup (or BPO first, then AI) |

**Hard flags.** Any of these caps the band at 🟠 regardless of score: no KB at all (A1 = 0), process
change with no KB update (A4 = 0), or no transcript history (B7 = 0).

## Readout template (one page)

1. Overall score and band
2. Pillar A and Pillar B scores, each with a one-line diagnosis
3. Top 5 gaps, ranked by impact on AI containment
4. "If you launched a bot tomorrow, here's what would happen" (the risk narrative)
5. Recommended next step and investment range

## Self-serve lite version (website lead magnet)

Uses the bold questions only (A1, A2, A3, A4, B1, B2, B4, B5). It returns an instant band and a short
explanation, and asks for an email to receive the full PDF. Answers are written to HubSpot contact
properties (see [05-sales-cycle.md](../05-sales-cycle.md#4-hubspot-configuration)).
