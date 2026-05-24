# THE INFINITY AI BUILDFEST 2026 — Concept Compendium (22 Projects)

Comprehensive deep-dive on all 22 concepts evaluated for the BuildFest. Each entry covers problem (with specific numbers), solution, AI-native architecture, market sizing (TAM/SAM/SOM), and the rationale for its judged-score ceiling on the BuildFest's 100-point rubric (Innovation 20 + Tech 20 + Business 20 + Impact 20 + Scalability 10 + Presentation 10).

**Selected for BuildFest 2026: #10 Baby Pulmo (HealthTech, ceiling 86–96).** See `EXECUTION_PLAN.md` for the execution plan.

## Ranking by combined-criteria score ceiling

| Rank | # | Project | Track | Ceiling |
|---|---|---|---|---|
| 1 | 10 | **Baby Pulmo** ← SELECTED | HealthTech | **86–96** |
| 2 | 11 | JoldhuiAI | E-Commerce | 85–94 |
| 3 | 15 | DariyaShiksha | EdTech | 84–94 |
| 4 | 1 | MaaSathi | HealthTech | 83–93 |
| 5 | 12 | NyayaAI | InfoTech | 83–93 |
| 6 | 16 | ChhayaShield | HealthTech | 83–93 |
| 7 | 8 | KhetMarket | E-Commerce | 82–93 |
| 8 | 17 | NariRokho | InfoTech | 82–92 |
| 9 | 18 | BipodAI | InfoTech | 82–92 |
| 10 | 6 | DoraEye | HealthTech | 81–93 |
| 11 | 5 | ProteenAI | EdTech | 81–92 |
| 12 | 19 | ShunoBhai | HealthTech | 81–91 |
| 13 | 21 | BharosaAI | InfoTech | 81–91 |
| 14 | 13 | AlapAI | HealthTech | 80–92 |
| 15 | 4 | LokKantho | EdTech | 80–90 |
| 16 | 9 | NagorikGPT | InfoTech | 80–90 |
| 17 | 14 | VasaSetu | HealthTech/EdTech | 80–90 |
| 18 | 20 | RaktoDan | HealthTech | 80–90 |
| 19 | 22 | ChakriBondhu | E-Commerce | 80–90 |
| 20 | 2 | Hisaab | E-Commerce | 79–89 |
| 21 | 7 | BangaBrand | MarTech | 76–86 |
| 22 | 3 | SatyaLens | InfoTech | 76–87 |

---

## 1. MaaSathi — Maternal Health AI Companion (HealthTech) — ceiling 83–93

**Problem.** 287,000 women die yearly from preventable pregnancy complications (WHO); 95% in low-resource countries. Bangladesh maternal mortality: 173/100k live births (SDG target: 70). 4M+ pregnancies/year in Bangladesh; most rural women see a skilled provider <4 times. Top killers — postpartum hemorrhage, eclampsia, sepsis — are detectable hours-to-days before crisis.

**Solution.** Bangla voice-first WhatsApp companion. Week-by-week pregnancy tracking, symptom triage against WHO + Bangladesh DGHS guidelines, red-flag escalation to nearest clinic with one-tap call.

**Architecture.** Twilio WhatsApp → Whisper Bangla STT → Claude with structured output (symptoms, gestational week, severity) → Supabase pgvector RAG over WHO PMNCH + DGHS maternal handbook → rules-gated risk classifier (red flags = hard escalation, not LLM discretion) → optional Neo4j symptom→condition graph → Bangla TTS reply + clinic directory + CHW dashboard for human-in-loop.

**Market.** TAM 200M pregnancies/yr global, SAM 60M South Asia + SSA, SOM Bangladesh 4M × $1.50 ARPU (B2G/NGO) = $6M ARR ceiling.

**Why ceiling 83–93:** Highest emotional pitch ("Rashida, 19, rural Bogura"); WHO alignment built in; textbook AI-native architecture (RAG + structured output + rules layer + human-in-loop).

**Risks.** Medical liability disclaimer; Bangla Whisper on rural dialects; clinic directory scope for demo.

---

## 2. Hisaab — Voice Bookkeeping for Micro-Merchants (E-Commerce) — ceiling 79–89

**Problem.** 500M+ underbanked micro-merchants globally (World Bank Findex); 8M+ in Bangladesh. They lose 15–25% margin to lack of inventory/cash-flow visibility. 80%+ functionally illiterate; typing apps fail. Khatabook/Tally require literacy + smartphone + manual entry.

**Solution.** Talk to WhatsApp: "aaj 5 cha bechlam 50 taka kore, dudh kinlam 200 taka." AI parses, updates ledger, returns daily P&L + best-seller chart + tomorrow's stock recommendation as Bangla audio brief.

**Architecture.** WhatsApp voice → Whisper Bangla → Claude function calling → structured JSON {item, qty, unit_price, txn_type, timestamp} → Supabase immutable txn log + materialized P&L views → nightly Claude analytics agent → Prophet time-series forecasting → ElevenLabs Bangla TTS for daily audio brief.

**Market.** TAM 500M global underbanked merchants, SAM 200M South Asia + Africa, SOM Bangladesh 8M × $2/mo @ 5% penetration = $9.6M ARR. Comparable: Khatabook valued ~$600M at 50M users.

**Why ceiling 79–89:** Cleanest investor pitch; clear SaaS monetization; lower emotional weight than HealthTech.

**Risks.** Money trust requires audit log + review flow; Bangla number parsing needs few-shot prompts.

---

## 3. SatyaLens — Misinformation Defense (InfoTech) — ceiling 76–87

**Problem.** 5B+ social media users; 64% encounter misinformation weekly (Reuters Digital News Report 2024). Bangladesh post-Jan 2026 elections has documented Bangla political deepfakes. 96% of deepfake detectors are English-only and trained on Western faces — fail on South Asian content. A Bangla deepfake can virally reach 10M WhatsApp households in 48 hours.

**Solution.** WhatsApp bot (forward suspicious media → 10-sec trust score) + Chrome extension (right-click to verify). Returns deepfake probability + source credibility + cross-referenced facts + plain-Bangla "why."

**Architecture.** HuggingFace deepfake detector fine-tuned on South Asian faces (e.g., `dima806/deepfake_vs_real_image_detection`) + TinEye reverse image + C2PA provenance + RAG over Rumor Scanner BD / Boom / AFP fact-checks + Neo4j entities↔claims↔sources↔verifications graph + Claude reasoning with citations.

**Market.** TAM 5B social users; SAM 600M Bangla+Hindi+Urdu underserved; SOM B2B fact-checkers + Meta/X content moderation + Election Commission = $5–20M ARR potential.

**Why ceiling 76–87:** Tech risk in 48h is highest (deepfake accuracy for South Asian faces caps ~88%); politically loaded — needs strong transparency narrative.

**Risks.** Deepfake model accuracy ceiling; fact-check DB requires scraping with permission.

---

## 4. LokKantho — Voice AI Tutor on Feature Phones (EdTech) — ceiling 80–90

**Problem.** 1.6B students globally; 600M+ have no smartphone access. Bangladesh: 65M students, 12M+ on feature phones / shared devices. Rural women are the most under-educated demographic. UNESCO: 70% of 10-year-olds in Bangladesh can't read simple text.

**Solution.** Phone any number → IVR picks up → AI tutor speaks Bangla → student talks back. Adaptive: 3 diagnostic questions to find learner's level, then 5-min conversational lesson, then spaced-repetition follow-up call next day. Works on any phone ever made.

**Architecture.** Twilio Voice IVR → Whisper Bangla STT → Supabase learner profile + mastery tracking → pgvector RAG over NCTB Class 1–10 curriculum → Claude generates 5-min conversational lesson script → Google or Coqui Bangla TTS → Half-Life Regression spaced repetition → optional multi-agent (assessor + teacher + motivator).

**Market.** TAM 1.6B students global; SAM 300M feature-phone-first in South Asia + Africa; SOM B2G (Ministry of Education) + NGO (BRAC, Save the Children) + telco bundling = $10M+ ARR with one government contract.

**Why ceiling 80–90:** Inclusivity framing wins; "call this number live during the pitch" demo is unforgettable.

**Risks.** Twilio voice latency; Bangla TTS naturalness uneven; ~$20 Twilio credit for 48h demo.

---

## 5. ProteenAI — Reskilling AI for Garment Workers (EdTech) — ceiling 81–92

**Problem.** 75M garment workers globally; 4M+ in Bangladesh (RMG = 84% of national exports). 80%+ are women, 60%+ functionally illiterate. McKinsey: automation will displace 30–50% of garment jobs by 2035. Zero scalable reskilling pipeline; one closed factory = 2,000 unemployed women.

**Solution.** Voice-first Bangla AI coach delivering 10-min daily reskilling micro-lessons via WhatsApp during the bus commute. Adaptive: assesses current skills, then teaches adjacent higher-value skills (quality inspection, supervisor English, basic merchandising). Verifiable micro-credentials.

**Architecture.** WhatsApp Business API (shift-aware scheduling) → Neo4j skill graph (current → adjacent → demand signals from BGMEA/LinkedIn) → adaptive Claude lesson engine → Supabase pgvector RAG over BGMEA + ILO frameworks + RMG quality standards → voice assessment via Whisper + LLM grading → auto-generated certificate + LinkedIn badge → factory HR dashboard.

**Market.** TAM 75M garment + 100M similar low-skill workers; SAM 30M South/SE Asia; SOM Bangladesh 4M × $0.50/mo B2B factory subsidy = $24M ARR ceiling; B2G partnerships (SEIP, Skills for Employment) add 10x.

**Why ceiling 81–92:** Three monetization paths (B2B + B2G + B2B2C); gender impact + automation displacement + Bangladesh export economy = trifecta.

**Risks.** Worker data costs (partner with Grameenphone for zero-rated WhatsApp); factory cooperation needed for credentialing.

---

## 6. DoraEye — Phone-Camera Diabetic Retinopathy Screening (HealthTech) — ceiling 81–93

**Problem.** 537M adults have diabetes globally (IDF 2021); projected 783M by 2045. ~30% develop diabetic retinopathy → leading cause of preventable blindness in working-age adults. 90%+ preventable with early screening. Bangladesh has <100 retina specialists for 13M diabetics; 1 ophthalmologist per ~50,000 people; rural districts: 0. Current screening requires $20,000 fundus camera + specialist.

**Solution.** Smartphone-based screening. Community health worker uses a $5 clip-on 20D lens (or $30 D-EYE adapter) on any Android phone to capture retina images. AI classifies risk in 10 seconds. Red cases auto-referred to nearest ophthalmologist with image attached. Patient gets Bangla audio explanation + appointment.

**Architecture.** Android app + clip-on lens → on-device CNN image quality gate (rejects blurry images) → EyePACS-pretrained ResNet50 fine-tuned on IDRiD (public Indian retinal dataset) → Mild/Moderate/Severe/Proliferative classification + Grad-CAM heatmap → RAG over AAO guidelines + Bangla patient education → Claude generates Bangla audio explanation → GraphDB of ophthalmologists by district → auto-book via SMS → Supabase HIPAA-style audit → human-in-loop ophthalmologist review for severe cases.

**Market.** TAM 537M diabetics ($80B vision care); SAM 200M without specialist access; SOM Bangladesh 13M × $2/screening × 2/year = $52M; B2G + insurer + clinic SaaS.

**Why ceiling 81–93:** "Phone + $5 lens = $20k machine" is investor catnip; CV + explainability + image quality gating = strongest tech of any concept.

**Risks.** Medical device regulatory classification; pretrained DR sensitivity ceiling 88–92%; demo requires IDRiD public images; lens hardware adds friction.

---

## 7. BangaBrand — Multilingual AI Brand Voice for SMEs (MarTech) — ceiling 76–86

**Problem.** 400M+ SMEs globally; ~10M in Bangladesh, ~70M in South Asia. SMEs run social/WhatsApp in 3+ languages (Bangla, English, Hindi) and fail at all of them. Jasper/Copy.ai are English-first; Bangla output is broken. Customers expect Instagram-quality posts + WhatsApp catalog replies + Facebook ads — beyond a 5-person shop's bandwidth.

**Solution.** Bangla-native brand intelligence platform. 5-min voice onboarding → AI builds "brand DNA" (voice, palette, do/don't). Then daily: generates social posts (text + image + 5-sec video) in 3 languages, drafts WhatsApp customer replies from product catalog (RAG), creates ad creative with performance feedback loop.

**Architecture.** Onboarding voice agent → Supabase brand DNA store → Claude (text with brand DNA in system prompt) + Vercel AI Gateway → Imagen/DALL-E images + Replicate Hunyuan/Wan2.2 for short video → pgvector catalog RAG → Meta Marketing API engagement metrics → RL feedback loop on creative variants → Vercel Next.js dashboard + WhatsApp Business integration.

**Market.** TAM 400M SMEs ($200B MarTech spend); SAM 70M South Asia; SOM Bangladesh 10M × $5/mo @ 3% = $18M ARR; comparable to Plivo, Wati.

**Why ceiling 76–86:** Best pure SaaS monetization; crowded MarTech space caps the ceiling; impact is economic but less emotional.

**Risks.** Image gen API costs scale; RL feedback loop is the hardest part — for submission, show architecture + 1 manual iteration.

---

## 8. KhetMarket — Voice-First Farmer-to-Buyer Marketplace (E-Commerce) — ceiling 82–93

**Problem.** 500M smallholder farmers globally; 87% in Asia + Africa; produce 1/3 of world's food. Middlemen (forias/aratdars in Bangladesh) take 50–70% of margin. Bangladesh: 15M farming households, average <1 acre, rural literacy ~60%. DeHaat/Ninjacart reach <2% of smallholders. Farmers lose 30–40% of produce to spoilage + bad market timing.

**Solution.** Voice-first WhatsApp marketplace. Farmer sends voice + photo of produce. AI parses listing, grades visually, matches verified buyers, negotiates price in Bangla, coordinates logistics, escrows payment via bKash/Nagad.

**Architecture.** WhatsApp voice + photo → Whisper Bangla → Claude function calling → structured listing {crop, qty, unit, freshness, location, asking_price} → YOLO/ResNet vision grading (public rice/mango/potato datasets) → Supabase pgvector buyer requirement matching → RAG over BMDA wholesale price feeds → AI pricing/negotiation agent → GraphDB of transporters by route → bKash escrow API → trust/fraud detection layer.

**Market.** TAM 500M smallholders + $1T smallholder produce GMV; SAM 200M South Asia smallholders, $300B GMV; SOM Bangladesh 15M households × $30/yr commission @ 1% take-rate = $50M GMV. Comparable: AgUnity / DeHaat valued $300M+.

**Why ceiling 82–93:** Most balanced across all 6 rubric dimensions; clearest GMV story; multimodal AI (voice + vision + negotiation) hits tech depth max.

**Risks.** Escrow + trust requires payment partner; buyer-side acquisition harder than farmer-side; politically sensitive vs middlemen — frame as augmenting.

---

## 9. NagorikGPT — Bangla AI Public Service Navigator (InfoTech) — ceiling 80–90

**Problem.** Bangladesh has 8,000+ public services across 180+ ministries; 70%+ of citizens have been bribed by intermediaries ("dalal culture") for routine services. ~85M Bangladeshis eligible for social safety nets miss out due to information barriers. services.gov.bd has poor UX, English-heavy. Same crisis in India, Indonesia, Nigeria, Philippines.

**Solution.** Bangla WhatsApp civic AI copilot. Voice question → exact eligibility, all required documents, fees, nearest service center, processing time, your rights if denied. RAG over verified .gov.bd content. Flags + corrects common misinformation. Drafts RTI letters in legal Bangla.

**Architecture.** Whisper Bangla → intent router → pgvector RAG over services.gov.bd + ekpay.gov.bd + MyGov + ministry websites (daily crawl) → Neo4j graph of services ↔ eligibility ↔ documents ↔ fees ↔ legal references → citation engine (every answer cites .gov.bd source) → misinformation cross-checker → RTI legal-Bangla drafter → GraphDB of UDC/DC/Upazila offices → optional complaint routing.

**Market.** TAM 2B+ citizens in service-complex countries (Bangladesh 170M + India 1.4B + Indonesia 280M + Nigeria 220M + Philippines 110M); SAM 500M Bangla + Hindi speakers; SOM Bangladesh 170M B2C free + ICT Division B2G ($500K–$5M) + insurance/loan referral fees.

**Why ceiling 80–90:** Anti-corruption + civic empowerment + 85M missing social safety net = welfare narrative; GraphDB + RAG + citation = strong InfoTech track fit.

**Risks.** Data freshness from daily crawl; political sensitivity around "dalal" critique — frame as empowerment, not accusation.

---

## 10. Baby Pulmo — AI Pediatric Cough/Cry Voice Diagnostic (HealthTech) — ceiling 86–96 ⭐ SELECTED

**Problem.** Pneumonia kills 740,000 children under 5 globally per year — the #1 killer of young children. Bangladesh: ~25,000 child deaths/year from acute respiratory infections; 63% of Bangladeshi children with pneumonia are NOT taken to a qualified provider (BDHS 2022). Detection requires stethoscope + trained doctor; rural Bangladesh has ~1 doctor per 8,000 people. Time-to-care averages 36+ hours from symptom onset.

**Published science:** Sharan et al. JAMA Pediatrics 2018: cough audio classifies pediatric pneumonia at 84% sensitivity, 81% specificity. Porter et al. Nature Scientific Reports 2019: 81–95% accuracy for asthma, croup, pertussis. ResApp Health acquired by Pfizer in 2022 for AUD $179M (USD ~$120M).

**Solution.** Mother holds phone near baby's mouth during a cough → AI classifies in 10 seconds → Bangla audio explanation + risk level + action plan. Severe cases auto-route to nearest CHW/clinic with audio attached. Longitudinal tracking over days catches deterioration.

**Architecture.** Phone mic (WhatsApp + IVR fallback) → noise filtering + cough segmentation + quality gate → Wav2Vec2-XLSR fine-tuned on Coswara + COUGHVID public datasets → CNN classifier head (Pneumonia / Bronchiolitis / Asthma / Croup / Pertussis / Normal) with confidence + Grad-CAM spectrogram heatmap explainability → Supabase pgvector RAG over WHO IMCI + Bangladesh DGHS pediatric protocols → rules-gated severity (NOT pure LLM): IF confidence > 0.7 AND class IN (pneumonia, severe) THEN mandatory_escalate → Claude generates Bangla audio guidance grounded in retrieved protocols → Neo4j GraphDB-routed CHW alert with audio + GPS → immutable audit log.

**Market.** TAM 730M U5 children + 130M births/yr globally; pediatric care market $80B (Grand View Research 2023); SAM 250M U5 in South Asia + SSA; SOM Bangladesh 15M U5 × $5/yr B2G/NGO = $75M ARR ceiling.

**Monetization paths.** (1) B2G — DGHS / National IMCI program licensing; Bangladesh National Pneumonia Programme has $30M+ annual budget. (2) B2NGO — UNICEF / Save the Children / BRAC ($1–3/beneficiary/yr). (3) B2B Hospitals + insurance — Square/United/Apollo/Evercare pediatric pre-triage. (4) B2B Telco — Grameenphone/Robi value-added service. (5) B2C freemium — premium tier for diaspora-paying-for-parents-in-Bangladesh.

**Why ceiling 86–96:** Highest combined-criteria ceiling of all 22. Audio AI is published science (not LLM wrapper); language-agnostic so global scale is built in (same model, new TTS = new country); saves children's lives = max emotional + measurable impact; demoable end-to-end in 60 seconds; responsible-AI built into architecture (rules-gated, human-in-loop, Grad-CAM, WHO IMCI alignment); Pfizer/ResApp $120M acquisition validates commercial category.

**Risks.** Coswara is adult data → frame honestly + pediatric fine-tune in Phase 1. Medical device regulatory → "decision support / screening assistive tool" framing + ResApp/Pfizer precedent. Bangla Whisper rural-dialect accuracy mid → ElevenLabs Bangla TTS fallback + script-narrated demo backup. Solo team → recruit one NRB advisor (Bangladeshi-American pediatrician or ML researcher) via LinkedIn outreach by hour 36.

---

## 11. JoldhuiAI — Climate-Resilient Smallholder Farming Advisor (E-Commerce) — ceiling 85–94

**Problem.** Climate change is destroying smallholder agriculture: 80M Bangladeshis in coastal/floodplain zones face increased salinity, flooding, cyclones. Bangladesh loses ~$3B/year to climate-related ag damages. Globally: 500M smallholder farmers face $200B+/year climate adaptation costs. Bangladesh DAE reaches <15% of farmers; hyperlocal data fragmented across BMD, BARI, SoilGrids, Sentinel-2.

**Solution.** Bangla WhatsApp advisor fusing satellite imagery + hyperlocal climate forecasts + soil data + farmer's plot location. Tells farmer: what to plant this season, when to harvest, when to delay sowing for cyclone risk, salt-tolerant variety recommendations, water management. Emergency alerts ("storm in 36hrs, harvest now").

**Architecture.** Sentinel-2 satellite imagery (free, NDVI + soil moisture) + BMD hyperlocal forecasts + SoilGrids global soil data + BMDA price feeds → per-plot learner profile → Claude + RAG over BARI/DAE crop manuals → personalized seasonal recommendations → nightly cron checks forecasts vs farmer's crop calendar → emergency Bangla voice alerts → Green Delta / Bima Mobile parametric insurance API → optional KhetMarket handoff for produce sales.

**Market.** TAM 500M smallholders + $200B/yr climate adaptation; SAM 200M South Asia + SSA climate-affected; SOM Bangladesh 15M farming households + B2G (DAE digitization) + insurance partnerships = $30M ARR potential.

**Why ceiling 85–94:** Climate is the biggest global narrative right now; UN SDG 2 (zero hunger) + 13 (climate action) alignment; technically rich (satellite + ML forecasting + RAG + insurance integration); massive impact.

**Risks.** Real Sentinel-2 pipeline takes time — for demo, snapshot one district. Insurance integration is a roadmap claim.

---

## 12. NyayaAI — AI Legal Copilot for the Poor (InfoTech) — ceiling 83–93

**Problem.** 5B people lack meaningful access to justice (UN, 2019). Bangladesh: 3.7M pending court cases, ~75% backlog; Legal Aid Services Trust serves <10% of those needing aid. Rural complainants don't know their rights, can't draft legal Bangla documents, and get exploited by paid intermediaries. Same crisis in India (50M+ pending), Indonesia, Nigeria, Pakistan.

**Solution.** Bangla WhatsApp AI legal copilot. Citizen describes problem in voice → AI (1) identifies applicable law, (2) explains rights in plain Bangla, (3) drafts complaint/RTI/legal notice in formal legal Bangla, (4) matches to free legal aid lawyer, (5) preps for court appearance. Focus areas: dowry/domestic violence, wage theft, land disputes, consumer rights, tenant rights.

**Architecture.** Whisper Bangla → domain classifier (criminal/civil/family/labor/land) → pgvector RAG over Bangladesh Penal Code + CrPC + Domestic Violence Prevention Act + Dowry Prohibition Act + Labour Act (all public domain) → citation-grounded answers → Claude templated legal Bangla document generation → GraphDB of lawyers by district + specialty + free/paid → match → strong agentic refusal for risky specific advice; escalates serious cases to human lawyers.

**Market.** TAM 5B unmet justice; SAM 700M South Asia + Indonesia + Nigeria; SOM Bangladesh 50M income-eligible + Law Ministry / Legal Aid Trust B2G contract = $1–5M ARR realistic.

**Why ceiling 83–93:** Anti-corruption + civic empowerment + UN SDG 16; RAG + GraphDB + agentic refusal = strong AI-native InfoTech architecture.

**Risks.** Legal advice liability — strong disclaimers + human-lawyer-in-loop framing.

---

## 13. AlapAI — Voice AI Speech Therapy for Stroke + Aphasia (HealthTech) — ceiling 80–92

**Problem.** 12.2M strokes/year globally; 80% in low/middle-income countries; ~30% develop aphasia (speech loss). Speech therapy access: Bangladesh has <100 trained Speech-Language Therapists for 170M people. WHO recommends 2–3 therapy sessions/week; Bangladesh patients average <2/year. Also affects 80M children with speech disorders globally.

**Solution.** AI speech therapist on a phone. Daily 15-minute Bangla sessions: AI prompts words → patient speaks → AI scores pronunciation, fluency, repetition → adapts difficulty → tracks recovery week-over-week. Gamified for kids; clinical-grade for adults. Caregiver dashboard. Plateaus auto-escalate to human SLT.

**Architecture.** Whisper-large fine-tuned for disordered Bangla speech → Montreal Forced Aligner for phoneme-level scoring → pgvector RAG over NIDCD + ASHA aphasia rehabilitation protocols → adaptive difficulty engine → Claude generates Bangla coaching ("aro slow bolun") → ML recovery trajectory predictor → Supabase backend.

**Market.** TAM 50M stroke survivors + 80M children with speech disorders = 130M; SAM 60M without SLT access; SOM Bangladesh 6M × $5/mo = $30M ARR potential.

**Why ceiling 80–92:** High impact, novel tech (disordered-speech STT is genuinely hard); longitudinal demo (less dramatic in 3 min than acute-care concepts).

**Risks.** Disordered-speech STT — be honest, show synthetic-to-disordered fine-tuning path.

---

## 14. VasaSetu — AI Bridge for Bangla Sign Language (HealthTech / EdTech) — ceiling 80–90

**Problem.** 70M+ deaf people globally use sign language; nearly all sign language AI is American Sign Language. Bangladesh: ~3M deaf people, <500 trained sign interpreters. Bangladeshi deaf children locked out of education because Bangla Sign Language (BdSL) not formally taught. Same gap in 80% of world's sign languages.

**Solution.** Two-way translation: (1) Camera captures BdSL signing → spoken Bangla output (deaf-to-hearing). (2) Spoken Bangla → animated 3D avatar performing BdSL (hearing-to-deaf). Use cases: doctor visits, classrooms, customer service.

**Architecture.** MediaPipe Hands + Body Pose → time-series pose vectors → Transformer trained on CDC-BdSL public dataset → Bangla text → TTS. Reverse: Bangla speech → text → Unity 3D avatar with custom BdSL rig. Community correction loop grows dataset. Vercel + Supabase + Modal/Replicate GPU inference.

**Market.** TAM 70M deaf globally; SAM 30M in non-English sign language regions; SOM Bangladesh 3M + global diaspora; B2B (schools, hospitals, govt) + B2C subscription.

**Why ceiling 80–90:** Very strong impact, novel tech, near-zero competition for non-English sign languages; BdSL dataset scarcity is the ceiling cap.

**Risks.** Public BdSL data limited — for demo, support 50–100 most common signs.

---

## 15. DariyaShiksha — Refugee + Migrant Children Education AI (EdTech) — ceiling 84–94

**Problem.** 100M+ forcibly displaced people globally (UNHCR 2025); 26M refugees. Bangladesh hosts 950,000+ Rohingya refugees in Cox's Bazar — generation of children growing up with zero formal education. Refugee children 5x more likely to be out of school. Under-served languages: Rohingya, Burmese, Arabic, Pashto, Dari, Tigrinya.

**Solution.** Mobile-first AI tutor in displaced people's mother tongue. Adapts UNHCR Accelerated Education Programme curriculum. Voice + image-first for low literacy. Generates printable worksheets for offline use. Trauma-informed psychosocial support modules. Caregiver-led mode.

**Architecture.** Whisper + Meta's NLLB (No Language Left Behind) for under-represented languages → adaptive mastery engine → pgvector RAG over UNHCR AEP curriculum + Open Educational Resources → Claude generates conversational lessons in target language → separate trauma-informed fine-tuned model recognizes distress cues → offline worksheet PDF generator → community network for same-age learners.

**Market.** TAM 100M displaced + 200M migrant children; SAM 30M in mobile-accessible refugee camps; SOM UNHCR + UNICEF + INGO licensing = $5–20M ARR potential.

**Why ceiling 84–94:** UN-aligned, impossible to argue impact, politically powerful narrative; Bangladesh Rohingya context makes it locally relevant.

**Risks.** Rohingya NLP support in NLLB is thin — demo Burmese + Bangla; community fine-tune Rohingya in roadmap.

---

## 16. ChhayaShield — Mental Health AI Companion (HealthTech) — ceiling 83–93

**Problem.** 1B+ people with mental disorders globally; 70% in low/middle-income countries with no access to care. Bangladesh: 16% adults with anxiety/depression (~25M people), <5% access care; stigma severe. WHO Mental Health Atlas: Bangladesh has 1 psychiatrist per 700,000 people. Suicide rate rising; youth post-pandemic distress.

**Solution.** Voice-first Bangla WhatsApp/phone mental health companion. Evidence-based CBT exercises, mood journaling via voice, daily check-ins, breathing exercises, crisis escalation to Kaan Pete Roi helpline. Non-judgmental, anonymous. Trained to detect suicidal ideation → mandatory human escalation.

**Architecture.** WhatsApp voice + Whisper Bangla → emotion classifier + crisis detector (safety-critical, rules-gated) → Claude with CBT protocol + Bangla cultural context → pgvector RAG over WHO mhGAP + Bangladesh National Mental Health Programme → safety layer: if crisis detected, mandatory handoff to Kaan Pete Roi → mood tracking over weeks → caregiver dashboard with consent.

**Market.** TAM 1B+ globally; SAM 400M South Asia + SSA; SOM Bangladesh 25M × $2/mo = $50M ARR potential.

**Why ceiling 83–93:** Massive scale; "save lives" framing; stigma-busting low-cost AI fits a literal global health priority.

**Risks.** Suicide liability — strong escalation layer required; emotion classification accuracy.

---

## 17. NariRokho — Women's Safety + Anti-Harassment AI (InfoTech) — ceiling 82–92

**Problem.** 1 in 3 women globally experience physical/sexual violence (WHO). Bangladesh: 87% of women report sexual harassment ("Eve-teasing"); 73% experienced domestic violence. Most cases unreported due to stigma + ineffective police response.

**Solution.** Bangla voice silent activation on WhatsApp ("ami bipode" = "I'm in danger") triggers: (1) silent SOS with GPS to pre-set guardians + 999, (2) auto-recording for evidence, (3) AI guides through next steps in safe voice, (4) connects to legal aid, women's shelters, medical care. Preventive: route safety prediction, "share my journey" mode.

**Architecture.** On-device voice keyword spotting (low-power) → silent activation → encrypted GPS + audio capture to Supabase → GraphDB of guardians + 999 + Acid Survivors Foundation + women's shelters → Claude legal-aid agent in Bangla → automatic case file creation with timestamped evidence → optional bKash safe-escape fund integration.

**Market.** TAM 4B women; SAM 1.5B in high-harassment regions; SOM Bangladesh 80M women × $0.50/mo + B2G (Ministry of Women) + B2B (corporate women safety) = $40M+ ARR.

**Why ceiling 82–92:** Emotional pitch is brutal in best way; SDG 5 alignment; clear demo (live activation).

**Risks.** False positive activation; misuse for stalking by abusers — design carefully.

---

## 18. BipodAI — Disaster Response AI for Floods/Cyclones (InfoTech) — ceiling 82–92

**Problem.** 200M+ people affected by climate disasters annually. Bangladesh: cyclones + floods affect 30M+ people every year; 2023 Cyclone Mocha displaced 2.3M. Existing disaster response is slow, fragmented, English-heavy. Family reunification post-disaster takes weeks. Shelter capacity unknown.

**Solution.** WhatsApp + IVR disaster command in Bangla. Pre-disaster: hyperlocal alerts in your dialect 48h ahead, optimal evacuation route to nearest shelter with capacity. During: live updates, missing-person registry, shelter coordination. Post: family reunification matching, government compensation claim auto-filing.

**Architecture.** Bangladesh Meteorological Dept + IMD + GLOFAS flood forecasting → per-village risk classifier (ML) → Bangla voice alerts via Twilio Voice + WhatsApp → GraphDB of shelters with real-time capacity + evacuation routes → image-recognition based missing person matching from family submissions → Cyclone Preparedness Programme volunteer integration.

**Market.** TAM 200M disaster-affected globally; SAM 80M South/SE Asia annual; SOM Bangladesh Disaster Management Bureau + UN OCHA + Red Crescent licensing = $5–20M ARR.

**Why ceiling 82–92:** SDG 13 (climate action) + 11 (resilient cities); time-critical AI saves lives; Bangladesh is the world's most disaster-experienced country.

**Risks.** Government data access; field validation; mobile network during disaster (need IVR fallback).

---

## 19. ShunoBhai — Accessibility AI for Blind & Low Vision (HealthTech) — ceiling 81–91

**Problem.** 1.3B people globally have vision impairment; 43M completely blind. Bangladesh: 750k blind, near-zero accessibility tools in Bangla. Existing tools (Seeing AI, Be My Eyes) are English-only. Blind people in non-English regions are invisible in product design.

**Solution.** Phone camera → AI describes world in Bangla audio. Use cases: read signs/menus, recognize money (BD Taka denominations), identify food/objects, recognize faces (with consent), navigate unfamiliar places. Voice-first; works hands-free via earpiece.

**Architecture.** Phone camera stream → GPT-4V or Gemini Vision multimodal → Claude generates contextual Bangla description tuned to user preference (terse vs detailed) → ElevenLabs Bangla TTS → optional on-device YOLO for currency/face recognition (faster) → user profile learns preferences over time.

**Market.** TAM 1.3B vision-impaired; SAM 600M in non-English regions; SOM Bangladesh 750k blind + 5M low-vision; B2C subscription + B2G (Department of Social Services) + B2B insurance = $5–15M ARR.

**Why ceiling 81–91:** SDG 10 (reduced inequality); multimodal AI showcase; disability inclusion framing.

**Risks.** Multimodal API costs; on-device model size; cellular data limits in rural Bangladesh.

---

## 20. RaktoDan — AI Blood Donation Network (HealthTech) — ceiling 80–90

**Problem.** 117M units of blood needed globally yearly; 60% of countries have shortages. Bangladesh: 5,000+ thalassemia deaths/year partly from blood shortage; 1M+ blood units short annually. Current system: WhatsApp groups + Quantum Foundation calls. Slow, manual, often too late for trauma cases.

**Solution.** WhatsApp + IVR AI matchmaker. Patient/hospital posts urgent need (blood type, location, urgency). AI: (1) ranks nearest eligible donors by blood type + last donation date + availability, (2) sends staggered alerts (closest first, expanding radius), (3) provides Bangla coaching to the donor, (4) confirms donation, (5) gamifies repeat donation. Thalassemia patient chronic scheduling.

**Architecture.** Supabase donor registry + pgvector for similarity matching → GraphDB of donors ↔ blood types ↔ hospital locations ↔ urgency ladders → real-time geo-matching engine → Twilio voice + WhatsApp → Claude Bangla SMS coaching → optional blockchain donation history → loyalty + gamification engine.

**Market.** TAM 117M units/yr globally; SAM 30M South Asia; SOM Bangladesh + hospital licensing $1–5M ARR + B2G (DGHS National Blood Programme).

**Why ceiling 80–90:** Tangible life-saving; demo is dramatic (real-time matching simulation); SDG 3.

**Risks.** Donor privacy + safety; verification fraud; thalassemia community partnership needed.

---

## 21. BharosaAI — Migrant Worker Rights AI (InfoTech) — ceiling 81–91

**Problem.** 13M Bangladeshi migrant workers abroad (Middle East, Malaysia, Singapore); they remit $24B/year (8% of Bangladesh GDP). Exploitation crisis: passport confiscation, wage theft, kafala-system abuse, no return ticket, deaths in custody. 281M international migrants globally face similar issues.

**Solution.** Bangla WhatsApp AI: workers report issues → AI files complaint with BD embassy/consulate, collects timestamped evidence, connects to BRAC Migration / WARBE / Akota NGOs, drafts legal complaints to host-country labor courts, helps prep deposition. Pre-departure: contract review (AI flags abusive clauses), legitimate-recruiter verification.

**Architecture.** WhatsApp Bangla → Whisper → entity extraction (employer name, country, issue type) → pgvector RAG over Bangladesh Expatriates' Welfare Act + ILO conventions + destination-country labor laws → GraphDB of BD consulates + migrant NGOs + legal aid → Claude drafts formal complaints in Bangla + Arabic/English → evidence chain-of-custody (immutable Supabase log + cryptographic timestamp) → optional escalation to MoEWOE.

**Market.** TAM 281M international migrants; SAM 50M from South/SE Asia; SOM 13M Bangladeshis + diaspora = $10M+ ARR + government contract potential.

**Why ceiling 81–91:** $24B remittance protection narrative; ethical labor + global compliance; SDG 8 (decent work).

**Risks.** Cross-border legal complexity; consulate cooperation needed; worker phone access in host countries.

---

## 22. ChakriBondhu — AI Job Matcher for Informal Workers (E-Commerce) — ceiling 80–90

**Problem.** 500M+ informal/low-skill workers globally. Bangladesh: 85% of workforce informal (~52M people); daily wage uncertainty, no contracts, no benefits. Workers spend 1–3 hours daily looking for work; employers struggle to find reliable workers. Bdjobs/LinkedIn target white-collar only.

**Solution.** WhatsApp Bangla voice: "ami rajmistri, dhaka, kalker kaaj ache?" (I'm a mason, Dhaka, work for tomorrow?) → AI matches employers by location + skill + rating + wage. Wage transparency (average market rate), dispute resolution, mobile money payment escrow, reputation system.

**Architecture.** WhatsApp Bangla → Whisper → Claude extracts {skill, location, availability, expected_wage} → Supabase pgvector match against job postings → GraphDB of workers ↔ skills ↔ employers ↔ ratings ↔ payment history → BMET (Bureau of Manpower) cross-reference for skill verification → bKash/Nagad escrow → reputation accrual.

**Market.** TAM 500M informal workers globally; SAM 200M South Asia; SOM Bangladesh 52M × $0.50/mo + employer subscription + transaction fees = $30M+ ARR.

**Why ceiling 80–90:** Formalizes the informal economy; SDG 8; clear monetization (multi-sided marketplace).

**Risks.** Trust at both ends; dispute resolution complex; fraud risk.
