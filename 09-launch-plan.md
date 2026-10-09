# 09 — 90-Day Launch Plan & KPIs

## Phase 1, Weeks 1–3: First new-client outreach out the door

**Principle:** the current inbox already delivers, so cohort 1 doesn't have to wait for agents,
the website, or a second inbox. Research and write cohort 1 by hand (with Claude's help), send it in
week 2, and build the agents from what works. Existing clients run in parallel.

| When | Step | Deliverable | Owner |
|------|------|-------------|-------|
| Week 1, day 1 | **1. Pause** the current Apollo sequences ("scaling headcount" copy) | Old sequences stopped | Beto / Ops |
| Week 1, day 1 | **2. Approve** the positioning, the free Readiness Check offer, and the email templates ([07 §3](07-outbound-playbook.md#3-sequence-templates)) | Go / changes | Beto |
| Week 1, day 1 | **3. Deliverability check**: confirm SPF/DKIM/DMARC on evolvecx.io, set up Google Postmaster Tools, create the second inbox and start warm-up. No new domains | Checks green, warm-up running | Ops |
| Week 1, days 1–3 | **4. Build cohort 1**: 50 Tier A accounts (25 Track A-US, 25 Track A-LATAM) from the Apollo recipes ([02 §5](02-icp.md#5-apollo-search-recipes)), with 2 contacts each (P1 + P2) | 50 accounts, ~100 verified contacts | Ops + Claude |
| Week 1, days 2–4 | **5. Research cohort 1**: help center, bot, job posts, tech stack, and one hook finding per account (manual version of the [Researcher agent](agents/01-researcher.md)) | 50 research briefs | Claude + review by Beto |
| Week 1, days 4–5 | **6. Write and load** the sequences (E1–E4 + 2 LinkedIn notes per contact); Beto approves every message | Sequences loaded in Apollo | Claude + Beto |
| Week 1, days 3–5 | **7. Minimal HubSpot**: pipeline A stages and the key properties (`icp_fit_score`, `research_brief`, `readiness_band`, `readiness_score_full`) | Replies and deals can be tracked | Ops |
| Week 1 | **8. Delivery kit ready**: questionnaire, analyst checklist, readout deck ([kit/](kit/)) and the analyst who'll run checks | Can deliver a check the day someone says yes | Beto + analyst |
| Week 2 | **9. Cohort 1 goes out** from Beto's inbox (≤ 30 cold emails/day), plus Beto's LinkedIn touches | ~100 contacts in sequence | Apollo + Beto |
| Week 2 | *Parallel:* **existing clients**: Beto sends the personal Readiness Check offers ([kit/01](kit/01-client-emails.md)) | 7 offers sent | Beto |
| Weeks 2–3 | **10. Website hero + `/ai-ready` scorecard live** before email 3 goes out (day 9 of the sequence, because it links to the scorecard) ([08](08-website-changes.md)) | Scorecard capturing leads in HubSpot | Claude + Beto |
| Week 3 | **11. Cohort 2** (50 accounts) researched and loaded, using what we learned from cohort 1 replies | Cohort 2 in sequence | Claude + Beto |
| Week 3 | **12. Start building agents v1** (Researcher, SDR Writer, Reply Triage) by automating the manual steps 5–6 | Agents in test | Builder |
| Week 3 | Content: LinkedIn series "Are you AI ready? / ¿Estás listo para la IA?" (3 posts/week) | First posts live | Beto |

## Phase 2, Weeks 4–8: First checks, first paid work
| Week | Workstream | Deliverable |
|------|-----------|-------------|
| 4 | First Readiness Checks (new prospects from cohorts 1–2, plus any existing clients who said yes) | First readouts. First Blueprint/Foundations proposals |
| 4 | HubSpot (full) | Pipeline B, lead scoring, the first workflows ([05 §4](05-sales-cycle.md#4-hubspot-configuration)) |
| 5 | Outbound | Second inbox live alongside Beto's. Cohort 3: 100 accounts, split 50 Track A-US / 50 Track A-LATAM |
| 5 | Agents v1 live | Researcher + SDR Writer (100% human approval) + Reply Triage |
| 5–6 | Blueprint kit | Suitability Matrix spreadsheet, intent-clustering notebook, Blueprint deck template |
| 6 | Process mapping kit | Process Record template (Sheet/YAML), AI + human renderers, test-set template |
| 5–6 | US case study | Anonymized write-up of the US fraud-detection fintech account (the main proof for Track A-US) |
| 6 | Pricing experiment E1 | Shadow outcome billing on one existing LOB |
| 6 | Website (rest) | Qualifier chat, pricing section, FAQ, llms.txt |
| 7 | Webinar #1 | "What to automate and what to keep human in fintech CX" |
| 8 | Agents v2 | Meeting Prep + CRM Scribe + Proposal Drafter. Auto-send for Standard accounts |

## Phase 3, Weeks 9–13: Scale & prove
| Week | Workstream | Deliverable |
|------|-----------|-------------|
| 9 | First Tier 2 build kicks off (new or existing client) | Wave 1 intents, shadow mode by week 12 |
| 9–10 | Partner applications | Zendesk / Intercom / HubSpot / Kustomer partner programs |
| 10 | Outbound | Cohort 2 (100 accounts). Iterate copy using reply data |
| 11 | Case study #1 | "From score X to Y": readiness improvement or the first containment result |
| 12 | Benchmark draft | "State of AI readiness in LATAM CX" (if 15+ checks are done) |
| 13 | QBR of the strategy | Review KPIs, pricing experiments, ICP adjustments. Plan for Q2 |

## Team & roles

| Role | Who | Time |
|------|-----|------|
| Founder-seller (readouts, proposals, closes, LinkedIn) | Beto | 50% |
| AI Readiness Analyst (runs checks, Blueprints) | Internal: QA/WFM lead or ops analyst, trained on the frameworks | 100% |
| Knowledge/Process Engineer (Process Records, KB) | Internal: training/documentation team (we already build KBs) | 1–2 FTE as projects land |
| AI Builder (agents, bots, integrations) | Contractor or first technical hire | 100% from week 2 |
| Sales Ops (HubSpot/Apollo, deliverability) | Part-time / contractor | 25% |

## Scoreboard (weekly review)

| Category | KPI | Day 30 | Day 60 | Day 90 |
|----------|-----|-------:|-------:|-------:|
| **Activity** | Accounts researched (cumulative) | 100 | 250 | 400 |
| | Contacts sequenced (cumulative) | 0 (warming) | 250 | 600 |
| **Engagement** | Reply rate | — | ≥ 5% | ≥ 6% |
| | Positive replies (cumulative) | — | 5 | 15 |
| | Scorecard completions (cumulative) | 5 | 30 | 75 |
| **Pipeline** | Readiness Checks started (cumulative) | 4 | 10 | 18 |
| | Readouts delivered | 2 | 7 | 14 |
| | Paid proposals sent | 1 | 5 | 10 |
| **Revenue** | Paid deals won (Foundations/Blueprint) | 0 | 2 | 5 |
| | New project bookings (USD) | $0 | $20k | $60k |
| | Builds started | 0 | 0 | 1–2 |
| | Clients on outcome pricing (pilot) | 0 | 1 shadow | 1 live |
| **Quality** | Readout NPS | — | ≥ 50 | ≥ 50 |
| | Agent brief accuracy | ≥ 85% | ≥ 90% | ≥ 90% |

## Decisions Beto needs to make this week

1. **Approve the positioning and tagline** ("Are you AI ready?" / "AI where it works. Humans where it matters.").
2. **Pick the analyst** who'll run the first Readiness Checks.
3. **Pick the AI builder**: an in-house hire or a contractor.
4. **Choose the outcome-pricing pilot client** and LOB for experiment E1.
5. **Confirm English capacity for Track A-US**: how many C1+ English agents we can staff within 30 days, and whether US healthtech (HIPAA/BAA) is in or out for now.
6. **Confirm the proof points** in [agents/proof-points.md](agents/proof-points.md), including permission to name clients.
7. **Replace the cost assumptions** in [04-pricing.md §5](04-pricing.md#5-why-outcome-pricing-doesnt-cannibalize-us) with actuals.
