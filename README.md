# Walsoft Contact-Level Clustering (Unsupervised Segmentation)

**Business objective:** Segment contacts into actionable behavioral groups (contact types) to support outreach planning, CRM prioritization, and relationship management.

## Value to a company (why this is useful)
**Who uses this:** operations/sales teams, founders, and analysts.  
**What changes after deploying:** outreach becomes segment-driven (cadence + priority + risk flags), not ad hoc.  
**Why unsupervised:** there are no reliable labels for “good contact” vs “bad contact”, so clustering provides structure from behavior.

## Practical outcomes
- Identify “inner circle” high-touch contacts vs dormant contacts
- Discover rare-but-long conversations (high-value relationships)
- Deliver a reproducible pipeline from messy logs → stable segments
- Provide interpretable cluster profiles + robustness evidence (not just plots)

## Privacy / anonymization
The dataset identifiers are anonymized per provenance. Even so, this repo avoids committing data and avoids exporting identifier-like fields by default. A stable hashed `contact_id` may be used for future-proofing.

## What’s inside
A Quarto chapter (`walsoft_contact_segmentation.qmd`) that runs top-to-bottom:
1. Audit (schema, missingness, duplicates, date range)
2. Contact-level feature engineering (volume/duration/recency/gaps/timing)
3. Preprocessing (imputation + robust scaling)
4. K selection (silhouette + Davies–Bouldin + inertia)
5. Interpretation (cluster profiles + safe examples)
6. Robustness (ARI stability + feature-block sensitivity)
7. PCA visualization (interpretation only)
8. Findings + limitations + “What decisions can a business make with these clusters?”

## How to run (Windows CMD)

### 1) Create environment + install dependencies
```bat
python -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
