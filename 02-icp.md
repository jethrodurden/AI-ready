# 02 — ICP & Buyer Personas

## 1. Ideal Customer Profile (accounts)

The new ICP is built around **readiness pain**, not industry alone. The best target has enough contact
volume for AI to matter, a CRM or helpdesk in place, and visible pressure to automate.

### Tier A ICP (prioritize: closest to our proof)

| Attribute | Criteria |
|-----------|----------|
| **Industry** | Fintech (BNPL, lending, wallets, neobanks, payments, investing), insurtech, healthtech, memberships and subscriptions, marketplaces, telecom/ISP |
| **Geography** | Mexico first, then Colombia, Chile, Peru, Argentina. Second: US companies serving Spanish-speaking customers |
| **Company size** | 100–2,000 employees (sweet spot 150–800) |
| **Contact volume** | ≥ 10,000 customer contacts per month (≈ 10+ support agents, in-house or outsourced) |
| **Channels** | WhatsApp and chat heavy (the best automation surface in LATAM), plus voice |
| **Systems** | Uses a helpdesk/CRM: Zendesk, Intercom, Kustomer, Freshdesk, HubSpot Service Hub, Salesforce Service Cloud, Gladly |
| **Stage** | Series B+ or profitable, funded in the last 18 months, or under margin pressure |
| **Trigger** | See buying signals below. At least one signal is required to enter a sequence |

### Tier B ICP (opportunistic)

- E-commerce and retail with high WISMO ("where is my order") volume, only if they're in LATAM and
  WhatsApp-heavy. **Drop the US fashion/cosmetics list**: we have no proof there and they rarely
  outsource to Mexico.
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
| Geography | 10 | MX 10 · LATAM 8 · US with Hispanic customers 6 · other 0 |
| Size | 10 | 150–800 employees 10 · 100–150 or 800–2,000: 6 · other 2 |
| Estimated contact volume | 15 | ≥ 50k/mo 15 · 10–50k 10 · 5–10k 5 · < 5k 0 |
| CRM/helpdesk in stack | 10 | Known helpdesk 10 · unknown 3 |
| Native AI licensed but underused | 10 | Yes 10 · unclear 5 · no 0 |
| KB health (outside-in) | 10 | Stale or none 10 · partial 5 · excellent 2 (less pain) |
| Active buying signal | 15 | Hiring CX / new leader / funding: 5 each, max 15 |

**Routing:** ≥ 70 goes to *Priority*, which gets a fully personalized sequence plus a LinkedIn touch from
Beto. 50–69 goes to *Standard*, an AI-personalized sequence. Below 50 is not sequenced (nurture via
content only).

## 5. Apollo search recipes

**Account search (Tier A, Mexico/LATAM):**
- Locations: Mexico, Colombia, Chile, Peru, Argentina
- Employees: 100–2,000
- Industries/keywords: financial services, fintech, BNPL, lending, payments, insurance, hospital &
  health care, health tech, telecommunications, internet, consumer services, marketplace
- Technologies (any): Zendesk, Intercom, Kustomer, Freshdesk, HubSpot Service Hub, Salesforce Service
  Cloud, Gladly, Zoho Desk, Twilio, WhatsApp Business API (treat as a signal)
- Job postings: contains "atención a clientes" OR "customer support" OR "customer experience" OR "CX"
- Exclude industries: media, publishing, staffing & recruiting, research

**People search (per account):**
- Titles (P1): `VP Customer Experience`, `Head of Customer Experience`, `Director de Experiencia`,
  `Director de Operaciones`, `COO`, `Head of Customer Support`, `Gerente de Atención a Clientes`
- Titles (P2): `CX Operations`, `Support Operations`, `Knowledge Manager`, `Quality Manager`,
  `Gerente de Calidad`, `CX Automation`, `Conversational AI`
- Seniority: Director, VP, Head, Manager (P2)
- Email status: Verified only

**Account list sizing target:** 300 Tier A accounts × 2–3 contacts = about 750 contacts, worked in
monthly cohorts of 75–100 accounts.

## 6. Existing clients count as ICP zero

Before any cold outreach, every current client (Aplazo, Clivi, Cashmind, Casap, iForex, Stori,
TotalPass) is offered a free AI Readiness Check. They have the data, the trust, and the budget, and
they're the most likely to buy AI from someone else if we don't offer it. Aplazo already runs an AI
agent ahead of our humans (see the 2026 QA rubric, which scores whether a prior AI agent already
greeted the customer). That's a Tier 3 hybrid operation we're already running without packaging or
pricing it as one.
