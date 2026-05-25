# Baby Pulmo — Finals Q&A Preparation

## Core Framing

> Baby Pulmo is an AI-assisted pediatric respiratory triage and decision-support platform, not an autonomous diagnostic device.

---

# Q1 — “What’s your actual accuracy?”

Our Phase 1 target is the published JAMA Pediatrics 2018 benchmark of 84% pediatric pneumonia sensitivity achieved by ResApp. 

Realistically, early lab-stage performance is expected around 70–78%, with lower real-world field performance initially around 58–68% because of background noise and pediatric domain shift. 

That’s why Baby Pulmo is designed as a decision-support and triage system rather than an autonomous diagnostic device. Severe cases are always escalated to a human Community Health Worker.

## Numbers / References

- JAMA Pediatrics 2018 benchmark: 84%
- Expected lab sensitivity: 70–78%
- Expected field sensitivity: 58–68%

Reference:
- submission/accuracy.md

---

# Q2 — “What’s your regulatory pathway?”

We intentionally position Baby Pulmo as a decision-support and triage platform, not a fully autonomous diagnostic device. 

Our regulatory path begins with BMRC ethics review and a BRAC-supported pilot in Bangladesh. Every severe-risk case is escalated to a real Community Health Worker, which keeps the system within a safer human-in-the-loop framework similar to the early ResApp deployment model.

This allows us to validate the system responsibly before pursuing more formal medical-device pathways.

## Numbers / References

- BMRC ethics review planned
- 1,000-child pilot in Bogura
- Human-in-loop escalation

References:
- submission/summary.md
- submission/accuracy.md

---

# Q3 — “How is this different from Hyfe or Sonde?”

Most competitors focus on adult respiratory monitoring in high-income healthcare markets and usually depend on standalone smartphone apps. 

Baby Pulmo is different because it is:
- pediatric-focused,
- Bangla-first,
- WhatsApp-native,
- and integrated into Community Health Worker workflows for rural LMIC healthcare systems.

Our strongest advantage is operational integration with real low-resource healthcare delivery, not only the AI model itself.

## Numbers / References

- Bangla-first deployment
- WhatsApp-native workflow
- ~$0.003 projected interaction cost

Reference:
- submission/competitive-analysis.md

---

# Q4 — “What’s the exit opportunity here?”

The respiratory-AI category already has strong commercial precedent. Pfizer acquired cough-AI company ResApp Health for approximately AUD $179M in 2022 after validating adult respiratory diagnostics. 

Baby Pulmo is positioned differently:
- pediatric-focused,
- LMIC-focused,
- and integrated into public-health delivery systems.

Potential exit pathways include strategic acquisition, NGO/public-health partnerships, and long-term government healthcare contracts.

## Numbers / References

- ResApp acquisition: AUD $179M
- Bangladesh target: 15M children

References:
- submission/financials.md
- submission/competitive-analysis.md

---

# Q5 — “What are your unit economics?”

Our projected infrastructure cost is approximately $0.003 per interaction because the system uses lightweight audio inference rather than imaging-scale AI. 

The stack is optimized for low-resource deployment using Modal serverless inference, Supabase, and lightweight Wav2Vec2 processing. 

The business model is based on NGO and government deployment contracts rather than charging caregivers directly.

## Numbers / References

- ~$0.003 per interaction
- ~$7/month prototype infra target

Reference:
- submission/financials.md

---

# Q6 — “How do you handle privacy and consent?”

All caregiver recordings are opt-in and stored in a de-identified format. 

We maintain immutable audit logs for BMRC review and operational accountability, while avoiding unnecessary personally identifiable information storage. 

Privacy and consent are treated as core infrastructure requirements from day one, not post-launch additions.

## Numbers / References

- Opt-in consent
- Immutable audit logs
- BMRC review pathway

References:
- submission/summary.md
- submission/accuracy.md

---

# Q7 — “What happens when the AI is wrong?”

The architecture is intentionally designed assuming the model will sometimes be wrong. 

Uncertain inputs are rejected through confidence gating, and severe-risk cases are automatically escalated to human Community Health Workers with the original audio attached. 

The system behaves more like a smoke detector than an autonomous doctor — false positives are acceptable, but missed severe pediatric cases are not.

## Numbers / References

- Confidence gating
- Human-in-loop escalation
- CHW review on severe cases

Reference:
- submission/accuracy.md

---

# Q8 — “Why WhatsApp instead of an app?”

WhatsApp dramatically lowers onboarding friction in rural Bangladesh because caregivers already understand voice notes and messaging workflows. 

A standalone healthcare app creates storage, literacy, and installation barriers that reduce adoption in low-resource environments. 

WhatsApp-native deployment allows faster caregiver adoption and lower acquisition cost.

## Numbers / References

- Lower caregiver CAC
- Voice-first onboarding
- No app-install dependency

References:
- submission/financials.md
- submission/competitive-analysis.md

---

# Q9 — “How do you scale to 15 million children?”

The scaling model relies on Community Health Worker network multiplication rather than centralized hospital staffing. 

The architecture itself is lightweight and cloud-native, so expansion mainly requires localization of language, TTS, and healthcare protocols. 

After Bangladesh, the same operational model can extend to India, Pakistan, Nigeria, Indonesia, and the Philippines.

## Numbers / References

- Year-3 target: 15M children
- Multi-country LMIC roadmap

Reference:
- submission/financials.md

---

# Q10 — “What if Meta changes WhatsApp policies?”

The platform is intentionally designed to be channel-agnostic. 

WhatsApp is simply the fastest adoption path today, but the roadmap already includes Telegram, IVR, and SMS fallback options. 

The core value of Baby Pulmo is the respiratory-triage and CHW-escalation infrastructure behind the messaging layer.

## Numbers / References

- WhatsApp primary deployment
- Telegram/SMS fallback roadmap
- IVR support planned

References:
- submission/summary.md
- submission/financials.md

---

# Finals Coaching Notes

## Strong Framing

Use:
- “decision-support”
- “triage”
- “human-in-the-loop”
- “field validation”
- “BMRC-reviewed”

Avoid:
- “AI diagnoses pneumonia”
- “fully autonomous”
- “doctor replacement”

---

# Finals Strategy

- Keep answers around 20–30 seconds
- Answer directly first
- Use numbers confidently
- Admit limitations honestly
- Stay calm and concise

Recommended rehearsal:
- Ferdous
- Shanta
