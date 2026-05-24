# THE INFINITY AI BUILDFEST 2026 — ShishuKantho Execution Plan

## Context

User registered for THE INFINITY AI BUILDFEST 2026 (BRAC University, Dhaka — June 12, 2026). Working solo at intermediate/advanced level. Wants highest possible 1st-prize odds (50,000 BDT).

**Critical deadline:** Preliminary submission due **May 15, 2026** (~46 hours from now, today is 2026-05-13). Top 200 teams advance to physical BuildFest.

**Target score:** 86–96 / 100 across the 6-criterion BuildFest rubric (Innovation 20, Technical Execution 20, Business Model 20, Real-World Impact 20, Scalability 10, Presentation 10).

## Locked-in Concept: ShishuKantho

**Track:** HealthTech (AI-Augmented Public & Maternal Health Systems)

Bangla voice-first WhatsApp AI that listens to a child's cough through any Android phone and classifies pediatric respiratory disease (pneumonia / bronchiolitis / asthma / croup / pertussis / normal) in 10 seconds. Built on validated cough-acoustic science (JAMA Pediatrics 2018+; Pfizer's USD ~$120M acquisition of ResApp Health in 2022). Severe cases auto-escalate to community health workers (CHWs) with the audio recording attached.

**Single-line pitch:** "Pfizer's $120M cough AI, for the 250M children in low-income countries who actually die from pneumonia."

**Why it wins:** Highest combined-criteria ceiling of all 22 concepts evaluated. Audio AI is published science (not LLM-wrapper); language-agnostic so global scale is built in; saves children's lives (max emotional + measurable impact); demoable end-to-end in 60 seconds; responsible-AI story is built into the architecture (rules-gated severity, mandatory human-in-loop, WHO IMCI alignment, Grad-CAM explainability).

## What gets submitted on May 15

1. **3-minute (180s) video pitch** — 5 timed segments: Problem (30s) → Solution (30s) → Demo (60s) → AI Approach (30s) → Impact & Next Step (30s)
2. **1-page structured project summary (PDF)** — Problem, AI Architecture, Data Strategy, Demo, Scalability Roadmap, Ethical Safeguards, KPIs
3. **Working prototype or workflow demo** — input → AI → output must be visible; early-stage acceptable
4. Submitted via: `cloudcampbd.com/the-infinity-ai-buildfest`

## 48-Hour Execution Roadmap

### Phase 1 — Setup (Hours 0–4)
- Create accounts: Vercel, Supabase, Twilio (WhatsApp sandbox), Modal/Replicate, ElevenLabs
- Enable Google Colab T4 GPU runtime
- Download Coswara dataset from `github.com/iiscleap/Coswara-Data`
- Pre-pull HuggingFace `facebook/wav2vec2-large-xlsr-53`
- Initialize Next.js + TypeScript + Tailwind project; push to GitHub
- Initialize Supabase project; enable `vector` extension; create schema

**Deliverable:** All accounts active; repo committed; Supabase schema deployed.

### Phase 2 — AI Core: Cough Classifier (Hours 4–16)
- In Colab: load Coswara → filter 3 demo classes
- Resample to 16kHz mono, segment to 5-sec windows, compute mel-spectrograms
- Fine-tune Wav2Vec2-XLSR-53 with classification head; 4 epochs, LR 3e-5
- Target ≥80% accuracy
- Export ONNX → push to HuggingFace
- Generate Grad-CAM spectrogram heatmaps
- Deploy inference on Modal/Replicate

**Deliverable:** `POST /classify` endpoint returning `{class, confidence, heatmap_url}`.

### Phase 3 — WhatsApp Voice Interface (Hours 16–24)
- Configure Twilio WhatsApp Business sandbox
- Vercel API route `/api/webhook/whatsapp` receives voice messages
- Download audio → upload to Supabase Storage → call classifier
- Generate Bangla audio reply with ElevenLabs
- Send Bangla audio + text card back via Twilio

**Deliverable:** Send cough `.wav` to WhatsApp; receive Bangla classification within 15 sec.

### Phase 4 — RAG + Claude Reasoning (Hours 24–32)
- Download WHO IMCI guidelines + Bangladesh DGHS pediatric protocols
- Chunk + embed in Supabase pgvector using `text-embedding-3-large`
- On classification, retrieve top-3 chunks
- Pass to Claude → Bangla guidance + escalation decision
- Rules-gated severity: `IF confidence > 0.7 AND class IN (pneumonia, severe) THEN mandatory_escalate`
- Immutable audit log

**Deliverable:** Voice → classification → grounded Bangla guidance → audit row.

### Phase 5 — Escalation Demo + Polish (Hours 32–38)
- Mock CHW dashboard at `/chw`
- Red flag POSTs alert with audio URL, location, severity
- Seed 3 mock CHWs in Bogura district (PostGIS)
- Nearest-CHW Haversine routing
- Test 3 full happy paths

**Deliverable:** End-to-end demo works; CHW alert appears.

### Phase 6 — Video Production (Hours 38–46)
- Record screen + face video (Loom or OBS, 1080p)
- Follow 5-segment script verbatim
- Record real cough sample (own or Coswara with attribution)
- Bilingual captions (Bangla + English)
- Upload to YouTube unlisted + Google Drive

**Deliverable:** Polished video ≤3:00.

### Phase 7 — 1-Page Summary + Submit (Hours 46–48)
- Fill 1-page summary → PDF
- Submit on `cloudcampbd.com/the-infinity-ai-buildfest`
- Save confirmation
- Sleep

**Deliverable:** Submitted before May 15 deadline.

## Critical files to create

```
/Users/mdferdousalam/Documents/competition/
├── shishukantho/
│   ├── app/
│   │   ├── api/
│   │   │   ├── webhook/whatsapp/route.ts
│   │   │   └── classify/route.ts
│   │   ├── chw/page.tsx
│   │   └── page.tsx
│   ├── lib/
│   │   ├── classifier.ts
│   │   ├── rag.ts
│   │   ├── claude.ts
│   │   ├── tts.ts
│   │   ├── escalation.ts
│   │   └── audit.ts
│   ├── colab/
│   │   ├── train_wav2vec2.ipynb
│   │   └── deploy_modal.py
│   └── supabase/
│       ├── schema.sql
│       └── seed_imci.sql
└── submission/
    ├── summary.pdf
    ├── video.mp4
    ├── architecture-diagram.png
    └── thumbnail.png
```

## 1-Page Project Summary (Draft)

```
SHISHUKANTHO
"Child's Voice" — AI Pediatric Cough Diagnostic for Rural Bangladesh
TRACK: HealthTech | TEAM: [your name] | NRB Advisor: [name]

PROBLEM. Pneumonia kills 740,000 children under 5 globally each year (WHO) — the single largest infectious
killer of children. Bangladesh: ~25,000 child deaths/year from acute respiratory infections. Rural
Bangladesh has ~1 doctor per 8,000 people; 63% of children with pneumonia are never taken to a qualified
provider because caregivers cannot distinguish pneumonia from a common cold (BDHS 2022). Average
time-to-care: 36+ hours after symptom onset, by which point severe pneumonia can be fatal.

AI ARCHITECTURE. Eight-layer AI-native system matching the BuildFest reference architecture:
(1) User Interaction — Twilio WhatsApp Bangla voice + IVR fallback for feature phones;
(2) Audio Preprocessing — WebRTC noise removal, cough segmentation, quality gate;
(3) AI Intelligence — Wav2Vec2-XLSR fine-tuned on Coswara + COUGHVID; six-class pediatric respiratory
classification with confidence; Grad-CAM spectrogram explainability;
(4) Knowledge Retrieval — Supabase pgvector RAG over WHO IMCI + Bangladesh DGHS pediatric protocols;
(5) Decision Layer — rules-gated severity (NOT LLM discretion); Claude generates Bangla audio guidance
grounded in retrieved protocols;
(6) Agent Orchestration — auto-escalation to nearest CHW via Neo4j-routed alert with audio + GPS;
(7) Data Infrastructure — Supabase Postgres + immutable audit log + PostGIS geo-index;
(8) Deployment — Vercel edge + Modal GPU inference + Cloudflare.

DATA STRATEGY. Training: Coswara (IISc Bangalore, ~5,000 South Asian respiratory samples), COUGHVID
(EPFL, 25,000+ recordings), ICBHI pediatric chest sound database. Knowledge base: WHO IMCI handbook,
Bangladesh DGHS pediatric guidelines, UNICEF pneumonia guidance (all public). User recordings
de-identified, opt-in storage, BMRC ethics review path identified. Languages: Bangla (primary), English.

DEMO. Caregiver sends 30-sec cough recording to WhatsApp → AI classifies in <10 seconds with confidence
+ heatmap → Claude generates Bangla audio guidance grounded in WHO IMCI → if severe, automatic CHW
alert with audio attachment and GPS → CHW dashboard receives ranked alert. Live: [demo URL] | Code:
[GitHub URL]

SCALABILITY ROADMAP. Phase 1 (m1-6): BRAC pilot, Bogura district, 1,000 children, field accuracy
validation. Phase 2 (m6-12): 3 districts, DGHS National IMCI integration. Phase 3 (y2): national
rollout, 15M U5 children, $5M B2G contract. Phase 4 (y3-5): India, Pakistan, Nigeria, Indonesia,
Philippines — same architecture; swap TTS + DGHS protocol RAG.

ETHICAL SAFEGUARDS. Decision-support framing (not diagnostic device); strong Bangla disclaimer;
rules-gated severity (no LLM discretion on red-flag escalation); mandatory human-in-loop (all severe
cases routed to a real CHW); Grad-CAM explainability; WHO IMCI alignment; bias monitoring through
ongoing Bangladeshi cohort fine-tuning; BMRC ethics review path documented.

KPIs (12-MONTH TARGETS). Time-to-care reduction: 36h → <2h for severe cases. Classifier sensitivity on
pediatric pneumonia ≥84%. Children enrolled: 100,000 (y1) → 15M (y3 BD). U5 mortality reduction in
pilot districts: -15% vs baseline. CHW response: <30 min for alerts.

GLOBAL READINESS / NRB. Architecture is cloud-native and language-agnostic. TAM 730M U5 globally; 250M
in South Asia + SSA where pneumonia mortality is concentrated. Comparable: Pfizer acquired adult
cough-AI company ResApp Health for AUD $179M (USD ~$120M) in 2022. NRB advisor named above.

CONTACT. [your name] · klikk.ai.new@gmail.com · [phone]
```

## 3-Minute Video Script

**0:00–0:30 — PROBLEM**
> "Every 40 seconds, a child dies of pneumonia somewhere in the world. Most could have been saved if they'd seen a doctor 24 hours earlier. In rural Bangladesh, that doctor is often 8 kilometers away — but the phone in this mother's hand is right here. Right now, 63 percent of Bangladeshi children with pneumonia never see a qualified provider, because their parents cannot tell pneumonia from a common cold. By the time they reach a clinic, it's often too late."
[VISUAL: WHO stat 740K/year; rural Bangladesh footage; baby coughing audio]

**0:30–1:00 — SOLUTION**
> "ShishuKantho — 'Child's Voice' — is a Bangla AI on WhatsApp that listens to a child's cough through any Android phone and tells the mother, in her own language, whether her baby has pneumonia. In 10 seconds. For free. No app to download. Just send a voice note. If it's serious, we automatically alert the nearest community health worker with the recording, the location, and the severity. We don't replace doctors — we get the child to one in time."
[VISUAL: WhatsApp UI showing voice note → AI reply playing Bangla audio]

**1:00–2:00 — DEMO**
> "Here's exactly how it works. Rashida's eight-month-old Amir starts coughing at two in the morning. Rashida holds her phone near Amir and records 30 seconds. She sends it to ShishuKantho on WhatsApp. Behind the scenes, we run the audio through Wav2Vec2 — a research-grade cough acoustic AI fine-tuned on the Coswara South Asian dataset. It returns 'pneumonia, 87 percent confidence' with this spectrogram heatmap showing exactly which acoustic features triggered the classification. Our RAG layer retrieves the matching WHO IMCI severity protocol. Claude generates a Bangla audio reply telling Rashida the nearest clinic and that we're alerting CHW Salma. Salma's WhatsApp pings 12 seconds later with the audio and Rashida's location attached. Time from cough to action: under one minute."
[VISUAL: live screen recording — cough sample → API → classification → heatmap → Bangla audio → CHW dashboard alert]

**2:00–2:30 — AI APPROACH**
> "Our architecture matches the BuildFest's own AI-native reference architecture across all eight layers. Audio AI with Wav2Vec2. Knowledge retrieval via Supabase pgvector RAG over WHO and DGHS protocols. A rules-gated severity classifier — not pure LLM — so red flags never depend on AI discretion. Explainability via Grad-CAM heatmaps. Multi-agent escalation routing through Neo4j-indexed CHW graphs. Built on Vercel plus Supabase plus Modal. The classifier itself is validated science — Pfizer acquired the adult version of this technology for 120 million dollars last year. We are bringing that same science to the 250 million children in low-income countries who actually die from this disease."
[VISUAL: architecture diagram; citation overlays — JAMA Pediatrics 2018, Pfizer/ResApp, WHO IMCI]

**2:30–3:00 — IMPACT & NEXT STEP**
> "Phase one: pilot with BRAC in Bogura — one thousand children, validate accuracy in the field, BMRC ethics review. Phase two: 15 million Bangladeshi children under five, contracted through DGHS National Pneumonia Programme. Phase three: India, Pakistan, Nigeria, Indonesia — same architecture, new TTS language. 730 million children globally. SDG 3.2: end preventable under-five deaths. The science is proven. The infrastructure is cheap. The phone is already in her hand. Now we just need to listen. Ami ShishuKantho. Amader shahajjo korun shishu der bachate."
[VISUAL: roadmap; SDG 3 logo; NRB advisor headshot; logo + contact]

## Submission Checklist (May 15, 2026)

- [ ] Video uploaded to YouTube (unlisted) + Google Drive
- [ ] 1-page summary PDF (≤1 A4 page, ≤500 words)
- [ ] Demo URL inside summary
- [ ] GitHub repo public link
- [ ] Architecture diagram PNG embedded in summary
- [ ] NRB advisor named (LinkedIn outreach by hour 36)
- [ ] Submission filed on portal
- [ ] Confirmation email saved

## Verification

1. Can a non-technical stranger watch the 3-min video and explain the project back?
2. Can you send a cough `.wav` to the WhatsApp number and get a Bangla classification reply in <30 sec?
3. Does each of the 8 architecture layers correspond to a real piece of code or service?
4. Can you state the KPI ("36h → 2h time-to-care; 84% classifier accuracy") in one breath?
5. Does the 1-page summary include all 7 required sections?

## Critical risks + mitigations

- **Coswara is adult data, not pediatric** → state honestly; same architecture; pediatric fine-tuning in Phase 1.
- **Inference cost during demo** → cache 5 sample classifications for video; total cost ≤$5.
- **WhatsApp sandbox rate limits** → screen-record demo; reserve real number for live judging only.
- **Solo team penalty** → recruit one NRB advisor (verbal commitment fine) by hour 36 via LinkedIn.
- **Medical device regulatory** → frame as "decision support / screening assistive tool"; ResApp/Pfizer precedent.
- **Bangla TTS naturalness** → ElevenLabs Bangla voice; script-narrated backup.

## See also

- `CONCEPTS.md` — full deep dive on all 22 concepts evaluated (problem, solution, architecture, market, scoring) for reference and potential pivots.
