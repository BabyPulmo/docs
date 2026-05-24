# BABY PULMO

**"Child's Voice" — AI Pediatric Cough Diagnostic for Rural Bangladesh**

**Track:** HealthTech (AI-Augmented Public & Maternal Health Systems)  •  **Team Lead:** [your name]  •  **NRB Advisor:** [name + role]  •  **Demo:** https://babypulmo.com  •  **Code:** https://github.com/Shishukantho/babypulmo

---

## Problem

Pneumonia kills **740,000 children under 5 globally each year** (WHO) — the single largest infectious killer of children. Bangladesh: **~25,000 child deaths/year** from acute respiratory infections. Rural Bangladesh has **~1 doctor per 8,000 people**; **63% of Bangladeshi children with pneumonia are NEVER taken to a qualified provider** because caregivers cannot distinguish pneumonia from a common cold (BDHS 2022). Average time-to-care: **36+ hours** after symptom onset — by which point severe pneumonia can be fatal.

## AI Architecture

Eight-layer AI-native system matching the BuildFest reference architecture. (1) **User Interaction** — Twilio WhatsApp Bangla voice + IVR fallback. (2) **Audio Preprocessing** — WebRTC noise removal, cough segmentation, quality gate. (3) **AI Intelligence** — Wav2Vec2-XLSR-53 fine-tuned on Coswara (IISc Bangalore, 5,000+ South Asian respiratory samples) + COUGHVID, six-class pediatric respiratory classification with confidence + Grad-CAM spectrogram explainability. (4) **Knowledge Retrieval** — Supabase pgvector RAG over WHO IMCI + Bangladesh DGHS pediatric protocols using text-embedding-3-large. (5) **Decision Layer** — *rules-gated severity (NOT LLM discretion)*; Claude generates Bangla audio guidance grounded in retrieved protocols. (6) **Agent Orchestration** — auto-escalation to nearest CHW via PostGIS-routed alert with audio + GPS. (7) **Data Infrastructure** — Supabase Postgres + immutable audit log + PostGIS geo-index. (8) **Deployment** — Vercel edge + Modal serverless inference.

## Data Strategy

**Training data:** Coswara (5,000+ South Asian respiratory recordings), COUGHVID (EPFL, 25,000+), ICBHI pediatric chest sound database — all public. **Knowledge base:** WHO IMCI handbook, Bangladesh DGHS pediatric guidelines, UNICEF pneumonia guidance — all public domain. **User recordings** stored de-identified with opt-in consent. **BMRC ethics review path** identified. **Languages:** Bangla (primary), English; TTS via ElevenLabs multilingual v2. **Bias monitoring** through planned Bangladeshi cohort fine-tuning in Phase 1.

## Demo

Caregiver sends a 30-second cough recording to WhatsApp → AI classifies in **<10 seconds** with confidence + Grad-CAM heatmap → Claude generates Bangla audio guidance grounded in WHO IMCI → if severity rule triggers, automatic CHW alert with audio attachment + GPS → CHW dashboard receives ranked alert. Live demo URL: **https://babypulmo.com**. Open source code: **https://github.com/Shishukantho/babypulmo**.

## Scalability Roadmap

**Phase 1 (M1–6):** Pilot with BRAC community health unit in Bogura district — 1,000 children, validate classifier accuracy in field, BMRC ethics review. **Phase 2 (M6–12):** Scale to 3 districts; partner with DGHS National IMCI program; integrate with Bangladesh Telemedicine network. **Phase 3 (Y2):** Bangladesh national rollout (15M U5 children); $5M B2G contract target; UNICEF + Save the Children + BRAC licensing. **Phase 4 (Y3–5):** India, Pakistan, Nigeria, Indonesia, Philippines — same architecture; swap TTS language and country protocol RAG.

## Ethical Safeguards

**Decision-support framing** (not diagnostic device); strong Bangla disclaimer on every reply. **Rules-gated severity** — red-flag escalation is decided by deterministic rules over classifier output, *never* by LLM discretion. **Mandatory human-in-loop:** all severe classifications routed to a real Community Health Worker with audio attached. **Explainability** via Grad-CAM spectrogram heatmap on every classification. **WHO IMCI clinical alignment.** **Immutable audit log** of every interaction (BMRC ethics review trail). **Bias mitigation** through field validation with pediatric Bangladeshi cohort.

## KPIs (12-Month Targets)

- **Time-to-care reduction:** 36h → <2h for severe cases
- **Classifier sensitivity** on pediatric pneumonia: **≥84%** (matching JAMA Pediatrics 2018 benchmark)
- **Children enrolled:** 100,000 (Y1) → 15M (Y3 Bangladesh)
- **U5 mortality reduction** in pilot districts: **−15%** vs baseline
- **CHW response time:** <30 min for alerts in pilot districts

## Global Readiness / NRB Collaboration

Architecture is cloud-native and language-agnostic. **TAM:** 730M U5 children globally; **SAM:** 250M in South Asia + Sub-Saharan Africa where pneumonia mortality is concentrated. **Pfizer acquired adult cough-AI company ResApp Health for AUD $179M (USD ~$120M) in August 2022** — same scientific category, validated commercial precedent. Baby Pulmo is the LMIC-deployable, Bangla-first, pediatric-focused version. **NRB Advisor: [name, role, affiliation]** — providing architecture review and clinical guidance.

## Contact

Md Ferdous Alam · pysoftbd@gmail.com · +8801724111475
