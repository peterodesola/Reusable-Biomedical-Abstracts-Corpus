# Reusable-Biomedical-Abstracts-Corpus
## Curated Biomedical Abstracts Metadata & Labels (v1.0)

**Provenance-Verified · Deduplicated · Taxonomy-Standardized**

**Dataset DOI:** [10.5281/zenodo.17229456](https://doi.org/10.5281/zenodo.17229456)  
**Code DOI / Repository:** [10.5281/zenodo.17381916](https://doi.org/10.5281/zenodo.17381916) · [https://github.com/peterodesola/Reusable-Biomedical-Abstracts-Corpus](https://github.com/peterodesola/Reusable-Biomedical-Abstracts-Corpus)  
**License:** CC BY-SA 4.0  
**Contact:** eidreiz01@gmail.com · adegokeaa44@gmail.com · peterodes27@gmail.com

---

## Table of Contents

- [Overview](overview)
- [Dataset Statistics](dataset-statistics)
- [Label Distribution](label-distribution)
- [File Structure](file-structure)
- [Quick Start](quick-start)
- [Provenance](provenance)
- [Intended Use](intended-use)
- [Limitations](limitations)
- [License](license)
- [Citation](citation)
- [Acknowledgments](acknowledgments)
- [Changelog](changelog)

---

## Overview

This release provides **metadata**, **disease labels**, and **deduplication keys** for a curated biomedical abstracts corpus derived from a public community dataset.

✅ **Duplicates and near-duplicates removed**  
✅ **Deprecated/generalized labels replaced**  
✅ **Provenance tracked via PubMed IDs**  

> **Note:** Abstract text is *not redistributed* due to copyright restrictions. Use included scripts to fetch texts from licensed/open sources (e.g., PubMed Central Open Access).

---

## Dataset Statistics

| Stage                                  | Count  |
|----------------------------------------|--------|
| Source Total                           | 14,438 |
| Duplicates Removed                     | 6,140  |
| Ultra-short Removed (< threshold)      | 4      |
| After Deduplication & Short Filtering  | 8,294  |
| **Final Records (v1.0)**               | **5,901** |

---

## Label Distribution

| Label Category              | Count |
|-----------------------------|------:|
| Neoplasms                   | 2,193 |
| Cardiovascular Diseases     | 1,960 |
| Nervous System Diseases     | 1,049 |
| Digestive System Diseases   | 699   |

---

## File Structure

```

data/
├─ metadata_labels.csv       # pmid, title, journal, year, disease_label, source_id, source_url, dedup_key, [split], notes
└─ label_taxonomy.csv        # final label set + definitions

docs/
├─ datacard.md               # detailed documentation
└─ README.md                 # quick usage notes

result/
├─ tables/*.csv              # summary tables (e.g., PubMed spot-check results)
└─ plots/*.png               # diagnostic figures

```

---

## Quick Start

```bash
# 1. Create environment
python3 -m venv venv
source venv/bin/activate

# 2. Clone repository & install dependencies
git clone https://github.com/peterodesola/Reusable-Biomedical-Abstracts-Corpus
cd Reusable-Biomedical-Abstracts-Corpus
pip install -r requirements.txt

# 3. Regenerate curated CSV (if license permits)
make regenerate
# or
python scripts/run_pipeline.py --config configs/default.yaml

# 4. (Optional) Fetch abstract texts
python scripts/fetch_pubmed_text.py --pmids data/metadata_labels.csv --out data/pubmed_text.jsonl
````

⚠️ **Fetch only from licensed/open sources. Respect PubMed API rate limits and terms.**

---

## Provenance

A **random 100-record sample** was checked via **NCBI E-utilities (PubMed API)**. PMIDs were recorded when matches were found.

See: `result/tables/pubmed_spotcheck_summary.csv`

---

## Intended Use

* **Supervised / Weakly-Supervised Classification Benchmarks**
* **Curriculum Use for Demonstrating Curation & Provenance**
* **Label Taxonomy Design / Comparisons**

---

## Limitations

* Full abstracts may be **copyrighted** and are **not redistributed**.
* Label taxonomy favours **separability for classification**; domain-specific alternatives may be preferable for clinical use.
* PubMed matching is **sample-based**, not exhaustive.

---

## License

This dataset is released under **CC BY-SA 4.0**.

> You must **attribute both the original creators and this curated release**, and **share derivatives under the same license**.

---

## Citation

```
Idris Babalola, Adewale Alex Adegoke, Peter Adebayo Odesola. (2025).
Curated Biomedical Abstracts Metadata & Labels - Provenance-Verified, Deduplicated (v1.0) [Data set].
Zenodo. https://doi.org/10.5281/zenodo.17229456
```

---

## Acknowledgments

Derived from the original dataset by **[Original Author/Team]**
Original License: CC BY-SA 3.0
Source: [https://www.kaggle.com/datasets/chaitanyakck/medical-text](https://www.kaggle.com/datasets/chaitanyakck/medical-text)

---

## Changelog

| Version  | Date       | Notes                                                                                                                                       |
| -------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **v1.0** | 2025-10-17 | Initial public release. Dedup = 6,140; ultra-short removed = 4; final records = 5,901; four-class taxonomy; PMIDs recorded where available. |


```
