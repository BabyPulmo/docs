# Baby Pulmo — Financial Model

## Executive Summary

Baby Pulmo is a low-cost AI-assisted pediatric respiratory triage platform designed for rural Bangladesh and other low-resource settings. The platform combines cough-audio AI, WHO IMCI-aligned decision support, and Community Health Worker (CHW) escalation workflows through WhatsApp and voice interfaces.

The business model is designed around:
- Extremely low per-interaction operating cost
- NGO and government partnership deployments
- Public-health infrastructure contracts
- Long-term defensibility through workflow integration, data network effects, and pediatric respiratory specialization

The platform is positioned as a decision-support and triage system rather than an autonomous diagnostic device.

---

# Unit Economics

Target operating cost per caregiver interaction: **~$0.003 USD**

Estimated cost assumptions for a single 30-second interaction:

| Component | Estimated Cost / Interaction |
|---|---:|
| Modal CPU inference (Wav2Vec2) | $0.0008 |
| OpenAI embeddings (RAG retrieval) | $0.0003 |
| Supabase database + pgvector | $0.0002 |
| Twilio / WhatsApp infra | $0.0005 |
| ElevenLabs TTS generation | $0.0007 |
| Misc bandwidth + logging | $0.0005 |
| **Total Estimated Cost** | **~$0.003** |

### Cost Model Notes

- Wav2Vec2 inference is optimized for short (<30 sec) cough audio.
- Modal serverless inference minimizes idle GPU cost.
- Supabase storage costs remain low because audio is compressed and de-identified.
- RAG retrieval cost is low because WHO/DGHS guideline chunks are embedded once and reused.
- TTS cost scales primarily with response length.

At national Bangladesh scale (15M caregivers), infrastructure remains operationally feasible because inference is lightweight relative to imaging or large multimodal medical AI systems.

---

# Caregiver Acquisition Cost (CAC)

Baby Pulmo is free for caregivers. CAC therefore represents the estimated cost to onboard a caregiver into the health-support network.

Primary acquisition channels:
- Community Health Worker referrals
- NGO outreach programs
- WhatsApp / Facebook awareness campaigns
- Word-of-mouth within villages

| Acquisition Channel | Estimated CAC |
|---|---:|
| Meta WhatsApp / Facebook ads | $0.40 |
| CHW-assisted onboarding | $0.05 |
| Organic / word-of-mouth | <$0.02 |
| NGO field campaigns | $0.08 |

### CAC Strategy

The model is intentionally designed to reduce dependence on paid advertising over time.

As CHW density increases and village trust networks form, acquisition is expected to become increasingly organic and referral-driven.

Projected blended CAC:
- Year 1: ~$0.12
- Year 2: ~$0.06
- Year 3: <$0.03

---

# LTV / NGO Value Model

Caregivers are not charged directly.

Instead, Baby Pulmo creates operational value for:
- NGOs
- Public-health systems
- Maternal and child healthcare programs
- Community Health Worker networks

### Per-CHW Operational Value

| Metric | Estimated Impact |
|---|---:|
| Children monitored per CHW / month | 150–300 |
| Severe respiratory escalations identified | 5–10 |
| Time-to-care reduction | 36h → <2h |
| CHW response target | <30 min |
| Pilot district mortality reduction target | −15% |

### NGO Value Proposition

Baby Pulmo provides:
- Earlier respiratory-risk identification
- Reduced delayed escalation
- Rural triage support
- Audit-ready digital interaction logs
- Population-level respiratory trend visibility

This creates measurable operational value even without caregiver monetization.

---

# Growth Projection (Year 1 → Year 3)

| Year | Caregivers Served | Geography |
|---|---:|---|
| Year 1 | 100,000 | Pilot districts in Bangladesh |
| Year 2 | 1,000,000 | Multi-district Bangladesh rollout |
| Year 3 | 15,000,000 | National Bangladesh scale |

### Expansion Pathway

Phase 1:
- BRAC-supported pilot validation
- BMRC ethics review
- Pediatric field validation

Phase 2:
- DGHS / IMCI integration
- Bangladesh Telemedicine partnerships

Phase 3:
- National Bangladesh deployment
- UNICEF / NGO scaling partnerships

Phase 4:
- India
- Pakistan
- Nigeria
- Indonesia
- Philippines

The architecture is language-agnostic and can expand primarily through:
- localized TTS
- local protocol RAG
- regional CHW integrations

---

# Revenue Model

Baby Pulmo does not rely on caregiver subscriptions or advertising.

Primary revenue streams:

| Revenue Stream | Description |
|---|---|
| NGO SaaS deployments | Per-district deployment contracts |
| Government health contracts | DGHS / IMCI / public-health integration |
| Research grants | WHO, UNICEF, Gates Foundation, pediatric-health pilots |
| Analytics & reporting | Aggregate respiratory trend dashboards |
| International licensing | Localized deployments in LMICs |

### Government Contract Opportunity

Target Year-3 Bangladesh public-health deployment:
- Estimated B2G opportunity: **~$5M**

Potential deployment partners:
- DGHS
- UNICEF
- BRAC
- Save the Children
- Telemedicine networks

---

# Series A Pathway

## Target Raise

| Round | Target |
|---|---:|
| Seed / pre-seed | Pilot + validation funding |
| Series A | $3M |
| Target valuation cap | $15M |

### Planned Use of Funds

| Area | Allocation |
|---|---:|
| Model improvement & pediatric fine-tuning | 35% |
| Clinical validation & BMRC studies | 25% |
| CHW operations & rollout | 20% |
| Regulatory / compliance | 10% |
| Hiring & infrastructure | 10% |

### Key Milestones Before Series A

- 100k caregivers enrolled
- BMRC-reviewed field validation
- NGO pilot deployment
- Pediatric sensitivity benchmark ≥84%
- Government partnership discussions initiated

---

# Comparable Companies

| Company | Signal |
|---|---|
| ResApp Health | Acquired by Pfizer for AUD $179M (~USD $120M) |
| Hyfe | Respiratory monitoring company with Series B funding |
| Sonde Health | Voice-biomarker company with Series C backing |

These companies validate investor and commercial interest in respiratory-audio AI systems.

Baby Pulmo differentiates itself through:
- Bangla-first deployment
- Pediatric specialization
- LMIC-focused architecture
- Human-in-the-loop CHW escalation workflow

---

# Financial Risks & Assumptions

## 1. Clinical Validation Risk

Pediatric respiratory AI requires real-world Bangladeshi cohort validation before clinical-scale deployment.

## 2. Government Procurement Delays

Public-health procurement cycles in Bangladesh may be slow and bureaucratic.

## 3. WhatsApp Platform Dependence

Policy or pricing changes from Meta / Twilio could affect onboarding or communication costs.

## 4. Infrastructure Scaling Costs

National-scale deployment may require:
- additional inference optimization
- caching layers
- hybrid edge deployment

## 5. Regulatory Landscape

Future AI-medical-device regulation may increase compliance requirements.

---

# Strategic Positioning

Baby Pulmo is designed as:
- a public-health infrastructure layer,
- not merely a chatbot,
- and not solely an AI model.

The long-term moat comes from:
- CHW integration,
- pediatric respiratory workflow optimization,
- Bangla-first deployment,
- operational data network effects,
- and field validation in low-resource environments.

The company is therefore positioned as a mission-driven but venture-scalable HealthTech platform for emerging markets.
