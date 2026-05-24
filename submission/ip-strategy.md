# IP Strategy — Trademark, Patent, FTO

For the Baby Pulmo product. Budget envelope $10k–$50k. Target jurisdictions: **US (USPTO) + Madrid Protocol (WIPO)**. Patent posture: **honest** — most of the underlying technology is published prior art or owned by incumbents; we file narrowly, lean on trade secret and defensive publication.

> ⚠️ **Nothing in this document is legal advice.** It is a strategy scope for a conversation with a real IP attorney. Hire counsel before filing anything. Specifically: an attorney dual-qualified in **Bangladesh DPDT + US USPTO**, or coordinate two firms.

---

## Part 1 — "Baby Pulmo" evaluated as a name

Quick verdict: **strong contender**, on par with Vyana from the earlier shortlist, but with a different risk profile worth understanding before $5–10k of trademark money lands on it.

### What's good

- **Crystal-clear category in two words.** "Baby" + Latin "pulmo" (lung). A doctor, a parent, a Series A investor, a UNICEF program officer — every audience instantly knows it's a pediatric respiratory product. Most other candidates need a tagline; this one doesn't.
- **Warm + clinical at once.** "Baby" signals approachable; "pulmo" signals medical authority. Same emotional pairing as Eko (cardio) or PillPack (consumer pharma) — names that work because they're warm-but-credible.
- **Memorable, almost unmisspellable.** Important for a WhatsApp product where caregivers see the name in plain text.
- **Travels.** "Baby" is near-universally understood; "pulmo" is recognized as a medical root globally (Pulmocort, Pulmozyme, etc.).

### What's risky

1. **Descriptiveness risk at USPTO.** US trademark law refuses marks that are "merely descriptive" of the goods (Lanham Act §2(e)(1)). "Baby Pulmo" for a baby-lung diagnostic *is* describing the product. The argument that saves it is that "pulmo" is **Latin / suggestive** rather than the English word "lung" — that makes it a *suggestive* mark (registrable on the Principal Register) rather than *descriptive* (only on Supplemental Register without secondary meaning).
   - Most likely outcome: **registrable as suggestive**, but expect a possible §2(e)(1) office action. Your attorney's response brief is what gets it through.
   - Worst case: forced to register on Supplemental Register first, then convert to Principal after 5 years of use (acquired distinctiveness).

2. **"Baby + medical" namespace is crowded.** BabyCenter, BabyBjorn, Baby Brezza, Baby Einstein, Babybel, Babyganics — none in cough-AI specifically, but examiners look at *likelihood of confusion* across the whole baby/infant category. None should block "Baby Pulmo" but each must be cleared.

3. **"Pulmo" appears in many class-5 pharma marks.** Pulmozyme (Roche), Pulmocort, Pulmicort, PulmoLife. These are class 5 (pharmaceuticals) — different from our class 9/10/44 (software/devices/services) — so technically not blocking, but examiners can find them in cross-class confusion analysis. Should clear with attorney clearance opinion.

4. **Two-word names are slightly worse for domains.** `babypulmo.ai` and `babypulmo.com` are likely *available* but you can't get a single-word URL. Minor.

### Verdict vs the earlier Top 3

| Name | Tells the product? | Trademark headroom | Investor/clinician feel | Parent feel |
|---|---|---|---|---|
| **Baby Pulmo** | ⭐⭐⭐⭐⭐ best | ⭐⭐⭐ ok (descriptiveness risk) | ⭐⭐⭐⭐ very good | ⭐⭐⭐⭐⭐ best |
| **Vyana** | ⭐⭐ requires explanation | ⭐⭐⭐⭐⭐ best (open namespace) | ⭐⭐⭐⭐⭐ best | ⭐⭐⭐ ok |
| **Respira** | ⭐⭐⭐⭐ very good | ⭐⭐⭐ ok (Respira Therapeutics exists) | ⭐⭐⭐⭐ very good | ⭐⭐⭐⭐⭐ best |
| **Karuna** | ⭐⭐ requires explanation | ⭐⭐⭐ ok (Karuna Therapeutics ~$3B, different IP class) | ⭐⭐⭐⭐ very good (mission-led) | ⭐⭐⭐⭐ very good |

**Recommendation:** Pay your attorney to **clear all of Baby Pulmo, Vyana, and Respira in parallel** (one $2k clearance covers up to ~5 marks at most firms). Pick whichever comes back cleanest, with a preference order of:

1. **Baby Pulmo** if descriptiveness office action looks survivable — best parent-facing, best fundraising name.
2. **Vyana** if Baby Pulmo gets stuck — best trademark headroom, most defensible position.
3. **Respira** as warm fallback.

---

## Part 2 — Trademark strategy

The part actually worth doing well. Trademark is comparatively cheap, the protection lasts forever (with renewals), and a registered trademark in the US is table-stakes for any healthtech Series A.

### Classes to file (Nice classification)

- **Class 9** — Downloadable software / mobile application / data analysis software → covers the Next.js app, the WhatsApp integration, the model serving.
- **Class 10** — Medical and diagnostic apparatus → covers the cough-classification "device" angle, important if you ever build a clinic-grade version.
- **Class 44** — Medical services including telemedicine, healthcare information, medical screening → covers the actual service caregivers receive.
- **(Optional) Class 41** — Educational services / training of medical personnel → file later if you scale CHW training.

File all three (9, 10, 44) from day one. Adding classes after registration costs almost as much as new filings.

### Pre-filing clearance

1. **DIY pass — free, do tonight:**
   - USPTO TESS: https://tmsearch.uspto.gov — search "Baby Pulmo", "Pulmo", "Baby Lung", phonetic variants.
   - WIPO Global Brand Database: https://branddb.wipo.int — global view across Madrid members.
   - Google + ICANN WHOIS for the obvious domains.
   - Knock out anything that turns up identical or near-identical in classes 5, 9, 10, 41, 44.

2. **Mandatory professional clearance opinion — $1,500–2,500:**
   - Attorney runs broader phonetic, semantic, and design-mark searches.
   - Issues a written opinion: register / register-with-risk / abandon.
   - **Do not file anything until this opinion is in your inbox.** Filings without clearance are how startups burn $10k and end up with an unenforceable Supplemental Register mark.

### Filing sequence

Because Madrid Protocol requires a "home" base application, the order matters:

| # | When | What | Why |
|---|---|---|---|
| 1 | Week 3 | **File BD DPDT trademark** (classes 9, 10, 44, intent-to-use) | Madrid Protocol *requires* a base application or registration in your home country. BD DPDT becomes the priority anchor for everything else. |
| 2 | Week 4 (parallel) | **File USPTO direct** (classes 9, 10, 44, §1(b) intent-to-use) | US examiners are notoriously strict; filing direct rather than via Madrid designation gives you cleaner prosecution. The premium over Madrid designation is worth it for the US specifically. |
| 3 | Month 6 | **File Madrid Protocol designation** through WIPO | Designate: EU, India, Indonesia, Nigeria, Philippines, Pakistan (the Phase 2–4 markets in `summary.md`). One filing covers all six. |
| 4 | Month 6–24 | **Respond to office actions** as they arrive | Budget $500–2,000 per office action; expect 1–2 from USPTO. |
| 5 | Month 36 (US) | **File Statement of Use** before §1(b) deadline | Once you have a commercial product/specimen. Required to perfect the US registration. |

### Estimated trademark cost envelope

| Line item | Cost |
|---|---|
| Professional clearance opinion | $1,500–2,500 |
| BD DPDT (3 classes + attorney) | $200–400 |
| USPTO direct (TEAS Plus $350/class × 3 + attorney $750) | $1,200–2,200 |
| Madrid base fee + 6 designations × 3 classes | $3,500–5,500 |
| Office-action response budget | $2,000–4,000 |
| **Total** | **~$8.5k–14.5k** |

Comfortably inside the $10k–$50k envelope with headroom.

### Defensive registrations

After picking your primary name, spend ~$300–500 to register **the runner-up names (Vyana, Respira) in BD only** — blocks domestic squatters cheaply if you ever want to pivot or sub-brand. Don't extend defensive registrations internationally; not worth the cost.

---

## Part 3 — Patent strategy (the honest version)

The hard truth: **most of what we built is not patentable**. Let's be clear-eyed about it.

### Prior art that blocks the obvious patent claims

Do NOT try to patent these — you will be rejected, lose the filing fees, and worse, publish your approach as prior art *against yourself* on appeal:

- **Wav2Vec2 itself** — open-source Meta/FAIR, freely licensed.
- **Cough acoustic classification via deep learning** — ResApp Health's patent portfolio (now Pfizer) covers this broadly; JAMA Pediatrics 2018; Hyfe portfolio; Cohort.ai patents; extensive academic literature.
- **Retrieval-augmented generation over clinical guidelines** — RAG technique is unpatentable in itself; specific applications to clinical guidelines have been published.
- **WhatsApp medical chatbots / WhatsApp telemedicine** — Babylon, Ada Health, multiple competitors have priority.
- **Coswara / COUGHVID / ICBHI dataset usage** — these are explicitly open datasets.
- **Mel spectrogram + Grad-CAM** — both extensively published computer vision techniques.

### What might be patentable (system claims only)

Three angles where there's potentially novel combination IP:

1. **Rules-gated severity + clinician-vetted multilingual stock script library.** The specific *workflow* of:
   - (a) audio classifier on pediatric cough → 6-class output with confidence,
   - (b) **deterministic** severity rules table (explicitly *not* LLM discretion) mapping (class, confidence) → severity,
   - (c) clinician-vetted pre-recorded stock scripts in low-resource language served at request time,
   - (d) PostGIS-routed nearest-CHW alert with original audio + GPS as the escalation payload.

   None of the parts are novel individually. The *combination* applied to **low-resource pediatric care** may be novel and non-obvious. This is a **combination claim** — weak (easy to design around) but useful for investor signaling and as a deterrent.

2. **Pediatric-specific threshold calibration.** ResApp's portfolio is largely adult-cough. Pediatric cough acoustics differ enough that pediatric-specific severity thresholds and quality gates could be claimed as a distinct system. Narrow but defensible.

3. **Audio + GPS escalation payload as human-in-loop trigger.** Most cough-AI systems return a diagnosis to the user; ours forwards the original audio + caregiver GPS to a community health worker as the actual decision-maker. This human-in-the-loop pattern is unusual enough to be claimable.

### Recommended patent action

**File ONE US provisional patent application** on the combination/system claim above. That's it. For now.

| Why | What |
|---|---|
| Locks 12-month priority date | Anyone filing a similar claim after our priority date is blocked or junior |
| Lets you say "patent pending" | Real value in investor decks; modest deterrent against copycats |
| Not examined; minimal disclosure burden | You're not required to draft formal claims; a detailed specification + drawings suffices |
| Cheap | $300 USPTO fee + $1,500–3,000 attorney drafting = **$2k–3.5k all-in** |
| Reversible | If 12 months later there's no real threat, let it lapse — the priority date was the value |

**Do NOT do** any of these:
- File a Bangladesh DPDT patent — weak enforcement, expensive, BD isn't where competitive litigation happens.
- File a non-provisional US patent now — examination costs $5–10k more and you don't have product traction yet to justify it.
- File a PCT international application now — premature; wait for Series A pressure.
- Pay an attorney to draft maximally broad claims — they'll get narrowed to nothing under prior art and you'll have wasted $20k.

### 12-month decision point

When the provisional approaches its 12-month deadline, choose one:

| Choice | Cost | When it makes sense |
|---|---|---|
| **Convert to US non-provisional** | $5–10k | Real competitor entered the pediatric cough-AI space; or VC pushing for stronger IP |
| **File PCT international** | $3–5k base + per-country later | Series A imminent and they want a global portfolio |
| **Let it lapse** | $0 | No competitive threat; the priority date was enough for the deck and FTO posture; trade secret + defensive publication carries forward |

### Trade secret — the real moat

What you keep secret is more valuable than what you patent:

- **The clinician-vetted Bangla (and later, multi-language) stock script library.** This is the actual differentiator. The exact wording of each (class, severity) script — vetted by pediatricians for clinical accuracy and by linguists for cultural sensitivity — is hard to reproduce and is what makes the system clinically deployable. **Keep it out of the public repo.** Move it from `lib/tts.ts` to a private config repo or encrypted Supabase table that's not in the public GitHub.
- **Threshold calibration values** in the severity rules table — these were tuned against pilot data and are how-it-actually-works knowledge.
- **Training data curation pipeline** — how you cleaned Coswara, what you discarded, what augmentations you used. The model card can be public; the recipe is not.
- **Quality-gate parameters** — exact RMS thresholds, duration bounds, VAD sensitivity.

For each: trade-secret protection requires (a) marking it confidential, (b) limiting access, (c) NDAs with anyone who sees it, (d) reasonable security measures. Talk to your attorney about a trade-secret protocol document.

### Defensive publication — free protection

The public GitHub repo `Shishukantho/babypulmo` (created earlier this session) is *itself* a defensive publication. Every line of code, every architecture choice in `ARCHITECTURE.md`, every cost decision in `COSTS.md` — all of it is **prior art as of the day it was pushed**. That blocks competitors from patenting around the techniques *you've published*.

Worth doing on top:
- **arxiv preprint** of the architecture + the rules-gated severity design — costs $0, blocks $$ of competitor patent claims, also builds academic credibility for FDA/CE submissions later.
- **Medium / Substack post** of the system overview — same effect, broader reach.
- **Conference talk** at any healthtech conference — same effect plus PR.

The trade-off: anything you publish, you can no longer patent. So publish the parts you don't need patent protection for (architecture, costs, philosophy) and keep secret the parts you actually need (scripts, thresholds, curation pipeline).

### Estimated patent cost envelope

| Line item | Cost | When |
|---|---|---|
| US provisional application | $2k–3.5k | Now |
| Non-provisional conversion (if needed) | $5k–10k | Month 11 decision |
| PCT international (if needed) | $3k–5k base + per-country | Month 11 decision |
| **Now-budget** | **~$3k** | |
| **Maximum 12-month budget** | **~$13k–18k** | If you go full PCT |

---

## Part 4 — Freedom-to-Operate (FTO)

FTO is what protects you from **getting sued after launch**. It's separate from your own patent filings — even if you have a patent, you can still infringe someone else's.

For a healthtech product entering the cough-AI space, FTO is **not optional**. It's the most underrated $5k a startup can spend.

### Specific portfolios to clear

| Portfolio | Risk | Why |
|---|---|---|
| **ResApp Health (now Pfizer)** | 🔴 high | Adult-cough patents acquired for AUD $179M. Pediatric carve-out is *probably* defensible (their claims focus on adult populations) but must be confirmed in writing. |
| **Hyfe** | 🟡 medium | Chronic-cough monitoring. Less direct overlap (their use case is at-home long-term tracking, not acute pediatric triage) but watch for broad audio-fingerprint claims. |
| **Eko Health** | 🟡 medium | Different sensor (their proprietary stethoscope vs. our smartphone microphone), but acoustic-AI claims could brush against ours. |
| **Babylon Health** | 🟡 medium | WhatsApp/chatbot medical triage flow. Our caregiver→audio→reply→escalate flow could read on theirs. |
| **Ada Health** | 🟡 medium | Same as Babylon; symptomatic triage via chat. |
| **Cohort.ai** | 🟢 lower | Smaller portfolio, likely narrow claims. |

### What the FTO opinion gives you

A written legal opinion ($3k–5k) stating, for each major portfolio:
- "**Cleared**" — our product doesn't read on any active claim.
- "**Cleared with design-around**" — minor product modifications recommended (e.g., change a specific step in our flow).
- "**Risk**" — specific patent X claim Y might read; recommend license discussion or product change before launch.

Without this, you launch into a category with Pfizer-scale incumbents and *hope* they don't notice. With it, you have an opinion-of-counsel defense if you're ever sued — which downgrades willful-infringement (treble damages) to ordinary infringement at most.

**Do this before any commercial launch in the US.** Pre-revenue pilots in Bangladesh are lower risk (US patents only enforceable in US), but the moment you take US customers or US partners, the clock starts.

---

## The 12-month checklist

| When | Action | Cost | Owner |
|---|---|---|---|
| Week 0 | Hire IP attorney (BD + US capable, or coordinate two) | $0 retainer | You |
| Week 1 | Trademark clearance opinion: Baby Pulmo + Vyana + Respira (one engagement) | $1.5k–2.5k | Attorney |
| Week 2 | Pick final name based on clearance result | — | You |
| Week 2 | File US provisional patent (system claim — rules-gated severity + CHW escalation) | $2k–3.5k | Attorney |
| Week 3 | File BD DPDT trademark (3 classes, intent-to-use) — Madrid base | $200–400 | Attorney |
| Week 4 | File USPTO direct trademark (3 classes, §1(b)) | $1.2k–2.2k | Attorney |
| Week 4 | Set up trade-secret protocol: move stock scripts + thresholds to private repo, NDAs in place | $0 | You |
| Month 1 | Defensive publication: arxiv preprint + Medium post of architecture | $0 | You |
| Month 6 | File Madrid Protocol designations (EU, IN, ID, NG, PH, PK — 3 classes each) | $3.5k–5.5k | Attorney |
| Month 6–24 | Respond to USPTO + national office actions as they arrive | $500–2k each | Attorney |
| Month 9 | FTO opinion before any US commercial launch | $3k–5k | Attorney |
| Month 11 | Decide: convert provisional → non-provisional / PCT / let lapse | $0–10k | You + Attorney |
| **Total in first 12 months** | | **~$11.5k–19k** | |

Comfortably inside the $10k–$50k envelope. Leaves room for additional jurisdictions, a non-provisional conversion, or a second FTO refresh after a product pivot.

---

## What you do next (this week)

1. **Tonight (free, 30 min):** Run a DIY USPTO TESS search for "Baby Pulmo", "Pulmo", "Baby Lung". If anything in class 9, 10, or 44 turns up identical, you've saved $2k by ruling Baby Pulmo out before the attorney call.
2. **This week:** Get 2–3 IP attorney quotes. Recommended profile — a firm with both **Bangladesh trademark** and **US healthcare IP** experience. Ask for a clearance opinion on three names (Baby Pulmo, Vyana, Respira) as a fixed-fee package — most firms will do this for $1.5–2.5k.
3. **Next week:** Move the clinician-vetted Bangla scripts and the severity threshold values from the public repo to a private repo *now* — every day they sit public erodes future trade-secret protection.
4. **Within 2 weeks:** Once clearance is back, file BD DPDT + USPTO + US provisional together. The clock starts when the first one is filed.

## What this strategy deliberately does NOT do

- **No Bangladesh patent filing.** Weak enforcement, expensive, wrong jurisdiction for the competitive landscape.
- **No broad algorithm patent claims.** They'll be rejected and waste the filing fees.
- **No EU trademark direct filing.** Use Madrid designation instead — single filing, multiple countries, cheaper.
- **No design patents on the UI.** WhatsApp UI; we don't control the design surface anyway.
- **No attorney recommendation by name.** Hire someone you've checked references for. Healthcare IP is specialized; don't use a generalist.
