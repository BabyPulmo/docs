# BuildFest 2026 — Submission form draft (paste-ready)

Each `###` heading below maps to one form field. Copy the prose that follows directly into that field. Fields marked **N/A — [reason]** are honest answers — do not fabricate. The two deferred sections (Data & AI Provenance, Tooling & IDE) are not drafted here; fill those yourself.

Source docs (for cross-reference):
- `submission/summary.md` — 1-page submission
- `babypulmo/ARCHITECTURE.md` — 8-layer mapping + responsible-AI choices
- `babypulmo/COSTS.md` — per-call cost breakdown
- `babypulmo/README.md` + `DEPLOY.md` — stack + deploy

---

## Event & Team

### Event
The Infinity AI BuildFest 2026

### Team
Fintant

### Phase
Preliminary Submission (Due: May 30, 2026, 11:59 PM GMT+6)

---

## Project Info

### Project Name
Baby Pulmo — AI Pediatric Cough Diagnostic

### Elevator Pitch
"Child's Voice" — a Bangla voice-first WhatsApp AI that listens to a 30-second pediatric cough recording and tells a rural Bangladeshi caregiver, in under 10 seconds, whether their child needs to see a doctor right now. Built on Wav2Vec2 cough acoustics, WHO IMCI RAG, and PostGIS-routed Community Health Worker alerts — the LMIC-deployable, pediatric-focused version of the cough-AI category Pfizer acquired (ResApp Health, AUD $179M, 2022).

### Public Summary
A caregiver records a 30-second cough on WhatsApp. Baby Pulmo's classifier (Wav2Vec2-XLSR fine-tuned on Coswara, int8 ONNX on Modal CPU) returns a six-class pediatric respiratory diagnosis with confidence and a Grad-CAM spectrogram heatmap. A deterministic severity table maps the result to a clinician-vetted Bangla audio reply, retrieved from WHO IMCI and Bangladesh DGHS protocols via Supabase pgvector RAG. If severity rules trigger, the nearest Community Health Worker is auto-paged via Meta WhatsApp with the audio attached and the caregiver's GPS. Total per-interaction cost: ≈ $0.003.

### Domain
Healthcare (HealthTech)

### Challenge
Health Worker Assistant

### Problem Statement
Pneumonia kills 740,000 children under 5 globally each year (WHO) — the single largest infectious killer of children. Bangladesh alone loses ~25,000 children/year to acute respiratory infections. Rural Bangladesh has roughly one doctor per 8,000 people, and 63% of Bangladeshi children with pneumonia are never taken to a qualified provider, because caregivers cannot distinguish pneumonia from a common cold (BDHS 2022). The average time from symptom onset to qualified care is 36+ hours — long enough that severe pneumonia is often already fatal. Existing telemedicine and toll-free hotlines require literacy, smartphone data plans, or a working clinic nearby. None of them listen to the actual cough.

### Solution Description
Baby Pulmo is an eight-layer AI-native system that meets caregivers on WhatsApp, in Bangla, in voice — the channel they already use. (1) **User Interaction:** Meta WhatsApp Cloud API direct (free service messages in Bangladesh). (2) **Audio Preprocessing:** WebRTC noise removal, cough segmentation, and an RMS+duration quality gate. (3) **AI Intelligence:** Wav2Vec2-XLSR-53 fine-tuned on Coswara, COUGHVID, and ICBHI; int8 ONNX quantized; served on a Modal serverless 2-vCPU CPU container (~5s inference). Output is six-class pediatric respiratory classification with confidence + a Grad-CAM spectrogram heatmap for explainability. (4) **Knowledge Retrieval:** Supabase pgvector RAG over WHO IMCI and Bangladesh DGHS pediatric protocols, indexed with OpenAI text-embedding-3-large. (5) **Decision Layer:** a deterministic severity rules table — *not LLM discretion* — maps (class, confidence) to one of seven clinician-reviewed stock Bangla scripts. (6) **Agent Orchestration:** PostGIS Haversine finds the nearest CHW and dispatches a Meta utility-template message with the audio attached and GPS. (7) **Data Infrastructure:** Supabase Postgres + PostGIS + an immutable `audit_log` row per interaction for BMRC ethics review trail. (8) **Deployment:** Vercel + Supabase + Modal CPU + GCP bn-IN WaveNet TTS (content-hash cached, >99% hit on the stock library). Net: a Bangla mother gets clinically-grounded guidance in under 10 seconds for one-third of one US cent.

---

## Data Lifecycle & Engineering

### 1. Data Sources — checkboxes
- ☑ External APIs (paid/free) — Meta WhatsApp Cloud API, GCP TTS, OpenAI embeddings
- ☑ Open Datasets (Kaggle, HF, gov) — Coswara (IISc), COUGHVID (EPFL), ICBHI
- ☑ User Uploads / Bulk Import — caregiver-submitted cough voice notes (with opt-in consent)

### 1. Data Sources — specific list
- **Training audio (open):** Coswara (IISc Bangalore, ~5,000 South Asian respiratory samples), COUGHVID (EPFL, ~25,000), ICBHI pediatric chest sound database.
- **Clinical knowledge base (public domain):** WHO IMCI handbook, Bangladesh DGHS pediatric guidelines, UNICEF pneumonia guidance.
- **APIs:** Meta WhatsApp Cloud API (inbound voice notes + outbound replies/alerts), Google Cloud Text-to-Speech (bn-IN WaveNet), OpenAI text-embedding-3-large (one-shot IMCI ingest), Modal (serverless ONNX inference).
- **Field data (Phase 1 pilot):** de-identified caregiver voice notes from BRAC community health unit, Bogura district — stored with opt-in consent and BMRC ethics review path.

### 2. Acquisition Methods — checkboxes
- ☑ Bulk Upload (CSV/XLSX/PDF intake) — Coswara/COUGHVID/ICBHI loaded at training time
- ☑ Automated Flows (n8n, Airflow, cron, webhooks) — Vercel cron pre-warms TTS cache; webhook-driven main path
- ☑ API Pull / SDK integrations — OpenAI embeddings, GCP TTS, Modal inference, Meta WhatsApp media-download
- ☑ Speech-to-Text (Whisper, Deepgram) — Wav2Vec2-XLSR audio encoder (cough acoustics, not transcription)

### 2. Scrapers / crawlers used
N/A — all training audio is downloaded from published open datasets (Coswara, COUGHVID, ICBHI); all clinical knowledge is ingested from official WHO and Bangladesh DGHS documents. No web scraping in the production or training pipeline.

### 2. MCP servers for data access
N/A — production data path is direct: Meta WhatsApp webhook → Next.js route handler → Supabase service-role client → Modal HTTPS endpoint. No MCP servers in the runtime stack. (Internal developer tooling may use Postgres MCP and Filesystem MCP for inspection; not part of the user-facing pipeline.)

### 3. Parsing, Formats & Cleaning — checkboxes
JSON · JSONL · CSV · XLSX · PDF · Markdown · WAV · OGG · MP3 · Images (Grad-CAM heatmaps)

### 3. Parsers used
- `librosa` and `soundfile` — load OGG voice notes from Meta and WAV training files; resample to 16 kHz mono.
- `ffmpeg` — OGG ↔ WAV transcoding in the webhook handler.
- `onnxruntime` — load the quantized Wav2Vec2 model on Modal CPU.
- `pdf-parse` + custom chunker — ingest WHO IMCI and Bangladesh DGHS PDFs into pgvector chunks.
- `transformers` (Hugging Face) — only at training time, not in production.

### 3. Formatters / converters
ffmpeg (OGG↔WAV↔MP3), `librosa.resample` (sample-rate normalization), `onnxruntime.quantization.quantize_dynamic` (FP32 → int8 ONNX), pgvector embedding format (1536-d float32). IMCI PDFs converted to Markdown chunks before embedding.

### 3. Data cleaning & enrichment
- **Audio quality gate:** RMS energy threshold + minimum/maximum duration + WebRTC voice-activity detection — rejects silent uploads, breath-only clips, and accidental music.
- **Cough segmentation:** isolates cough events from background noise so the classifier sees signal, not babble.
- **Noise removal:** WebRTC noise suppression on inbound voice notes.
- **Confidence gating:** RAG and severity decisions only fire when classifier confidence ≥ 0.5; below that we ask for a re-record.
- **Stock-script enrichment:** every (class, severity) tuple maps to a clinician-vetted Bangla script — the model never speaks unrehearsed words.

### 3. Schema validation
Zod for all TypeScript request/response shapes (webhook payload, classifier response, RAG result). Pydantic on the Modal endpoint. Postgres CHECK constraints on enum columns (class, severity). Audio uploads validated against allowed MIME types and a 1 MB ceiling.

### 4. Storage Targets — checkboxes
- ☑ Relational (Postgres, MySQL) — Supabase Postgres
- ☑ Vector DB (pgvector, Pinecone, Weaviate) — Supabase pgvector
- ☑ Object Storage (S3, R2, GCS) — Supabase Storage (S3-compatible) for caregiver audio + cached TTS replies

### 4. Storage design
Single Supabase Postgres instance with three extensions: **pgvector** (IMCI/DGHS chunks, 1536-d), **PostGIS** (CHW geo-index, Haversine `find_nearest_chw`), and standard relational tables (caregivers, classifications, escalations, audit_log). The `audit_log` table is append-only by RLS policy and partitioned by month for retention. Audio is stored in Supabase Storage behind signed URLs (TTL = 24h for caregiver replays; permanent for CHW alerts). Bangladesh data-residency satisfied by Supabase Singapore region (closest available). De-identification at write time: no name, no phone number stored in audit log — only an opaque caregiver_id hash.

### 5. Visualization — checkboxes
- ☑ Recharts — CHW dashboard (`/chw` Next.js page)
- ☑ Grafana — operational metrics (cost/call, classifier latency, error rate)

### 5. Visualization details
- **CHW dashboard:** real-time ranked list of pending alerts, sorted by severity then distance, with embedded audio player, Grad-CAM spectrogram heatmap, and one-click "I am responding" / "Resolved" actions. Updates push live via Supabase Realtime channels.
- **Grad-CAM heatmaps:** every classification returns a PNG overlay on the mel spectrogram showing which acoustic frequencies/timesteps drove the result — satisfies the BuildFest "explainable AI" requirement and is shown to CHWs.
- **Caregiver UX:** intentionally no charts — voice-only Bangla. Visualization is for the clinician/CHW side only.

### 5. Dashboards & reports
CHW realtime dashboard (Recharts + Supabase Realtime). Grafana operational dashboard tracking per-call cost, p50/p95 inference latency, classifier confidence distribution, escalation rate, CHW response time. Weekly de-identified CSV export for clinician review of misclassifications.

### 6. Insights — checkboxes
- ☑ Deep Learning (PyTorch, TensorFlow, JAX) — Wav2Vec2-XLSR fine-tune
- ☑ LLM Inference / RAG over data — pgvector RAG over IMCI/DGHS (Claude is *not* used at runtime; rules-gated design)
- ☑ Rule Engine / Heuristics (non-AI) — deterministic severity rules table
- ☑ Statistical Analysis — KPI aggregations, sensitivity/specificity tracking

### 6. AI / ML details
**Model:** Wav2Vec2-XLSR-53 (Facebook, multilingual self-supervised audio encoder) fine-tuned on Coswara + COUGHVID + ICBHI for six-class pediatric respiratory classification (healthy / common cold / bronchiolitis / pneumonia / asthma / croup). **Training:** Google Colab T4 GPU, ~2 hours, AdamW + cosine schedule, weighted cross-entropy for class imbalance. **Quantization:** `onnxruntime.quantization.quantize_dynamic` → int8 ONNX, ~4× size reduction, ~3× CPU speedup with <1pt accuracy loss. **Serving:** Modal serverless 2 vCPU / 2 GB CPU container, ~5 s per inference. **Explainability:** Grad-CAM on the final transformer layer, projected back to mel-spectrogram space. **Target sensitivity on pediatric pneumonia: ≥84%**, matching the JAMA Pediatrics 2018 benchmark. **RAG:** OpenAI text-embedding-3-large (one-shot ingest of ~200 IMCI/DGHS chunks); cosine similarity in pgvector; top-3 chunks per query.

### 6. Non-AI analytics
- **Severity rules table:** deterministic `(class, confidence) → severity` lookup in `lib/claude.ts` — clinician-reviewable, no model discretion.
- **KPI aggregations (SQL on `audit_log`):** time-to-care (symptom→CHW response), classifier sensitivity/specificity vs CHW ground-truth, CHW response time distribution, escalation rate, cost-per-interaction.
- **Statistical tests:** Wilson confidence intervals on sensitivity in pilot cohort; chi-square for misclassification skew across age groups.

### 6. How are insights delivered to users?
- **Caregiver:** Bangla audio reply on WhatsApp (≤10 s end-to-end) — voice-only because rural literacy is mixed.
- **CHW:** WhatsApp utility-template alert with audio attachment, GPS, severity, and one-tap dashboard link; ranked queue on the `/chw` realtime dashboard.
- **Clinician / partner (BRAC, DGHS):** weekly de-identified CSV digest of misclassifications and severity distribution.
- **Ethics / regulator:** immutable `audit_log` with full payload per interaction, accessible to BMRC reviewers.

### 7. Orchestration
**Event-driven, not Airflow-scale.** Inbound: Meta WhatsApp webhook → Vercel edge function (`/api/webhook/whatsapp`) — synchronous orchestration of classify → RAG → rules → TTS → reply → optional escalation. Background: Vercel cron (TTS cache pre-warm, daily KPI rollup) and Supabase `pg_cron` (audit log monthly partition rotation). No Kafka or Airflow — the per-call latency budget is 10 s, dominated by classifier inference, so a single edge function is the right primitive.

### 7. Scheduling / Triggers
- **Webhook-driven (primary):** every caregiver voice note hits `/api/webhook/whatsapp` POST.
- **Vercel cron:** `0 */6 * * *` to pre-warm the GCP TTS cache after every deploy and every 6h thereafter (`warmStockCache()` in `lib/tts.ts`).
- **Supabase pg_cron:** nightly rollup of `audit_log` into a denormalized KPI view; monthly partition rotation.
- **Verification handshake:** GET `/api/webhook/whatsapp` returns Meta hub challenge.

### 7. Streaming / Real-time
**Supabase Realtime** channels for the CHW dashboard — Postgres logical replication pushes new escalation rows to subscribed CHW browsers in <1 s. No Kafka/Redpanda/NATS — Supabase Realtime is sufficient for the alert fan-out, and adding a broker would be premature infrastructure.

### 8. Outbound APIs
- **Meta WhatsApp Cloud API direct:** caregiver replies (free service messages in BD) and CHW alerts (utility templates, $0.014 each). Implemented in `lib/whatsapp.ts` with HMAC signature verification on inbound.
- **CHW dashboard:** Next.js App Router routes (`/chw`) authenticated via Supabase Auth + RLS.
- **Internal classify endpoint:** `/api/classify` for testing the Modal inference path directly.

### 8. Webhooks & exports
- **Inbound webhook:** Meta WhatsApp → `/api/webhook/whatsapp` (POST events + GET verification handshake).
- **Outbound webhook (planned):** partner notification (BRAC / DGHS) on CHW escalation.
- **Exports:** weekly de-identified CSV of `audit_log` for clinician review; on-demand PDF report of per-district KPIs.

### 8. Embeddings / model serving
- **Cough classifier:** Modal serverless ONNX endpoint (HTTPS POST audio → JSON with class, confidence, Grad-CAM PNG). Cold start ~3 s, warm ~5 s inference, scales to zero between calls.
- **Text embeddings:** OpenAI text-embedding-3-large — one-shot at ingest time only (~200 IMCI chunks, <$1 total); never called at runtime.
- **TTS:** GCP Text-to-Speech `bn-IN-Wavenet-A` over HTTPS, content-hash cached in Supabase Storage so the stock library produces >99% cache hits.

### 9. Open Source Stack
- **Next.js 14 (App Router)** — application framework on Vercel.
- **Wav2Vec2-XLSR-53 (Facebook, via Hugging Face Transformers)** — pretrained audio encoder we fine-tune.
- **ONNX Runtime** — production inference with int8 quantization on Modal CPU.
- **librosa + soundfile + ffmpeg** — audio loading, resampling, format conversion.
- **PyTorch** — training only (Colab T4).
- **pgvector** — Postgres vector extension for RAG.
- **PostGIS** — geo-indexed nearest-CHW routing.
- **Supabase** (open-source Postgres + Storage + Auth + Realtime).
- **Zod** — TypeScript request/response validation.
- **Recharts** — CHW dashboard charts.
- **Tailwind CSS + shadcn-style components** — UI.

### 10. Data quality
Three-layer quality gate: (1) **inbound audio** rejected if RMS < threshold, duration outside [3 s, 90 s], or WebRTC VAD finds no voice activity — caregiver is asked to re-record in Bangla. (2) **classifier confidence** below 0.5 triggers a "please re-record in a quiet room" Bangla reply instead of guidance. (3) **RAG retrieval** falls back to a generic IMCI safety script if no chunk scores above similarity threshold. All seven (class, severity) Bangla scripts are clinician-vetted and stored as immutable assets — the system literally cannot say something a clinician hasn't approved.

### 10. Privacy & compliance
- **De-identified storage:** no name or phone number in `audit_log` — only an opaque caregiver_id hash.
- **Opt-in consent:** first-message Bangla consent script explicitly opts the user into research use of their cough recording.
- **BMRC (Bangladesh Medical Research Council) ethics review path identified** for Phase 1 BRAC pilot.
- **Immutable audit log** by Postgres RLS policy — required for BMRC review trail.
- **Signed URLs** with 24h TTL for caregiver replays; permanent for CHW alerts.
- **Data residency:** Supabase Singapore region (closest to BD).
- **Decision-support framing** (not a medical device): caregiver-facing Bangla never says "your child has X," only "the cough shows signs of X — see a doctor." Same legal posture as ResApp Health.

### 10. Lineage & observability
- **Immutable `audit_log` table** — row per interaction with full payload (classifier output, RAG chunks, severity, script used, TTS cache hit, escalation status). Doubles as lineage and ethics audit.
- **Vercel + Modal + Supabase logs** aggregated; Vercel function logs include request-ID propagation.
- **Sentry** on the webhook handler (errors, p95 latency).
- **Grafana operational board** sourced from a Supabase log drain — cost/call, classifier p95 latency, escalation rate, CHW response time.
- **Per-deploy smoke test:** `warmStockCache()` runs after every deploy and verifies all seven stock scripts are cached.

### 10. Cost & performance
**Per-interaction cost ≈ $0.003 weighted average** (80% standard + 20% escalated), broken down: classifier $0.0003 (Modal CPU int8 ONNX), audio storage ~$0.0001, embedding ~$0.00001, Bangla guidance $0 (stock library, no LLM), TTS ~$0 (content-hash cached, >99% hit), Meta WhatsApp service messages $0 (free in BD), CHW utility template $0.014 (escalated only). Four optimizations got us from $0.064 → $0.003 (21× cheaper): (i) drop runtime LLM for stock Bangla scripts, (ii) swap ElevenLabs for GCP bn-IN WaveNet with content-hash cache, (iii) Twilio → Meta WhatsApp Cloud API direct, (iv) int8 ONNX on Modal CPU instead of A10G GPU. End-to-end p95 latency target: <10 s. Free-tier headroom covers the first ~1,000 monthly users at $0 all-in.

### 10. Anything else about your data stack?
The single most important design choice is **rules-gated severity with no runtime LLM**. The classifier outputs a class and confidence; a deterministic table maps that to one of seven pre-written, clinician-vetted Bangla scripts. No model generates new prose at request time, so every word a caregiver hears was vetted in advance. This collapses three otherwise-painful problems at once: (a) clinical liability — a clinician signs off on the actual words; (b) Bangla TTS cost — the stock library produces >99% cache hits; (c) reproducibility — given the same (class, severity), the user gets the same audio every time. The LLM (Claude) is used only at *ingest* time to chunk IMCI PDFs — never at inference time. This is the BuildFest "responsible AI" requirement implemented at the architecture level, not as a disclaimer.

---

## Deferred sections (fill yourself)

- **Data & AI Provenance** — not drafted (per your request).
- **Tooling & IDE** — not drafted (per your request).
