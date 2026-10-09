# Kit 03 — Running the Readiness Check (10 business days)

**Owner:** the AI Readiness Analyst. **Effort cap:** about 12 hours of analyst time per check.
**Output:** a scored scorecard, a top-5 gap list, and the readout deck ([kit/04](04-readout-template.md)).

## Day-by-day

| Day | Task | Done when |
|-----|------|-----------|
| 0 | Client says yes. Create the HubSpot deal (pipeline B, *Check In Progress*). Send the questionnaire and book the intake | Intake on the calendar |
| 1 | **Pre-fill** what we already know: volume, channels, helpdesk, tagging, KB location (current clients) | Section 0 and B1–B3 drafted |
| 1–2 | **45-min intake call** with the client: confirm pre-filled answers, walk through A3–A5 and B4–B6, ask the Section C questions | Questionnaire 100% answered (including "Not sure") |
| 2–3 | Get the **data**: 1 month of tickets (export) and read-only KB access. For current clients, use what we already operate | Files in the client folder |
| 3–5 | **KB sample audit**: 20 articles (pick from the top-5 contact reasons) | Audit sheet complete |
| 3–5 | **Ticket sample**: 100 tickets, or an LLM-assisted pass over the full month | Contact-reason table complete |
| 6 | **Score** the scorecard, apply the hard flags, set the band | Score + band in HubSpot (`readiness_score_full`, `pillar_a_score`, `pillar_b_score`) |
| 7 | Write the **top-5 gaps** and the "if you launched a bot tomorrow" paragraph | Gap list reviewed by Beto |
| 8 | Build the **readout deck** from the template | Deck ready |
| 9–10 | **45-min readout** with Beto and the client decision-maker | Next step agreed; proposal due within 48h |

## KB sample audit (20 articles)

For each article, record in a sheet:

| Field | What to check |
|-------|---------------|
| Article / contact reason | Which reason it covers |
| Last updated | Date. Flag anything older than 12 months |
| Matches reality? | Compare with 3–5 real tickets on the same reason. Yes / partly / no |
| Contradicts another source? | Another article, a macro, or what agents actually do |
| One topic? | Or several topics in one document |
| Closed rules? | Exact conditions and numbers, or vague words ("usually", "depends") |
| Escalation defined? | Does it say when to hand over to someone else |

**Rolls up to:** A6 (consistency), A7 (structure), and evidence for A1/A4.

## Ticket sample (100 tickets or the full month)

| Field | What to capture |
|-------|-----------------|
| Contact reason | Group into 10–20 reasons |
| Share of volume | % per reason |
| Resolved in first contact? | Yes / no |
| Needed a system action? | Look-up only / change data / neither |
| Judgment or rule? | Black-and-white rule vs. needs judgment |
| Risk if answered wrong | Low / medium / high (money, health, legal, account access) |
| Tagged correctly? | Compare the tag with the actual reason |

**Rolls up to:** B3 (tagging reliability), plus a **preview** of the Tier 1 Automation Suitability
Matrix. Show 3–5 reasons as "AI could handle these" and 2–3 as "these stay human." That preview is
what makes clients ask for the Blueprint.

## Quality bar before the readout

- [ ] Every score has evidence (an answer, an audit row, or a ticket example)
- [ ] "Not sure" answers are either verified or listed as findings
- [ ] The top-5 gaps are specific ("38% of sampled articles are older than 12 months"), not generic
- [ ] Recommended path matches the band ([scorecard bands](../frameworks/ai-readiness-scorecard.md#scoring))
- [ ] Investment range uses the rate card ([04-pricing.md](../04-pricing.md)); current clients get 40% off the Blueprint
- [ ] Beto has reviewed the deck
