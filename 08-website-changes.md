# 08 — Website Changes (evolvecx.io)

The current site (repo `evolve-cx-homepage`, copy in `lib/content.ts`) is a strong **founder-led
BPO** site, built around the hero line *"I spent a decade buying CX. Now I run the company I wished I
could have hired."* Keep the founder voice and change what it promises.

## 1. Section-by-section

| Section (component) | Today | Change to |
|---------------------|-------|-----------|
| **Hero** (`hero.tsx`) | "I spent a decade buying CX…" | **H1:** "Are you AI ready?" **Sub:** "I spent a decade buying CX at Stripe, Uber, and Kavak. Now I help CX teams find out what AI should handle, build it, and run the humans for everything it shouldn't." **CTA 1:** "Get your free AI Readiness Check" **CTA 2:** "Take the 3-minute score" |
| **Proof bar** | 156 agents · 4.2 CSAT · 98% SLA · PCI DSS | ~198k contacts/month · 24/7 operation, any time zone · 4 channels incl. WhatsApp & voice · PCI DSS · 98% SLA · bilingual. *(Drop "agents" as the lead metric)* |
| **Hook** ("questions I used to ask vendors") | Tenure, QA, SLA questions | **"The questions that decide if AI will work":** (1) What % of your processes are documented? (2) When a process changes, does your KB change within 48 hours? (3) Is the AI you already pay for in your CRM actually turned on? |
| **Different** | Built by a buyer · Fintech-native · Founder-led | **Readiness before robots** · **Honest automation** (we tell you what *not* to automate) · **AI + humans, one owner, paid per outcome** |
| **Services** | Support · Collections · Outbound Sales · Back office | **The AI-Ready ladder**: 0 Readiness Check (free) → 1 Automation Blueprint → 2 Build & Launch (+ Care) → 3 Hybrid Operations. Then a strip: "Human layer services: support, collections, back office, KYC" |
| **Case study** | Aplazo 4→124 agents | Keep it. If Aplazo agrees, reframe it as the human layer behind their AI ("Aplazo: the human layer behind an AI-first support operation"). Their 2026 QA rubric suggests an AI agent already greets customers before our agents do. Add a second card as soon as a Readiness Check result exists |
| **New section: How pricing works** | — | "Pay per resolved contact, whether AI or a human resolved it." Three cards: Projects (fixed fee) · Care (monthly) · Operations (per outcome). No exact rates, just "from" ranges if desired |
| **Industries** | Fintech & BNPL · Lending & Collections · Marketplaces · Healthtech · Technology & SaaS | Keep all five and add **Insurtech**, **Subscriptions & Memberships** (TotalPass), **Telecom**, and **E-commerce**. For e-commerce, lead with order-status questions ("where is my order?"), returns, and delivery issues, which are the most automatable contacts there are |
| **FAQ** | BPO questions | Add: "What is an AI Readiness Check?" · "Do you replace my CRM's AI?" (No, we're tech-agnostic) · "What contacts should never be automated?" · "How does outcome pricing work?" · "Do you serve US companies in English?" (Yes, bilingual teams in Mexico City, 24/7, covering any time zone) · "Is my data safe?" (PCI DSS) |
| **CTA footer** | "Book 30 minutes with Beto. No SDR…" | "Find out if you're AI ready. Free check, 10 business days, a score you can take to your board." *(Remove "No SDR". Our SDR is now an AI we built, and the site should say that proudly)* |
| **llms.txt** | BPO description | Update: "AI enablement and CX operations partner…", the tiers, and outcome pricing |
| **New page `/ai-ready`** | — | Self-serve scorecard (8 questions → band → email gate → HubSpot form). Embeds the Qualifier chat widget |

## 2. Technical

- HubSpot forms (or the HubSpot JS API) for the scorecard. Write answers to the contact properties in
  [05 §4](05-sales-cycle.md#4-hubspot-configuration).
- HubSpot tracking code on all pages (needed for the lead-scoring page-visit signals).
- A chat widget for the Qualifier agent, and a WhatsApp click-to-chat link with an opt-in message.
- Keep the `/es` locale in sync. Spanish is the primary market.

> I can implement these changes in the `evolve-cx-homepage` repo as a follow-up.
