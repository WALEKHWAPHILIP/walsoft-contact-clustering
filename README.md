## Live site (GitHub Pages)
https://walekhwaphilip.github.io/walsoft-contact-clustering/

# Walsoft Contact-Level Clustering (Unsupervised Segmentation)

**Business objective:** Segment contacts into actionable behavioral groups to support outreach planning, CRM prioritization, and relationship management.

This repo demonstrates a **privacy-first, decision-driven segmentation pipeline** built on real call-behaviour logs, with **robust preprocessing**, **K selection**, **cluster interpretation**, and **stability checks** (ARI + sensitivity tests).

---

## Why this matters (value to a company)

**Who uses this:** operations/sales teams, founders, and analysts.  
**What changes after deploying:** outreach becomes segment-driven (cadence + priority + risk flags), not ad hoc.  
**Why unsupervised:** there are no reliable labels for “good contact” vs “bad contact”, so clustering provides structure from behavior.

### Practical outcomes
- Identify “core active” high-touch relationships vs dormant contacts
- Detect rare-but-deep conversations (high-value, high-context relationships)
- Deliver a reproducible pipeline from messy logs → stable segments
- Provide interpretable segment cards + robustness evidence (not just plots)

---

## Data source

Direct CSV source (identifiers anonymized per provenance):

https://learn.walsoftcomputers.com/machine_learning/walsoft_phonecall/original_dataset_with_instructions/walsoft_semi_categorized_phone_dataset.csv

> Note: The repository does **not** commit the dataset. The analysis loads the dataset from the URL at runtime.

---

## Privacy / anonymization

The dataset identifiers are anonymized per provenance. Even so, this repo avoids committing data and avoids exporting identifier-like fields by default. A stable hashed `contact_id` is used to keep outputs consistent without exposing raw identifiers.

---

## What’s inside

Primary artifact:

- **Quarto analysis chapter:** `walsoft_contact_segmentation.qmd` (runs top-to-bottom)

Pipeline stages:

1. Audit (schema, missingness, duplicates, date range)
2. Contact-level feature engineering (volume/duration/recency/timing + category mix for interpretation)
3. Preprocessing (median imputation + RobustScaler, heavy-tail control)
4. K selection (inertia + silhouette + Davies–Bouldin)
5. Fit + interpret (cluster cards, segment naming, actions)
6. Robustness (seed stability via ARI + drop-one-block sensitivity)
7. PCA visualization (interpretation only)
8. Findings + limitations + “What decisions can a business make with these clusters?”

---

## Quickstart (Windows CMD)

### 1) Create environment + install dependencies
```bat
python -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt
````

### 2) Render the site locally

```bat
quarto render
```

### 3) Open the output

```bat
start _site\index.html
```

---

## Outputs (generated)

* The rendered site is produced under `_site/` (ignored on `main`, deployed via `gh-pages`).
* Optional CSV exports are **OFF by default** (see `SAVE_FILES = False` inside the Quarto chapter).

---

## Reproducibility notes

* The pipeline is designed to be stable and auditable:

  * robust scaling for heavy-tailed behaviour
  * K selection using multiple metrics
  * stability checks using ARI across seeds
  * sensitivity checks by dropping feature blocks

---

## License and citation

* **License:** MIT (see `LICENSE`)
* **How to cite:** see `CITATION.cff`

---

## Author

**Philip Tambiti Leo Walekhwa**
*Data Scientist* | *Business Strategist* | *Entrepreneur* | *Educator*
Profile: [https://ai.walsoftcomputers.com/](https://ai.walsoftcomputers.com/)

````

