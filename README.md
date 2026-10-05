# EvolveCX — "Are you AI ready?" Go-to-Market Strategy

> **The premise:** *Are you AI ready? If you're not — or you don't know — talk to me.*
>
> EvolveCX stops selling seats and starts selling **AI readiness, AI implementation, and outcomes**,
> with the BPO as the human layer behind the bots, not the main thing we sell.

This repository is the working playbook for that shift. It covers how we position ourselves, who we
sell to, what we sell (four tiers), how we price it, how the full sales cycle runs, and the AI agents
that run the top of our own funnel. **We use the same AI we sell.**

## How to read this

| # | Document | What it answers |
|---|----------|-----------------|
| 01 | [Diagnosis & Positioning](01-positioning.md) | Why the current outbound got zero replies, and the new narrative |
| 02 | [ICP & Buyer Personas](02-icp.md) | Who we target, how we score them, exact Apollo filters |
| 03 | [Offer Architecture (the 4 tiers)](03-offer-tiers.md) | What each tier delivers, entry/exit gates, upgrade paths |
| 04 | [Pricing](04-pricing.md) | Project, retainer, and per-outcome pricing, with worked unit economics |
| 05 | [Full Sales Cycle](05-sales-cycle.md) | Stages, owners (AI vs human), HubSpot pipeline + properties, SLAs |
| 06 | [AI SDR / BDR / Qualification Agent](06-ai-sales-agent.md) | Architecture on Apollo + HubSpot, agent roles, guardrails |
| 07 | [Outbound & Inbound Playbook](07-outbound-playbook.md) | Sequences (EN/ES), LinkedIn, WhatsApp, content, lead magnet |
| 08 | [Website Changes](08-website-changes.md) | What to change on evolvecx.io to match the new story |
| 09 | [90-Day Launch Plan & KPIs](09-launch-plan.md) | Week-by-week rollout and the scoreboard |

### Frameworks (the IP we sell)

| Framework | Used in |
|-----------|---------|
| [AI Readiness Scorecard](frameworks/ai-readiness-scorecard.md) | Tier 0, the free assessment, and the AI qualification agent |
| [Automation Suitability Matrix](frameworks/automation-suitability-matrix.md) | Tier 1, which contacts AI should handle, which need a human, and which tech |
| [Dual Process Mapping (AI-friendly + Human-friendly)](frameworks/dual-process-mapping.md) | Tier 2, process mapping that reduces hallucinations and trains humans |
| [Outcome Definitions & Contract Guardrails](frameworks/outcome-definitions.md) | Tier 3, what counts as a billable "resolution" |

### Agent specs (for building our own sales agents)

| Agent | Spec |
|-------|------|
| Prompts & schemas for every agent in the funnel | [agents/](agents/) |

## The strategy on one page

1. **Reposition.** We stop saying "a nearshore BPO that scales your team" and start saying "we get your CX
   operation AI-ready, build the AI, and supply the humans for what AI shouldn't do."
   Beto's buyer story ("I spent a decade buying CX") stays. What changes is the promise attached to it.
2. **Free entry point.** The **AI Readiness Check** is a 10-business-day assessment of two things:
   *documented processes* (KB and process coverage, freshness, change discipline) and *systems* (CRM,
   data volume, native AI and whether it's actually used). The output is a score plus a readout.
   It's free, it's gated, and its job is to qualify.
3. **Paid ladder.** Readiness Check (free) → **Automation Blueprint** (project) → **Build & Launch**
   (project + KB/Bot Care retainer) → **Hybrid Operations** (AI + human, priced per outcome).
   Clients who aren't ready don't fall out of the ladder. They buy **Foundations**: KB and process
   rebuild, the documentation work we already do for BPO clients.
4. **Pricing moves from seats to outcomes.** Assessments and builds are fixed-fee projects. Maintenance
   is a retainer. Operations are billed **per resolved contact, whether AI or human resolved it**, with
   a monthly minimum. We earn the same or more margin while the client pays less. See
   [04-pricing.md](04-pricing.md#5-why-outcome-pricing-doesnt-cannibalize-us).
5. **Our funnel runs on agents.** An AI research/SDR agent builds an *outside-in* readiness pre-score
   for each target account (from its help center, chatbot, job posts, and tech stack) and writes the
   first touch around what it found. An AI qualification agent runs the Readiness Check intake on
   web and WhatsApp. Humans (Beto) take every call from the readout onward. HubSpot is the system of
   record and Apollo is the data and sending layer.
6. **Start with current clients.** Aplazo, Clivi, Cashmind, Casap, iForex, Stori, and TotalPass each get
   a free Readiness Check in the first 30 days. That's the fastest path to case studies and revenue,
   and it keeps those accounts from buying AI from someone else.
