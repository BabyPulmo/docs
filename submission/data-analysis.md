# Baby Pulmo — Coswara Dataset Analysis

## Source Dataset

Primary dataset: **Coswara** (IISc Bangalore)  
Repository: <https://github.com/iiscleap/Coswara-Data>

Purpose in Baby Pulmo:
- Respiratory acoustic pretraining
- South Asian cough representation learning
- Initial Wav2Vec2 fine-tuning support

---

# Dataset Overview

| Metric | Value |
|---|---:|
| Total metadata rows | 2,746 |
| Total audio recordings (est.) | 24,714 |
| Recording types | Cough (deep/shallow), Breathing (fast/slow), Vowels, Counting |
| Primary language region | South Asia |
| Collection period | 2020-04-13 to 2022-02-24 |

---

# Class / Symptom Distribution

> **Note:** Coswara is a COVID-era dataset. `pneumonia` and `asthma` exist as
> pre-existing condition flags. `bronchiolitis` and `croup` are **not labeled**.

| Label / Condition | Count | % of total |
|---|---:|---:|
| Healthy | 1,433 | 52.2% |
| COVID-positive (mild + moderate + asymp) | 681 | 24.8% |
| Exposed (no resp illness) | 248 | 9.0% |
| Recovered (full) | 146 | 5.3% |
| Resp illness not identified | 157 | 5.7% |
| Under validation | 81 | 2.9% |
| Pneumonia (pre-existing flag) | 45 | 1.6% |
| Asthma (pre-existing flag) | 134 | 4.9% |
| Cough (symptom flag) | 652 | 23.7% |
| Cold (symptom flag) | 488 | 17.8% |
| Fever | 406 | 14.8% |
| Breathing difficulty (bd) | 211 | 7.7% |
| Bronchiolitis | Not labeled | — |
| Croup | Not labeled | — |

---

# Sex Distribution

| Sex | Count | Percentage |
|---|---:|---:|
| Male | 1,900 | 69.2% |
| Female | 844 | 30.7% |
| Other / Unknown | 2 | 0.1% |

---

# Age Distribution

| Age Group | Count | % |
|---|---:|---:|
| 0-5 | 5 | 0.2% |
| 6-17 | 54 | 2.0% |
| 18-40 | 1,891 | 68.9% |
| 41-60 | 631 | 23.0% |
| 60+ | 165 | 6.0% |

Median age: **31.0** | Mean age: **35.2**

> Dataset is heavily adult-skewed. Only 59 participants are under 18.
> Children under 5 = only **5 participants** — critical gap for Baby Pulmo.

---

# Geographic / Language Origin

| Country | Count | % |
|---|---:|---:|
| India | 2,515 | 91.6% |
| United States | 87 | 3.2% |
| France | 19 | 0.7% |
| Canada | 15 | 0.5% |
| United Kingdom | 8 | 0.3% |
| Germany | 7 | 0.3% |
| Netherlands The | 7 | 0.3% |
| China | 6 | 0.2% |
| Japan | 5 | 0.2% |
| Bahrain | 5 | 0.2% |

> 91.6% of participants are from India — more relevant for South Asian
> deployment than Western datasets. However, **not** Bangladesh-specific.

---

# Audio Quality

> Quality labels (0/1/2) are stored in the `annotations/` folder separately
> from `combined_data.csv` and were not merged in this analysis.

| Quality | Description |
|---|---|
| 2 | Excellent |
| 1 | Good |
| 0 | Bad |

_Run annotation merge to get per-participant quality counts._

---

# Audio Duration & Sample Rate

| Metric | Value |
|---|---:|
| Dominant sample rate | 44,100 Hz (typical for Coswara) |
| Median duration | Requires `librosa` audio scan |
| Mean duration | Requires `librosa` audio scan |
| SNR metadata | Not available in public release |

---

# Key Limitations

## 1. COVID-era collection bias
Collected 2020–2022, over-representing COVID-related respiratory patterns.

## 2. Adult-skewed demographics
Only **59** participants under 18 out of **2,746** total.
Children under 5 = only **5** — severely underrepresented for Baby Pulmo's target population.

## 3. Incomplete pediatric disease labels

| Condition | Available? |
|---|---|
| Pneumonia | ✅ Pre-existing flag (not clinically verified) |
| Asthma | ✅ Pre-existing flag |
| Bronchiolitis | ❌ Not labeled |
| Croup | ❌ Not labeled |
| COVID-19 status | ✅ Primary label |

## 4. Not Bangladesh-specific
Requires Bangladeshi pediatric cohort validation, BMRC ethics approval,
and field fine-tuning on local pediatric recordings.

---

# Relevance to Baby Pulmo

Coswara is used for **respiratory acoustic pretraining only**, not standalone diagnosis.

| Benefit | Why it matters |
|---|---|
| Large-scale South Asian audio | Better than Western datasets for BD deployment |
| Diverse cough/breathing patterns | Broad acoustic pretraining signal |
| Publicly accessible (CC BY 4.0) | No licensing barrier |
| Wav2Vec2 compatible | Direct use in feature extraction pipeline |

Baby Pulmo is a **decision-support and triage tool**, not an autonomous diagnostic system.
Future phases will prioritize Bangladeshi pediatric field validation and model recalibration.