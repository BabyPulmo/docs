# Baby Pulmo — First-Prize Strategy for BuildFest 2026

> Team-facing execution plan. Open this file daily. Each role section is paste-ready for stand-up. Update statuses as tasks land.

**Goal:** Win first prize at THE INFINITY AI BUILDFEST 2026 (BDT 50,000 + global exposure).
**Today:** 2026-05-25
**Preliminary deadline:** 2026-05-30, 11:59 PM GMT+6 (Top 200 advance)
**Finals:** 2026-06-12, Dhaka (first prize decided here)

---

## 🎯 Quick issue queues — bookmark yours

> Every task in this plan is a GitHub issue. Click yours; work it; close it.

- **Master board** (pinned in babypulmo): https://github.com/BabyPulmo/babypulmo/issues/22
- **Ferdous (Lead + Deploy):**
  - Code: https://github.com/BabyPulmo/babypulmo/issues?q=is%3Aopen+label%3Aowner%3Aferdous
  - Strategy: https://github.com/BabyPulmo/discussion/issues?q=is%3Aopen+label%3Aowner%3Aferdous
  - CLI: `gh issue list -R BabyPulmo/babypulmo -l owner:ferdous`
- **Faiyad (Backend, NRB):** https://github.com/BabyPulmo/babypulmo/issues?q=is%3Aopen+label%3Aowner%3Afaiyad
  - CLI: `gh issue list -R BabyPulmo/babypulmo -l owner:faiyad`
- **Shanta (UI + Presentation):** https://github.com/BabyPulmo/babypulmo/issues?q=is%3Aopen+label%3Aowner%3Ashanta
  - CLI: `gh issue list -R BabyPulmo/babypulmo -l owner:shanta`
- **Abdullah (Business + Data):** https://github.com/BabyPulmo/discussion/issues?q=is%3Aopen+label%3Aowner%3Aabdullah
  - CLI: `gh issue list -R BabyPulmo/discussion -l owner:abdullah`

**Phase filters:**
- Phase 1 only: append `+milestone:%22Phase+1%3A+Preliminary+%282026-05-30%29%22` to any link
- Phase 2 only: `+milestone:%22Phase+2%3A+Finals+%282026-06-12%29%22`

---

## Team

| Member | Role | Country | Mode | Owns |
|---|---|---|---|---|
| **Engr Md Ferdous Alam** | Leader / Coordinator + **Deployment Lead** | 🇧🇩 | Physical | VPS + Docker + DNS, finals pitch, form submission, all infra credentials |
| **Faiyad Irfan Hares** | Backend / Database / Scraper Engineer | 🇨🇦 NRB | Virtual | Wav2Vec2 training (Colab), IMCI scrape+chunk+embed, Meta WA backend code, webhook/API code |
| **Shanta Khatun** | UI/UX / Frontend + Presentation Lead | 🇧🇩 F | Physical | YouTube video, `/docs` page, landing+CHW polish, investor deck |
| **Abdullah Al Masum** | Business Analyst / Data Scientist | 🇧🇩 | Physical | Pilot LOIs, financial model, Coswara dataset analysis, hostile-Q&A prep |
| *(5th open)* | Clinical Advisor — target: **Dr. Al Muktafi Saadi** | 🇧🇩 | TBD | Bangla script review; lifts ethics rubric +5pts and adds 5th team slot +1pt |

**Pre-judgment team eligibility: +6 pts** (4 members +4, NRB +1, female +1). Adding Dr. Saadi as 5th member: +1 more.

**Deployment policy:** All VPS/Docker/DNS/env work is Ferdous-only. Faiyad ships PRs against `BabyPulmo/babypulmo`; Ferdous deploys.

---

## Score targets — two systems, two deadlines

| Phase | Deadline | Filter | Decided by |
|---|---|---|---|
| **Preliminary** | 2026-05-30 11:59pm GMT+6 | Top 200 advance | **Internal 153-pt form score** |
| **Finals** | 2026-06-12 Dhaka | First prize | **Official 100-pt rubric** (Innovation 20 / Tech 20 / Business 20 / Impact 20 / Scalability+NRB 10 / Presentation 10) |

| Metric | Today | Phase 1 target | Phase 2 target |
|---|---|---|---|
| Form score (/153) | 79 (52%) | 130–138 (85–90%) | n/a |
| Rubric score (/100) | ~58–65 | ~70 | **85–90 (first-prize range)** |

---

## PHASE 1 — Survive Preliminary Cut (5 days)

Total effort: ~30 person-hours.

### Ferdous (~14h) — Lead + Deploy

- [ ] **Day 1** Send Dr. Saadi outreach (paste from `outreach/dr-saadi-email.md`). LinkedIn DM first; email when address found.
- [x] **Day 1** Commit + push Docker stack files (`babypulmo/deploy/`).
- [x] **Day 1** VPS confirmed: Contabo `vmi2956989`, Ubuntu 24.04.3, Docker 29.1.3, nginx 1.24, certbot 2.9. IPv4 `86.48.31.193`, IPv6 `2605:a142:2295:6989::1`. Other apps (api/cal/pgadmin.fintant.ai) coexist — port 3000 owned by `fintant-backend`, so babypulmo web binds to **127.0.0.1:3010**.
- [ ] **Day 1–2** Set DNS records per `babypulmo/deploy/DNS-RECORDS.md` (A + AAAA for `@` and `www`). Verify with `dig babypulmo.com +short`.
- [ ] **Day 2** Clone `BabyPulmo/babypulmo` to `/opt/babypulmo`; fill `.env.production`; run `./deploy/deploy.sh up`; `./deploy/deploy.sh sync-nginx`. See `babypulmo/deploy/DEPLOY-VPS.md`.
- [ ] **Day 2** Install GitHub self-hosted runner (~10 min, sixth runner on this VPS) per `babypulmo/deploy/RUNNER-SETUP.md`. Once registered, every push to `main` auto-deploys via `.github/workflows/deploy.yml`.
- [ ] **Day 3** Paste full form content (all tabs) from `submission/form-draft.md`. Check **Variable/Semantic Chunking** (+3). Do NOT check Contextual/Graph RAG. Paste YouTube URL once Shanta delivers.
- [ ] **Day 3–4** Once DNS resolves: `sudo certbot --nginx -d babypulmo.com -d www.babypulmo.com`. Smoke-test: landing + `/docs` + `/chw` over HTTPS.
- [ ] **Day 5** Add uptime monitoring. Full form pre-flight (every tab). Coordinate Dr. Saadi outcome.
- [ ] **2026-05-30** Submit form **by 6pm GMT+6** (5+ hour deadline buffer).

### Faiyad (~8h) — Backend code (NRB, virtual)

- [ ] **Day 2** Audit `app/api/webhook/whatsapp/route.ts` — remove any Twilio remnants; verify Meta Cloud API HMAC signature path is correct.
- [ ] **Day 3** Harden `lib/rag.ts` — replace zero-vector embedding fallback with a hard error in production; add retry-on-429 to OpenAI embedding call.
- [ ] **Day 4** Build `app/api/health/route.ts` returning `{db, classifier, tts}` health JSON for nginx + Compose health checks.
- [ ] **Day 4** Polish webhook signed-URL flow for caregiver audio upload (Supabase Storage path).
- [ ] **Day 5** Prep Phase 2 — outline `colab/train_wav2vec2.py` runbook + `scripts/imci-scrape.ts` skeleton.

### Shanta (~8h) — UI + Video (female, physical)

- [ ] **Day 1** Storyboard the 3-min video from `submission/video-script.md`. Gather B-roll keywords.
- [ ] **Day 2 (~4h)** Record + edit + upload YouTube video. **$0 stack:** ElevenLabs free TTS for voiceover + CapCut free editor + Pexels free B-roll + real screen recording of babypulmo.com. **CRITICAL:** the 1:00–2:00 demo segment must be a real screen recording, not AI-generated footage.
- [ ] **Day 2** Upload as **Unlisted** (not Private) to YouTube. Share URL with Ferdous immediately for the form.
- [ ] **Day 3** Build `app/docs/page.tsx` — single Next.js route that renders `ARCHITECTURE.md`, `accuracy.md`, `submission/summary.md` as a public docs portal. Use a simple markdown-to-HTML library (e.g., `react-markdown` + `remark-gfm`).
- [ ] **Day 4** Polish `app/page.tsx` (landing) + `app/chw/page.tsx` (dashboard) — typography, spacing, mobile-responsive pass.
- [ ] **Day 5** If Dr. Saadi hasn't replied, send backup-pediatrician DM template (adapt `outreach/dr-saadi-email.md`).

### Abdullah (~6h) — Business + Data (physical)

- [ ] **Day 1–2** Draft 3 pilot-LOI templates — one-page MOUs each for BRAC, icddr,b, Smiling Sun. Save to `submission/loi-templates/{brac,icddr-b,smiling-sun}.md`.
- [ ] **Day 3** Send the 3 LOI emails. Track responses in `submission/loi-tracker.md`.
- [ ] **Day 3–4** Pull Coswara dataset statistics — class distribution, audio quality histogram, sex/age splits. Save to `submission/data-analysis.md`. Use this for finals Q&A.
- [ ] **Day 4** Write 1-page financial model — unit economics ($0.003/call), CAC, LTV, Series A pathway. Save to `submission/financials.md`.
- [ ] **Day 5** Prep Q&A answers — accuracy claims, regulatory, competition, exit pathway. Save to `submission/qa-prep.md`.

### Phase 1 verification (Day 5)

- [ ] Form submitted by 6pm GMT+6 on 2026-05-30
- [ ] YouTube URL Unlisted, playable
- [ ] babypulmo.com → VPS, HTTPS valid, landing + `/docs` + `/chw` reachable
- [ ] All 4 team members on form team tab; Dr. Saadi added if confirmed
- [ ] 3 pilot-LOI emails sent

**Target: 130–138 / 153 (85–90%). Top 200 advancement.**

---

## PHASE 2 — Win First Prize at Finals (13 days)

Total effort: ~50–70 person-hours.

### Strategic dimension lift on the 100-pt rubric

| Dimension | Today | Target | Owner | How |
|---|---|---|---|---|
| Innovation (20) | 12 | 17 | Ferdous + Abdullah | Sharpen "first IMCI-grounded RAG-gated pediatric voice triage on WhatsApp." |
| Technical Execution (20) | 6 | 17 | Faiyad (model+RAG) + Ferdous (deploy) | Ship real classifier + real RAG. |
| Business Model (20) | 13 | 17 | Abdullah | 1-page financial model. LOI follow-ups. Series A path. |
| Real-World Impact + Ethics (20) | 13 | 17 | Ferdous + Shanta | Confirm Dr. Saadi as Clinical Advisor. Demo immutable audit log. |
| Scalability + NRB (10) | 7 | 9 | Ferdous (Faiyad credit) | Highlight NRB team member; self-hosted VPS narrative. |
| Presentation (10) | 0 | 9 | Shanta + Ferdous | Tight 4-min pitch + live demo + investor-deck PDF. |
| **Total** | **~51** | **~86** | | |

### Faiyad (~18h) — Backend code

1. **P2-1 to P2-3 (May 31–Jun 2)** Train Wav2Vec2 on Google Colab T4 (~2hrs unattended). Output `babypulmo_wav2vec2_int8.onnx`. Hand to Ferdous via private file transfer. **Do not SSH the VPS.**
2. **P2-4 to P2-6 (Jun 3–5)** **IMCI scrape** — scrape WHO IMCI handbook, chunk via Claude API, embed via OpenAI `text-embedding-3-large` (~$5 one-time), generate `supabase/seed_imci_full.sql`.
3. **P2-5 to P2-7 (Jun 4–6)** Meta WA Cloud API integration code — template messages, signed-URL audio upload, HMAC verify hardening. Push as PRs.
4. **P2-8 (Jun 7)** CHW location-acquisition flow (WhatsApp share-location step in webhook).
5. **P2-9 to P2-11 (Jun 8–10)** Pair-program with Ferdous on rehearsal smoke-test bugs.

### Ferdous (~17h) — Lead + Deploy

1. **P2-3 (Jun 2)** SCP ONNX from Faiyad to VPS `/var/babypulmo/models/`; `./deploy.sh up phase2`; smoke-test E2E.
2. **P2-4 (Jun 3)** Wire `CLASSIFIER_ENDPOINT` env on VPS; verify container networking.
3. **P2-6 (Jun 5)** Run Faiyad's `seed_imci_full.sql` on Supabase.
4. **P2-7 (Jun 6)** Begin Meta WA Business verification (24–72hr lead time — START EARLY).
5. **P2-10 (Jun 9)** Switch demo from sandbox to production WA number once approved.
6. **P2-10 to P2-11 (Jun 9–10)** Confirm Dr. Saadi; add to team page; ingest his script edits into `clinical-content`; `./deploy.sh reload-clinical`.
7. **P2-12 (Jun 11)** Lead first full pitch rehearsal.
8. **P2-Final (Jun 12)** Pitch on stage.

### Shanta (~15h) — Frontend + Presentation

1. **P2-7 to P2-8 (Jun 6–7)** Build investor deck — 10 slides in Canva or Google Slides. Export PDF.
2. **P2-8 to P2-9 (Jun 7–8)** Pitch storyboard + 4-min spoken structure choreography.
3. **P2-10 to P2-12 (Jun 9–11)** Rehearsals + record backup demo video for stage-fallback.
4. **P2-12 (Jun 11)** Final polish on Bangla landing copy + `/docs` page.
5. **P2-Final (Jun 12)** Co-present with Ferdous; manage Q&A pacing.

### Abdullah (~12h) — Business + Data

1. **P2-8 to P2-9 (Jun 7–8)** Pilot-LOI follow-ups to all 3 NGOs.
2. **P2-9 (Jun 8)** Competitive analysis update — Hyfe, Sonde Health, Aevice, Babylon pediatric. Position our LMIC moat.
3. **P2-10 to P2-11 (Jun 9–10)** Finalize unit economics chart + CAC/LTV projections for deck.
4. **P2-11 to P2-12 (Jun 10–11)** Hostile-Q&A answers for business questions (accuracy, regulatory, exit pathway).

### Phase 2 daily timeline

| Date | Day | Key event |
|---|---|---|
| 2026-05-31 | P2-1 | Faiyad: Colab training starts |
| 2026-06-01 | P2-2 | Faiyad: ONNX delivered to Ferdous |
| 2026-06-02 | P2-3 | **Ferdous: classifier container live on VPS** |
| 2026-06-03 | P2-4 | Faiyad: IMCI scrape begins |
| 2026-06-04 | P2-5 | Faiyad: IMCI continues + Meta WA code |
| 2026-06-05 | P2-6 | Ferdous: IMCI loaded to Supabase; Faiyad: webhook polish |
| 2026-06-06 | P2-7 | Ferdous: Meta WA Business verification filed |
| 2026-06-07 | P2-8 | Shanta: investor deck draft; Abdullah: competitive analysis |
| 2026-06-08 | P2-9 | All: send LOI follow-ups; begin pitch memorization |
| 2026-06-09 | P2-10 | Ferdous: production WA number live; Dr. Saadi on team page |
| 2026-06-10 | P2-11 | All: full timed pitch rehearsal #1 |
| 2026-06-11 | P2-12 | All: rehearsal #2 + hostile Q&A + backup demo video |
| **2026-06-12** | **P2-Final** | **🏆 Finals Day (Dhaka)** |

### Phase 2 verification (Jun 12 AM)

- [ ] `lib/classifier.ts` hits real VPS classifier (no longer mock)
- [ ] `lib/rag.ts` semantic retrieval from full IMCI corpus (no keyword fallback)
- [ ] Meta WA number live (production OR sandbox); voice note → Bangla TTS reply + `/chw` alert
- [ ] Dr. Saadi (or backup) on team page as Clinical Advisor
- [ ] Investor deck PDF on USB + cloud
- [ ] Backup demo video recorded
- [ ] 4-min pitch timed 3:45–4:15 in final rehearsal
- [ ] Hostile-Q&A battery (10 questions) practiced

---

## Honest posture (locked — do NOT compromise)

Judges punish fabrication harder than missing optional bonuses. The submission's intellectual honesty is a competitive advantage.

**Do NOT claim:**
- Contextual RAG / Graph RAG (not built)
- Agent frameworks (LangGraph, CrewAI — intentionally avoided for clinical determinism)
- On-device LLMs / Ollama (architecturally wrong for our phone profile)
- n8n / Temporal (we use Vercel cron + Supabase pg_cron + systemd timers)
- Accuracy beyond 70–78% lab / 58–68% field

**Do claim (all defensible):**
- Wav2Vec2-XLSR-53 fine-tuned on Coswara + COUGHVID + ICBHI
- Naive RAG with Variable/Semantic Chunking over pgvector
- Rules-gated deterministic severity (no LLM at runtime)
- Clinician-vetted stock Bangla scripts (after Dr. Saadi review)
- Meta WhatsApp Cloud API direct (no Twilio markup)
- PostGIS Haversine CHW routing
- Immutable audit log
- Singapore region for BD data residency
- Self-hosted Docker on $7/mo VPS (scales horizontally)

---

## Risks & contingencies

| Risk | Likelihood | Mitigation |
|---|---|---|
| Dr. Saadi doesn't reply | Med | Shanta runs backup-pediatrician outreach Day 5 |
| Meta WA verification stalls | High | Fall back to Meta sandbox (5 testers, OK for judging) |
| Colab training fails | Low | HuggingFace pre-trained checkpoint + 30min fine-tune |
| NGO LOIs: no response | High | Outreach itself becomes pitch story |
| babypulmo.com DNS issues | Low | Form's "Live Demo" field accepts raw VPS IP |
| Faiyad timezone gap | Med | Async GitHub Issues; daily 9pm BDT sync = 11am ET |
| VPS unreachable in finals | Med | Docker `restart: unless-stopped` + nginx auto-restart via systemd + recorded backup demo |
| Ferdous bottleneck on deploy | Med | `DEPLOY-VPS.md` is full enough that any teammate can take over |

---

## Out of scope (we are NOT doing this)

- Contextual RAG, Graph RAG, agent frameworks, on-device LLMs
- BMRC ethics submission (framed as planned, not done)
- Production multi-region deployment
- Trademark filing (12-month process; separate from competition)

---

## File-of-truth pointers

| What | Where |
|---|---|
| This plan | `competition/WIN-PLAN.md` (this file) + mirror in `BabyPulmo/docs` |
| Form paste source | `submission/form-draft.md` |
| Video script | `submission/video-script.md` |
| Dr. Saadi outreach | `outreach/dr-saadi-email.md` |
| VPS runbook | `babypulmo/deploy/DEPLOY-VPS.md` |
| Architecture | `babypulmo/ARCHITECTURE.md` + `babypulmo/README.md` (mermaid) |
| Honest accuracy | `submission/accuracy.md` |
| IP strategy | `submission/ip-strategy.md` |
| Names history | `submission/names.md` |
| Clinical content (private) | `BabyPulmo/clinical-content` repo |

---

*Last updated: 2026-05-25. Update this file as you complete tasks. The team source-of-truth.*
