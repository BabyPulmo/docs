# Baby Pulmo — Finals Q&A Preparation

## Purpose

This document prepares Baby Pulmo team members for likely hostile or high-pressure finals questions.

Goal:
- concise 20–30 second oral answers
- scientifically honest positioning
- operational credibility
- investor-grade clarity

Core framing used throughout:
> Baby Pulmo is an AI-assisted pediatric respiratory triage and decision-support platform, not an autonomous diagnostic device.

---

# Q1 — “What’s your actual accuracy?”

## Recommended Answer

Our Phase 1 target is the published JAMA Pediatrics 2018 benchmark of 84% pediatric pneumonia sensitivity achieved by ResApp. 

Realistically, early lab-stage sensitivity for Baby Pulmo is expected around 70–78%, with lower real-world field performance initially — likely around 58–68% in rural deployment conditions. 

That is why the system is designed as a decision-support and triage platform rather than an autonomous diagnostic device. Confidence gating, deterministic severity rules, and mandatory human-in-the-loop CHW escalation are designed to make the system clinically useful even before full-scale validation.

## Numbers / References

- JAMA Pediatrics 2018 ResApp benchmark: 84% sensitivity
- Expected v0 lab sensitivity: 70–78%
- Expected field sensitivity: 58–68%

Reference:
- submission/accuracy.md

---

# Q2 — “What’s your regulatory pathway?”

## Recommended Answer

Baby Pulmo intentionally avoids positioning itself as a fully autonomous diagnostic device. 

Our planned regulatory pathway begins with BMRC ethics review and NGO-supported pilot deployment in Bangladesh. Severe-risk cases are always escalated to a human Community Health Worker, which keeps the system within a decision-support framework similar to the early ResApp deployment strategy.

This substantially lowers regulatory friction while allowing real-world validation before pursuing more formal medical-device pathways.

## Numbers / References

- BMRC ethics review planned in Phase 1
- 1,000-child BRAC Bogura pilot
- Human-in-loop escalation on every severe case

References:
- submission/summary.md
- submission/ip-strategy.md
- submission/accuracy.md

---

# Q3 — “How is this different from Hyfe or Sonde Health?”

## Recommended Answer

Most incumbents optimize for adult respiratory monitoring or English-language smartphone apps in high-income healthcare systems. 

Baby Pulmo instead focuses on:
- pediatric respiratory triage,
- Bangla-first interaction,
- WhatsApp-native deployment,
- and Community Health Worker escalation workflows for rural LMIC healthcare systems.

Our strongest differentiation is operational integration with low-resource healthcare delivery rather than only the classifier itself.

## Numbers / References

- Bangla-first deployment
- WhatsApp-native workflow
- ~$0.003 projected interaction cost

Reference:
- submission/competitive-analysis.md

---

# Q4 — “What’s the exit opportunity here?”

## Recommended Answer

The respiratory-AI category already has strong commercial precedent. Pfizer acquired ResApp Health in 2022 for approximately AUD $179M after validating adult cough-diagnostic AI. 

Baby Pulmo is positioned differently:
- pediatric-focused,
- LMIC-focused,
- and integrated into public-health delivery systems.

Potential exit pathways include:
- strategic acquisition,
- NGO/public-health infrastructure partnerships,
- or long-term government deployment contracts.

## Numbers / References

- ResApp acquisition: AUD $179M
- Bangladesh target: 15M under-5 children

References:
- submission/financials.md
- submission/competitive-analysis.md

---

# Q5 — “What are your unit economics?”

## Recommended Answer

Our projected infrastructure cost is approximately $0.003 per interaction because the system uses lightweight audio inference instead of imaging-scale AI. 

The stack is intentionally optimized for low-resource deployment using:
- Modal serverless inference,
- Supabase,
- lightweight Wav2Vec2 audio processing,
- and WhatsApp-native interaction.

The business model is NGO and government deployment contracts rather than charging caregivers directly.

## Numbers / References

- ~$0.003 projected interaction cost
- Early prototype infra target: ~$7/month VPS-equivalent scale

Reference:
- submission/financials.md

---

# Q6 — “How do you handle privacy and consent?”

## Recommended Answer

User recordings are stored de-identified with explicit opt-in consent. 

The system maintains immutable audit logs for BMRC review and operational accountability. We intentionally avoid storing unnecessary personally identifiable information, and all severe-case escalation is handled through authorized healthcare workflows.

Privacy and ethics are treated as core infrastructure requirements, not post-launch additions.

## Numbers / References

- Opt-in consent model
- Immutable audit log
- BMRC ethics review pathway

References:
- submission/summary.md
- submission/accuracy.md

---

# Q7 — “What happens when the AI is wrong?”

## Recommended Answer

The architecture is intentionally designed assuming the model will sometimes be wrong. 

Three safeguards reduce risk:
- confidence gating rejects uncertain inputs,
- deterministic severity rules bias toward escalation,
- and every severe-risk case routes to a real Community Health Worker with the original audio attached.

The system behaves more like a smoke detector than an autonomous doctor — false positives are acceptable, but missed severe pediatric cases are not.

## Numbers / References

- Confidence threshold gating
- Human-in-loop escalation
- CHW review on every severe case

Reference:
- submission/accuracy.md

---

# Q8 — “Why WhatsApp instead of a dedicated app?”

## Recommended Answer

In Bangladesh and similar LMIC environments, WhatsApp dramatically lowers onboarding friction compared with standalone healthcare apps. 

Caregivers already understand voice notes and messaging workflows, while app downloads create:
- storage friction,
- literacy barriers,
- and onboarding drop-off.

WhatsApp-native deployment allows much faster rural adoption and lower caregiver acquisition cost.

## Numbers / References

- Lower caregiver CAC
- No app-install dependency
- Voice-first interaction

References:
- submission/financials.md
- submission/competitive-analysis.md

---

# Q9 — “How do you scale this to 15 million children?”

## Recommended Answer

The scaling model depends on Community Health Worker network multiplication rather than centralized hospital staffing. 

The architecture itself is lightweight and cloud-native, meaning localization mainly requires:
- new language TTS,
- local protocol RAG,
- and CHW integration.

Bangladesh is the initial deployment market, but the same operational model can extend to India, Pakistan, Nigeria, Indonesia, and the Philippines.

## Numbers / References

- Year 3 Bangladesh target: 15M children
- Multi-country LMIC roadmap

Reference:
- submission/financials.md

---

# Q10 — “What happens if Meta changes WhatsApp policies?”

## Recommended Answer

The platform architecture is intentionally channel-agnostic. 

WhatsApp is the fastest adoption path today, but the roadmap already includes:
- Telegram,
- IVR fallback,
- and SMS-based escalation workflows.

The core value is not the messaging platform itself — it is the respiratory-triage and CHW-escalation infrastructure behind it.

## Numbers / References

- WhatsApp primary
- IVR fallback already planned
- Telegram/SMS extensibility in roadmap

References:
- submission/summary.md
- submission/financials.md

---

# Final Coaching Notes

## Most Important Principle

Never oversell the classifier.

Strong framing:
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

# Judge Psychology

Judges are not expecting:
- FDA-grade clinical proof,
- or production-ready deployment.

They are evaluating:
- systems thinking,
- realism,
- ethical awareness,
- scalability,
- and operational understanding.

Honest limitations increase credibility.

---

# Rehearsal Checklist

Before finals:
- rehearse twice minimum,
- keep answers under 30 seconds,
- memorize opening lines,
- avoid technical over-explaining,
- answer directly first, then elaborate only if asked.

Recommended mock audience:
- Ferdous
- Shanta

Goal:
confident, concise, non-defensive delivery under pressure.
