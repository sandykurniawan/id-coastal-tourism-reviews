# id-coastal-tourism-reviews

Annotated Indonesian **coastal tourism** reviews (Google Maps) — cleaned, anonymized, and **triple-annotated** for sentiment analysis. Includes per-annotator labels, a **majority-vote** subset, and an **all-agree** subset.

> **At a glance:** 3 sentiment classes (*negative/neutral/positive*). Three-way agreement **72.67%** on **n = 21,785** fully labeled items. Pairwise Cohen’s κ: **0.767 / 0.709 / 0.656**.

---

## Repository structure

ID-Coastal Tourism Review Dataset/
├── 1. Annotated Dataset/ # Full table with per-annotator labels
├── 2. Majority Vote Based Dataset/ # Subset: majority_sentiment (≥2 of 3)
└── 3. All Agree Based Dataset/ # Subset: all three raters identical


**Core columns**

- `number_id`, `place_name`, `rating`, `date`, `review`, `clean_review`  
- `sent_ann1`, `sent_ann2`, `sent_ann3`  
- `major_sentiment`, `all_agree_sentiment`  
(Label set: `{negative, neutral, positive}`; PII removed/anonymized.)

---

## Intended uses

- Indonesian-language sentiment classification & benchmarking  
- Tourism analytics (destination perceptions, complaints, satisfaction)  
- Coastal sustainability & socio-environmental studies  
- Domain adaptation / error analysis for Indonesian NLP in tourism contexts

## Ethics & terms

Reviews originate from **Google Maps**. This release contains text and derived annotations; user identifiers are anonymized.  
Please respect platform attribution and applicable terms in any downstream use.

## Citation

If you use this dataset, please cite:

Sandy (2025). *Indonesian Coastal Tourism Review Dataset (id-coastal-tourism-reviews)*.  
GitHub repository. https://github.com/sandykurniawan/id-coastal-tourism-reviews

**BibTeX**
```bibtex
@dataset{id_coastal_tourism_reviews_2025,
  title   = {Indonesian Coastal Tourism Review Dataset (id-coastal-tourism-reviews)},
  author  = {Sandy},
  year    = {2025},
  url     = {https://github.com/sandykurniawan/id-coastal-tourism-reviews}
}
