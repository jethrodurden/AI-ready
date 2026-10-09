# Kit 02 — AI Readiness Check questionnaire

Paste this into a Google Form or HubSpot form. It takes the client about 20 minutes. The analyst
scores it with the [AI Readiness Scorecard](../frameworks/ai-readiness-scorecard.md). Each question
maps to a scorecard item (A1–B7), with the scores shown as **[0] / [2] / [4]**. Answers between two
levels get 1 or 3 points.

**Form intro (ES):** "Este cuestionario nos ayuda a medir qué tan lista está tu operación para la IA.
No hay respuestas buenas o malas: si no sabes algo, elige 'No sé' y lo revisamos juntos."
**Form intro (EN):** "This questionnaire helps us measure how ready your operation is for AI. There
are no wrong answers. If you don't know something, pick 'Not sure' and we'll review it together."

## Section 0: About the operation (not scored, used for sizing)

| # | Question (EN / ES) | Type |
|---|--------------------|------|
| 0.1 | Company, your name, role / Empresa, nombre, puesto | Text |
| 0.2 | Customer contacts per month, approx. / Contactos de clientes al mes, aprox. | Number |
| 0.3 | Channels and approx. % of volume each (chat, WhatsApp, email, voice, other) / Canales y % aprox. | Text |
| 0.4 | Number of support agents (in-house + outsourced) / Número de agentes (internos + externos) | Number |
| 0.5 | Top 5 reasons customers contact you / Los 5 motivos principales de contacto | Text |
| 0.6 | Languages / Idiomas | Checkbox |

## Section A: Processes & knowledge

| # | Question (EN / ES) | Options → score |
|---|--------------------|-----------------|
| A1 | Do agents use a knowledge base in their daily work? / ¿Los agentes usan una base de conocimiento en su día a día? | No KB; docs in chats/drives **[0]** · KB exists, partially used **[2]** · Single KB used in every contact **[4]** · Not sure |
| A2 | What % of contact reasons have a documented, step-by-step process? / ¿Qué % de los motivos de contacto tiene un proceso documentado paso a paso? | < 30% **[0]** · 30–70% **[2]** · > 70% **[4]** · Not sure |
| A3 | How often do your processes or policies change? / ¿Con qué frecuencia cambian los procesos o políticas? | Weekly or more **[0]** · Monthly **[2]** · Quarterly or less **[4]** |
| A4 | When a process changes, how fast is the KB updated? / Cuando cambia un proceso, ¿qué tan rápido se actualiza el KB? | Rarely / no one owns it **[0]** · Within weeks **[2]** · Within 48h, with a named owner **[4]** |
| A5 | Is there a named KB owner and a change-request process? / ¿Hay un responsable del KB y un proceso para solicitar cambios? | No **[0]** · Informal **[2]** · Yes, with an SLA **[4]** |
| A6 | Do the KB, macros, and what agents actually do match? / ¿Coinciden el KB, las macros y lo que realmente hacen los agentes? | Often contradict **[0]** · Sometimes **[2]** · Consistent **[4]** · Not sure *(analyst verifies by sampling)* |
| A7 | How are articles written? / ¿Cómo están escritos los artículos? | Long docs with many topics **[0]** · Mixed **[2]** · One topic per article, dated, versioned **[4]** |

## Section B: Systems & data

| # | Question (EN / ES) | Options → score |
|---|--------------------|-----------------|
| B1 | Which CRM/helpdesk do you use? / ¿Qué CRM o helpdesk usan? | None / spreadsheets / WhatsApp on phones **[0]** · Basic helpdesk **[2]** · Zendesk, Intercom, Salesforce, HubSpot, Kustomer, Freshdesk or similar **[4]** + text field for the name |
| B2 | How many months of contact history do you keep? / ¿Cuántos meses de historial guardan? | < 3 months or < 2k contacts/mo **[0]** · 3–6 months **[2]** · 6+ months and > 10k/mo **[4]** |
| B3 | Are contacts tagged by reason? How reliable is it? / ¿Los contactos se etiquetan por motivo? ¿Qué tan confiable es? | No tagging **[0]** · Tagged, inconsistent **[2]** · Consistent, > 80% tagged **[4]** |
| B4 | Does your CRM include AI (bot, agent assist)? Is it on? / ¿Su CRM incluye IA? ¿Está encendida? | No **[0]** · Licensed but off, or pilot **[2]** · Live and measured **[4]** · Not sure |
| B5 | If AI is live: what % of contacts does it fully resolve? / Si hay IA activa, ¿qué % resuelve por completo? | < 10% or unknown **[0]** · 10–30% **[2]** · > 30% with CSAT tracked **[4]** · N/A (score 0) |
| B6 | Can a bot look up or change data (order, payment, account) through an API? / ¿Un bot puede consultar o modificar datos vía API? | No APIs **[0]** · Read-only **[2]** · Read + write with authentication **[4]** · Not sure |
| B7 | Are conversations (chat, WhatsApp, voice) stored and exportable? / ¿Se guardan y se pueden exportar las conversaciones? | No **[0]** · Partially (e.g., no voice transcripts) **[2]** · All channels **[4]** |

## Section C: Goals (not scored, used for the readout)

| # | Question | Type |
|---|----------|------|
| C1 | What would you want AI to do for your operation in the next 6 months? / ¿Qué te gustaría que hiciera la IA en tu operación en 6 meses? | Text |
| C2 | Have you tried AI in support before? What happened? / ¿Ya probaron IA en atención? ¿Qué pasó? | Text |
| C3 | Which contacts should *never* be handled by AI, in your view? / ¿Qué contactos *nunca* debería atender una IA, en tu opinión? | Text |
| C4 | Can you share an export of 1 month of tickets and access to the KB (read-only)? / ¿Pueden compartir un export de 1 mes de tickets y acceso de lectura al KB? | Yes / Need approval / No |

> **"Not sure" answers** score 0 until the analyst verifies them. They're also good readout material:
> "you don't know whether your bot is turned on" is a finding in itself.
>
> **For current clients**, the analyst pre-fills everything EvolveCX already knows (volume, channels,
> helpdesk, tagging, KB access). The client then only confirms and answers A3–A5, B4–B6, and Section C.
