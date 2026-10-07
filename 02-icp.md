# 02 — ICP & Buyer Personas

## 1. Ideal Customer Profile (accounts)

The new ICP is built around **readiness pain**, not industry alone. The best target has enough contact
volume for AI to matter, a CRM or helpdesk in place, and visible pressure to automate.

### Tier A ICP (prioritize): two tracks with equal priority

Tier A has two tracks. Both get the same research depth, the same sequence quality, and Beto's
personal LinkedIn touches. **Track A-US is the growth bet:** US companies buying in English pay higher
rates, have bigger budgets for AI projects, and we can cover any US time zone because our Mexico City site operates 24/7.

| Attribute | Track A-LATAM (Spanish) | Track A-US (English) |
|-----------|-------------------------|----------------------|
| **Industry** | Fintech (BNPL, lending, wallets, neobanks, payments, investing), insurtech, healthtech, memberships and subscriptions, marketplaces, telecom/ISP, **e-commerce** (see qualifier below) | Same, prioritizing US fintech and lending, insurtech, subscriptions/memberships, marketplaces, **e-commerce**, and B2C SaaS. Healthtech only if we can sign a BAA (HIPAA). See the note below |
| **Geography** | Mexico first, then Colombia, Chile, Peru, Argentina | All of the United States. Our site runs 24/7, so we can cover any time zone, including overnight and weekend coverage. Start with the largest fintech and insurtech hubs (New York, California, Texas, Florida, Illinois, Georgia) |
| **Language** | Spanish (es-MX), with English for bilingual programs | **English-first**. Spanish is an add-on for US companies with Hispanic customers |
| **Company size** | 100–2,000 employees (sweet spot 150–800) | 100–1,500 employees (sweet spot 150–600). Big enough for volume, small enough that Beto is a credible counterpart |
| **Contact volume** | ≥ 10,000 customer contacts per month (≈ 10+ support agents) | ≥ 8,000 contacts per month. US contacts have higher AHT and value, so a lower volume still justifies AI |
| **Channels** | WhatsApp and chat heavy (the best automation surface in LATAM), plus voice | Chat, email, and **voice** (voice is still large in US support), plus SMS. WhatsApp is rarely relevant |
| **Systems** | Zendesk, Intercom, Kustomer, Freshdesk, HubSpot Service Hub, Salesforce Service Cloud, Gladly (Gorgias for e-commerce) | Same, with more Salesforce, Gladly, and Kustomer. Native AI (Fin, Zendesk AI, Agentforce) is more likely to be licensed and underused, which is our strongest hook |
| **Stage** | Series B+ or profitable, funded in the last 18 months, or under margin pressure | Same. Add "post-layoff / efficiency mandate", a common US trigger for AI-plus-nearshore conversations |
| **Trigger** | At least one buying signal is required to enter a sequence | Same |

**E-commerce qualifier (both tracks).** E-commerce is Tier A only for larger operators:
≥ 20,000 contacts a month (both tracks), or WhatsApp-heavy support in LATAM. That means multi-brand
retailers, D2C brands at scale, online grocery and delivery, and e-commerce marketplaces. Small and
highly seasonal brands stay out. That's where the old fashion/cosmetics list failed. The angle is the
easiest automation story there is: order status ("where is my order?"), returns and exchanges,
delivery issues, and refunds within policy. These are mostly binary, high-volume, low-risk contacts
(mode A/B in the [Automation Suitability Matrix](frameworks/automation-suitability-matrix.md)), plus
24/7 human coverage for peak season (Buen Fin, Hot Sale, Black Friday, Cyber Monday, holidays).
We don't have a retail case study yet, so the first e-commerce Readiness Check should become one.

**Why US buyers will listen:** we pitch "AI readiness plus a nearshore human layer covering your hours, 24/7,"
not "cheap offshore seats." Tiers 0–2 (Readiness Check, Blueprint, Build) are delivered remotely and
don't depend on agent language at all, so they're the natural entry point for US accounts. Tier 3 adds
English-speaking agents from Mexico City at nearshore rates, at a premium over Spanish (see
[04-pricing.md](04-pricing.md)).

**US proof we already have:** a US fraud-detection fintech client (back-office and investigations).
Turn it into an anonymized case study first, because it's the most relevant reference for Track A-US.

> **Before scaling Track A-US, confirm two things:**
> 1. **English agent capacity:** how many C1+ English agents we have today and how fast we can hire
>    them. Outbound should only promise English human-layer capacity we can staff within 30 days.
> 2. **Compliance by industry:** PCI DSS already covers fintech. US healthtech needs HIPAA readiness
>    and a BAA. SOC 2 (on the 2026 roadmap) matters more to US buyers than to LATAM buyers, so push it
>    forward if Track A-US starts converting.

### Tier B ICP (opportunistic)

- Smaller e-commerce and physical retail below the Tier A e-commerce qualifier (< 20k contacts a
  month). **Drop the current US fashion/cosmetics list:** most of those brands are too small and too
  seasonal for this offer. Re-screen it against the Tier A e-commerce qualifier and keep only the
  accounts that pass.
- Traditional companies (banks, insurers, utilities) that are "digitally transforming". Long cycles,
  so pursue them only through referral.

### Explicit exclusions (stop wasting sends)

- Media and publishers (TechCrunch, WIRED, ADWEEK), AI-native labs (Perplexity, GenAI Works), staffing
  agencies, and companies with fewer than 50 employees.
- Anyone without a customer-facing support operation.
- Contacts scored below 6/10 fit.

## 2. Buying signals (ranked)

| # | Signal | How to detect | Weight |
|---|--------|---------------|--------|
| 1 | **Hiring CX roles**: job posts for "Customer Support Agent", "Agente de Atención", "Head of CX", "CX Automation", "Conversational AI" | Apollo job postings filter / LinkedIn jobs | ★★★ |
| 2 | **Licensed native AI they likely aren't using**: Zendesk/Intercom/Kustomer/Salesforce/HubSpot in stack, but no bot (or a weak one) on site or WhatsApp | Apollo technographics + research agent checks the website and WhatsApp | ★★★ |
| 3 | **Stale help center**: public KB with articles not updated in more than 12 months, or no public KB | Research agent crawls help.domain.com | ★★★ |
| 4 | **Recent funding or new CX leader** (in seat under 6 months) | Apollo funding / job-change alerts | ★★ |
| 5 | **Public complaints about support**: app store reviews, Reclame Aqui, social | Research agent | ★★ |
| 6 | **Exec mentions of AI** in posts or interviews ("we're rolling out AI in support") | LinkedIn / news | ★★ |
| 7 | **Already outsources to a BPO** | LinkedIn employees at known BPOs listing the client; job posts | ★ |

## 3. Personas (who we talk to)

### P1. Economic buyer: VP/Head of Customer Experience, VP Operations, COO
- **Wants:** Lower cost per contact, better CSAT, and an answer to the board's "what's our AI plan?"
- **Fears:** A failed AI project in public, a bot that hallucinates on money or health, being replaced by
  a vendor's decision.
- **Hook:** "Are you AI-ready? Most CX teams that buy native AI never get past 20% containment because
  their KB isn't ready. We'll tell you where you stand, free."
- **Titles to search:** VP Customer Experience, Head of CX, Director de Experiencia al Cliente,
  Director de Operaciones, COO, VP Operations, Head of Customer Support, Gerente de Atención a Clientes.

### P2. Champion: CX Ops / Support Ops / Knowledge Manager / CX Automation lead
- **Wants:** Help actually doing the work: mapping processes, cleaning the KB, configuring the bot.
- **Fears:** Owning an AI rollout alone, with no time.
- **Hook:** "We'll map your processes in two formats, one for the AI and one for your agents, so the bot
  stops making things up and new hires ramp faster."
- **Titles:** CX Operations Manager, Support Operations Lead, Knowledge Manager, Quality Lead, CX
  Automation Specialist, Gerente de Procesos.

### P3. Technical influencer: Head of Product/Engineering, CTO (in smaller companies)
- **Wants:** No vendor lock-in, clean integrations, security.
- **Fears:** A black box that touches customer PII.
- **Hook:** "Your CRM's AI, our build, or your own. We pick the tech per use case, and we're PCI DSS."
- **Titles:** CTO, VP Engineering, Head of Product, Product Manager AI/Ops.

### P4. Finance (later stage): CFO
- **Wants:** Predictable cost per outcome instead of seat creep.
- **Hook:** "Per-resolution pricing with a monthly minimum and a cost-per-contact target."

**Sequencing rule:** Lead with **P1 + P2 in parallel** at the same account (two threads with different
angles). Bring P3 and P4 in from Tier 1 onward.

## 4. Account fit score (0–100), used by the AI research agent

| Dimension | Points | Scoring |
|-----------|--------|---------|
| Industry match | 20 | Tier A industry 20 · adjacent 10 · other 0 |
| Geography & language | 10 | US English-first 10 · MX 10 · US with Spanish-speaking customers 9 · rest of LATAM 8 · Canada/UK 4 · other 0 |
| Size | 10 | 150–800 employees 10 · 100–150 or 800–2,000: 6 · other 2 |
| Estimated contact volume | 15 | ≥ 50k/mo 15 · 10–50k 10 (US: 8–50k) · 5–10k 5 · < 5k 0 |
| CRM/helpdesk in stack | 10 | Known helpdesk 10 · unknown 3 |
| Native AI licensed but underused | 10 | Yes 10 · unclear 5 · no 0 |
| KB health (outside-in) | 10 | Stale or none 10 · partial 5 · excellent 2 (less pain) |
| Active buying signal | 15 | Hiring CX / new leader / funding: 5 each, max 15 |

**Routing:** ≥ 70 goes to *Priority*, which gets a fully personalized sequence plus a LinkedIn touch from
Beto. 50–69 goes to *Standard*, an AI-personalized sequence. Below 50 is not sequenced (nurture via
content only).

## 5. Apollo search recipes

**Account search (Track A-LATAM):**
- Locations: Mexico, Colombia, Chile, Peru, Argentina
- Employees: 100–2,000
- Industries/keywords: financial services, fintech, BNPL, lending, payments, insurance, hospital &
  health care, health tech, telecommunications, internet, consumer services, marketplace, e-commerce,
  online retail, retail (filter by the e-commerce qualifier)
- Technologies (any): Zendesk, Intercom, Kustomer, Freshdesk, HubSpot Service Hub, Salesforce Service
  Cloud, Gladly, Gorgias, Zoho Desk, Twilio, WhatsApp Business API (treat as a signal). E-commerce
  platforms as a signal: VTEX, Shopify Plus, Salesforce Commerce Cloud, Adobe Commerce/Magento
- Job postings: contains "atención a clientes" OR "customer support" OR "customer experience" OR "CX"
- Exclude industries: media, publishing, staffing & recruiting, research

**Account search (Track A-US):**
- Locations: United States, all states. Start with NY, CA, TX, FL, IL, GA, which have the most fintech and insurtech companies
- Employees: 100–1,500
- Industries/keywords: financial services, fintech, lending, payments, insurance, insurtech,
  consumer services, subscription, membership, marketplace, internet, computer software (B2C SaaS),
  telecommunications, e-commerce, online retail (filter by the e-commerce qualifier). Add hospital & health care only once HIPAA/BAA is confirmed
- Technologies (any): Zendesk, Intercom, Kustomer, Gladly, Salesforce Service Cloud, Freshdesk,
  HubSpot Service Hub, Gorgias, Five9, Talkdesk, Genesys, Aircall (voice-heavy signal), Twilio,
  plus Shopify Plus, Salesforce Commerce Cloud, Adobe Commerce/Magento for e-commerce
- Job postings: contains "customer support" OR "customer service representative" OR "customer
  experience" OR "support specialist" OR "CX operations"
- Extra US signals: job posts for support roles in high-cost cities, recent layoffs or an "efficiency"
  announcement, an existing offshore BPO (a switching opportunity)
- Exclude: the same exclusions as LATAM, plus companies that require US-only/onshore support by
  regulation (some government, defense, and certain banking programs)

**People search (per account):**
- Titles (P1): `VP Customer Experience`, `Head of Customer Experience`, `Director de Experiencia`,
  `Director de Operaciones`, `COO`, `Head of Customer Support`, `Gerente de Atención a Clientes`
- Titles (P1, US additions): `VP Customer Support`, `VP Customer Success` (in B2C), `Director of
  Customer Operations`, `Senior Director, Customer Care`, `Head of Member Experience`
- Titles (P2): `CX Operations`, `Support Operations`, `Knowledge Manager`, `Quality Manager`,
  `Gerente de Calidad`, `CX Automation`, `Conversational AI`
- Seniority: Director, VP, Head, Manager (P2)
- Email status: Verified only

**Account list sizing target:** 300 Tier A accounts (150 A-US + 150 A-LATAM) × 2–3 contacts = about
750 contacts, worked in monthly cohorts of 75–100 accounts split 50/50 between the tracks. Shift the
split toward whichever track converts better after the first two cohorts.

## 6. Existing clients count as ICP zero

Before any cold outreach, every current client (Aplazo, Clivi, Cashmind, Casap, iForex, Stori,
TotalPass) is offered a free AI Readiness Check. They have the data, the trust, and the budget, and
they're the most likely to buy AI from someone else if we don't offer it. Aplazo already runs an AI
agent ahead of our humans (see the 2026 QA rubric, which scores whether a prior AI agent already
greeted the customer). That's a Tier 3 hybrid operation we're already running without packaging or
pricing it as one.
