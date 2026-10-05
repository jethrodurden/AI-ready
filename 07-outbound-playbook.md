# 07 — Outbound & Inbound Playbook

## 1. Deliverability: fix before sending anything

Zero replies (not even out-of-office replies or unsubscribes) suggests the emails may not be reaching
inboxes. Run these checks first:

- [ ] **Test placement now:** send the old email to 10 seed inboxes (Gmail, Outlook, Google Workspace,
      M365) using a tool like GlockApps or Mail-Tester. If more than 30% land in spam, fixing that is step one.
- [ ] **Don't cold-send from `evolvecx.io`.** Buy 2–3 secondary domains (e.g., `evolvecx-ai.com`,
      `getevolvecx.com`, `evolvecxhq.com`) that redirect to evolvecx.io. Use 2 inboxes per domain
      (e.g., `beto@`, `alberto@`).
- [ ] SPF, DKIM, and DMARC (`p=none` to start) on every sending domain. Custom tracking domain in Apollo.
- [ ] **Warm up** each inbox for 3–4 weeks (Apollo warm-up or a dedicated tool) before sequencing.
- [ ] **Limits:** ≤ 40 cold emails/day per inbox. Plain text. **No links or images in the first touch.**
      Turn off open tracking for first touches (it adds a tracking pixel).
- [ ] Verify every email (Apollo "verified" only, plus a secondary verification on catch-all domains).
- [ ] **Send times:** Tue–Thu, 8:00–10:30 local time for the recipient. The Aug 13 batch went out at
      about 18:20 CDMX (00:20 UTC), after the workday.

## 2. Channel mix per Priority account (fit ≥ 70)

| Day | Channel | Who | Content |
|-----|---------|-----|---------|
| 0 | LinkedIn | Beto (personal) | View profile, follow company, engage with 1 post |
| 1 | Email E1 | SDR agent → Beto approves | Hook finding + free offer, yes/no ask |
| 2 | LinkedIn | Beto | Connection request (no pitch) |
| 4 | Email E2 | SDR agent | The reframe: knowledge, not models |
| 7 | Call | Beto / sales hire | 30-second voicemail referencing the finding (only if a direct number is available) |
| 9 | Email E3 | SDR agent | Not everything should be automated, plus the scorecard link |
| 10 | LinkedIn | Beto | Short note with a finding or post (if connected) |
| 16 | Email E4 | SDR agent | Break-up / "want the findings anyway?" |

Standard accounts (fit 50–69) get emails E1–E4 only. The P2 champion at the same account gets a
parallel sequence that starts 3 days later, with the champion angle.

## 3. Sequence templates

> These are the **reference versions** the SDR agent adapts per account. `{hook_finding}` must be a
> verified, specific observation from the research brief.

### Spanish (P1, economic buyer)

**E1, subject: `tu centro de ayuda y la IA`**
> Hola {nombre},
>
> Revisé el centro de ayuda de {empresa} antes de escribirte: {hook_finding}.
>
> Lo menciono porque es la razón #1 por la que los bots de IA alucinan o se quedan en 15–20% de
> resolución: no es el modelo, es el conocimiento con el que lo alimentas.
>
> Preparé un diagnóstico rápido "desde afuera" de qué tan lista está la operación de {empresa} para
> IA. ¿Te lo comparto?
>
> Beto
> CEO, EvolveCX
>
> P.D. Si no es relevante, dímelo y no vuelvo a escribir.

**E2, subject: `la pregunta que nadie hace`**
> {nombre}, todos preguntan "¿qué IA compramos?". Muy pocos preguntan "¿estamos listos?".
>
> Antes de lanzar cualquier bot, reviso dos cosas: qué % de tus procesos está documentado (y si el KB
> se actualiza cuando cambian), y si tu CRM tiene suficiente historial y una IA nativa que alguien
> esté usando de verdad.
>
> Operamos ~198 mil contactos al mes para fintechs y lo vemos todos los días: ahí se gana o se pierde
> un proyecto de IA.
>
> ¿Te sirve que lo revisemos para {empresa}? Es gratis.

**E3, subject: `no todo se debe automatizar`**
> {nombre}, un dato incómodo: en {industria}, contactos como {ejemplo_modo_D} *no* deberían ir a un
> bot. Si la IA se equivoca, el costo es mucho mayor que el contacto.
>
> Calificamos cada motivo de contacto por esfuerzo del cliente, impacto y si la decisión es blanco o
> negro, para saber cuáles automatizar, cuáles asistir y cuáles dejar con personas.
>
> Si quieres ver dónde está {empresa}, son 3 minutos: {scorecard_link}

**E4, subject: `¿lo cierro?`**
> {nombre}, no quiero llenarte el inbox. Cierro el tema por ahora.
>
> Si en algún momento te preguntan "¿cuál es nuestro plan de IA en atención?", respóndeme este correo
> y te mando el diagnóstico de {empresa}. Ya está hecho.
>
> Beto

### English (P1, economic buyer)

**E1, subject: `your help center + AI`**
> Hi {first_name},
>
> I looked at {company}'s help center before writing: {hook_finding}.
>
> I mention it because it's the #1 reason AI bots hallucinate or stall at 15–20% resolution. It's
> rarely the model. It's the knowledge you ground it on.
>
> I put together a quick outside-in read on how AI-ready {company}'s support operation looks. Want me
> to send it over?
>
> Beto
> CEO, EvolveCX
>
> P.S. If this isn't relevant, tell me and I won't follow up.

**E2, subject: `the question nobody asks`**
> {first_name}, everyone asks "which AI should we buy?" Almost nobody asks "are we ready?"
>
> Before any bot goes live, I check two things: what % of your processes are documented (and whether
> the KB gets updated when they change), and whether your CRM has the history, plus native AI that
> someone actually uses.
>
> We run ~198k contacts a month for fintechs. That's where AI projects are won or lost.
>
> Worth checking for {company}? It's free.

**E3, subject: `not everything should be automated`**
> {first_name}, an uncomfortable truth: in {industry}, contacts like {mode_D_example} shouldn't go to
> a bot. When AI gets those wrong, the cost is far higher than the contact.
>
> We score every contact reason on customer effort, impact, and whether the decision is black-and-white,
> so you know what to automate, what to assist, and what to keep human.
>
> If you want to see where {company} lands, it takes 3 minutes: {scorecard_link}

**E4, subject: `close the loop?`**
> {first_name}, I don't want to crowd your inbox, so I'll close this out.
>
> If someone asks you "what's our AI plan for support?", reply to this and I'll send {company}'s
> readiness read. It's already done.
>
> Beto

### Champion angle (P2) for E1, Spanish
> Hola {nombre}, vi que {empresa} usa {helpdesk} y {hook_finding}.
> Cuando un bot entra sobre un KB escrito para personas, inventa respuestas. Nosotros mapeamos cada
> proceso dos veces: una versión para la IA (reglas cerradas, límites, escalaciones) y una para el
> equipo (paso a paso, el porqué). ¿Te comparto la plantilla que usamos?

> Offering the template is a deliberate "give first" ask for champions. Send the
> [AI-friendly Process Record template](frameworks/dual-process-mapping.md#2-process-record-schema-source-of-truth)
> as a PDF.

### LinkedIn
- **Connect (ES):** "Hola {nombre}, sigo de cerca cómo los equipos de CX en {industria} están llevando
  IA a su operación. Me encantaría conectar."
- **Follow-up (ES):** "Gracias por conectar. Te escribí por correo sobre el centro de ayuda de
  {empresa}. Si te sirve, te mando el diagnóstico por aquí."

## 4. Existing client expansion play (start here, week 1)

**To:** the decision-maker at each current client. **From:** Beto, personally (not the agent).
> "We've been running your support for {X months}. Before you get pitched AI by five vendors, I want
> to give you an honest answer to 'are we AI-ready?' We'll run our AI Readiness Check on your
> operation at no cost. We already have most of the data. In 10 days you'll have a score, the gaps,
> and which of your contacts should and shouldn't be automated."

Then: Readout → Blueprint (40% off) → Build → convert to Hybrid outcome pricing at renewal.

## 5. Inbound engine: "Are you AI ready?"

| Asset | Description | CTA |
|-------|-------------|-----|
| **Self-serve AI Readiness Score** (evolvecx.io/ai-ready) | 8 questions, instant band, PDF by email. Feeds HubSpot | "Get your full check (free)" |
| **Founder LinkedIn series** (3 posts/week) | "Are you AI ready?" Mondays, with one readiness question explained. Teardowns of public help centers (anonymized). Stories of the bot that shouldn't have handled X. Behind-the-scenes on our own AI SDR | Comment "READY" for the scorecard |
| **Guide (lead magnet)** | "AI-friendly vs human-friendly process maps: the template" | Email gate |
| **Benchmark report (quarterly)** | "State of AI readiness in LATAM CX": aggregated, anonymized Readiness Check data | PR + LinkedIn + outbound hook |
| **Webinar / roundtable (monthly)** | 45 min with 1 CX leader guest: "What we automated and what we kept human" | Registration list = warm leads |
| **WhatsApp concierge** | The Qualifier agent on a WhatsApp number shown on the site | Shows the product in action |

**Content cadence, first 90 days:** 36 LinkedIn posts, 1 guide, 3 webinars, and 1 benchmark report
(once 15+ checks are completed).

## 6. Referral & partner motion

- **CRM/helpdesk partners:** apply to the partner programs of Zendesk, Intercom, HubSpot, and Kustomer
  as an implementation/services partner in LATAM. Native AI vendors need services partners to drive
  adoption of the AI their customers already bought, and that's our Tier 2 "native configuration" offer.
- **Investor/VC platform teams:** offer portfolio-wide Readiness Checks (fintech VCs in MX/LATAM).
- **Ask every satisfied client for 2 intros** right after a positive readout or QBR.
