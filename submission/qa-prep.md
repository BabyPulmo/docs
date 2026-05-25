# Baby Pulmo — Finals Q&A Preparation

## Core Framing

> Baby Pulmo is an AI-assisted pediatric respiratory triage and decision-support platform, not an autonomous diagnostic device.

---

# Q1 — “What’s your actual accuracy?”

## ------------ Answer --------------

Our target is the published JAMA Pediatrics 2018 benchmark of 84% pediatric pneumonia sensitivity. 

Realistically, we expect early lab performance around 70–78%, with lower field performance initially around 58–68%. 

That’s why Baby Pulmo is designed as a decision-support system with human-in-the-loop CHW escalation, not an autonomous diagnostic tool.

## Numbers / References

- JAMA Pediatrics 2018 benchmark: 84%
- Expected lab sensitivity: 70–78%
- Expected field sensitivity: 58–68%

Reference:
- submission/accuracy.md

---

# Q2 — “What’s your regulatory pathway?”

## ------------ Answer --------------

We position Baby Pulmo as a decision-support and triage platform, not a diagnostic device. 

Phase 1 starts with BMRC ethics review and a BRAC-supported pilot, with all severe cases escalated to human CHWs.

## Numbers / References

- BMRC ethics review planned
- 1,000-child pilot in Bogura
- Human-in-loop escalation

References:
- submission/summary.md
- submission/accuracy.md

---

# Q3 — “How is this different from Hyfe or Sonde?”

## ------------ Answer --------------

Most competitors focus on adult respiratory monitoring in high-income markets. 

Baby Pulmo is pediatric-focused, Bangla-first, WhatsApp-native, and integrated into rural CHW healthcare workflows.

## Numbers / References

- Bangla-first deployment
- WhatsApp-native workflow
- ~$0.003 interaction cost

Reference:
- submission/competitive-analysis.md

---

# Q4 — “What’s the exit opportunity here?”

## ------------ Answer --------------

Pfizer acquired cough-AI company ResApp for AUD $179M, proving commercial demand in this category. 

Our likely pathways are government deployment contracts, NGO partnerships, or strategic acquisition.

## Numbers / References

- ResApp acquisition: AUD $179M
- Bangladesh target: 15M children

References:
- submission/financials.md
- submission/competitive-analysis.md

---

# Q5 — “What are your unit economics?”

## ------------ Answer --------------

Our projected infrastructure cost is about $0.003 per interaction because we use lightweight audio inference instead of imaging-scale AI. 

The business model is NGO and government deployment contracts, not caregiver subscriptions.

## Numbers / References

- ~$0.003 per interaction
- ~$7/month prototype infra target

Reference:
- submission/financials.md

---

# Q6 — “How do you handle privacy and consent?”

## ------------ Answer --------------

All recordings are opt-in and stored de-identified. 

We maintain immutable audit logs and plan BMRC-reviewed deployment with strict human oversight.

## Numbers / References

- Opt-in consent
- Immutable audit logs
- BMRC review pathway

References:
- submission/summary.md
- submission/accuracy.md

---

# Q7 — “What happens when the AI is wrong?”

## ------------ Answer --------------

The system assumes the AI will sometimes be wrong. 

That’s why uncertain inputs are rejected, severe cases are escalated automatically, and human CHWs stay in the loop.

## Numbers / References

- Confidence gating
- Human-in-loop escalation
- CHW review on severe cases

Reference:
- submission/accuracy.md

---

# Q8 — “Why WhatsApp instead of an app?”

## ------------ Answer --------------

WhatsApp removes app-download friction in rural Bangladesh. 

Caregivers already understand voice notes, making onboarding much faster and cheaper than a standalone app.

## Numbers / References

- Lower caregiver CAC
- Voice-first onboarding
- No app-install dependency

References:
- submission/financials.md
- submission/competitive-analysis.md

---

# Q9 — “How do you scale to 15 million children?”

## ------------ Answer --------------

The scaling model relies on CHW network multiplication, not centralized hospitals. 

The architecture is lightweight and can expand to other LMICs mainly through language and protocol localization.

## Numbers / References

- Year-3 target: 15M children
- LMIC expansion roadmap

Reference:
- submission/financials.md

---

# Q10 — “What if Meta changes WhatsApp policies?”

## ------------ Answer --------------

The platform is channel-agnostic. 

WhatsApp is the fastest deployment path today, but the roadmap already includes Telegram, IVR, and SMS fallback options.

## Numbers / References

- WhatsApp primary deployment
- Telegram/SMS fallback roadmap
- IVR support planned

References:
- submission/summary.md
- submission/financials.md

---

# Final Coaching Notes

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

- Keep answers under 30 seconds
- Answer directly first
- Use numbers confidently
- Admit limitations honestly
- Stay calm and concise

Recommended rehearsal:
- Ferdous
- Shanta
