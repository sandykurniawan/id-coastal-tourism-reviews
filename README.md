# ID-CoastSent Dataset: Indonesian Coastal Tourism Review Dataset

## Overview
This repository provides **ID-CoastSent**, a rigorously annotated sentiment analysis dataset composed of Indonesian coastal tourism reviews. The dataset contains **21,779 clean reviews**, categorized into three sentiment classes: **Positive**, **Negative**, and **Neutral**. 

To support advanced Natural Language Processing (NLP) research—such as model robustness and uncertainty handling—every review was independently evaluated by three human annotators. The dataset is provided in two distinct training variations (High-Confidence/All Agree vs. Real-World/Majority Vote) to facilitate comparative AI studies.

## UN Sustainable Development Goal 9 (SDG 9) Alignment
This dataset was developed to directly support **UN SDG 9: Industry, Innovation and Infrastructure**. 

Coastal tourism is a vital economic driver in Indonesia, but local governments and businesses often lack automated, data-driven feedback loops to monitor public sentiment regarding facilities, safety, and accessibility. By providing high-quality, domain-specific infrastructure for AI researchers, this dataset accelerates the development of automated NLP tools. These tools allow policymakers to rapidly process unstructured public feedback, leading to more resilient tourism infrastructure, inclusive industrialization, and targeted local innovations.

## Annotation Quality & Inter-Annotator Agreement (IAA)
To ensure the reliability of the dataset, inter-annotator agreement was measured across all 21,779 valid reviews prior to partitioning. 

*   **Fleiss' Kappa Score:** `0.7096`
*   **Interpretation:** Substantial agreement

An analysis of individual annotator distributions reveals consistent overall behaviors, with slight natural variations in how ambiguous/neutral reviews were handled. Providing both unanimous and majority-vote data splits allows researchers to explicitly study this human subjectivity.

| Annotator | Positive | Negative | Neutral |
| :--- | :--- | :--- | :--- |
| **Annotator 1** | 8,339 (38.3%) | 8,679 (39.9%) | 4,761 (21.9%) |
| **Annotator 2** | 7,878 (36.2%) | 8,129 (37.3%) | 5,772 (26.5%) |
| **Annotator 3** | 9,719 (44.6%) | 9,476 (43.5%) | 2,584 (11.9%) |

## Repository Structure

```text
📁 dataset-root/
│
├── 📂 data/
│   ├── train_all_agree.csv        # High-confidence training set (unanimous agreement)
│   ├── train_majority_vote.csv    # Real-world training set (2/3 annotator agreement)
│   ├── test_set.csv               # Fixed testing set (300 rows, strictly balanced)
│   └── full_dataset_clean.csv     # Unsplit dataset with all original metadata
│
└── README.md
```

## Data Splits & Methodological Design

To prevent data leakage and provide a standardized benchmark, a strictly balanced testing set was extracted *before* the training data was partitioned. 

1. **`test_set.csv` (300 rows):** The gold-standard evaluation set. Contains exactly 100 positive, 100 negative, and 100 neutral reviews sampled strictly from the unanimous agreement pool.
2. **`train_all_agree.csv` (15,527 rows):** The high-confidence training set. Contains only reviews where all three annotators were in absolute agreement. 
3. **`train_majority_vote.csv` (21,235 rows):** The broader training set containing all valid reviews where at least two annotators agreed on the sentiment, representing a noisier, real-world distribution. *Note: To strictly prevent data leakage, the 300 reviews from the evaluation set have been completely excluded from this file.*
4. **`full_dataset_clean.csv` (21,779 rows):** The complete dataset prior to splitting, providing individual annotator votes (`Ann 1`, `Ann 2`, `Ann 3`) for researchers interested in custom cross-validation, label smoothing, or annotator disagreement studies. *This file includes the 244 highly divergent reviews (3-way ties) that were excluded from the majority vote training set.*

## Data Dictionary
All training and testing CSVs have been standardized to use `sentiment` as the target label column for seamless machine learning pipeline integration.

| Column | Type | Description |
| :--- | :--- | :--- |
| `number_id` | Integer | Unique identifier for the review. |
| `name` | String | The name of the coastal tourism destination/attraction. |
| `province` | String | The Indonesian province where the coastal destination is located. |
| `published_at_date` | Date | The original publication date of the review. |
| `review_text` | String | The raw text of the review in Indonesian. |
| `rating` | Integer | The original numerical rating (e.g., 1-5 stars) provided by the user. |
| `Ann 1`, `Ann 2`, `Ann 3` | String | Individual sentiment labels assigned by the three human annotators. |
| `sentiment` | String | The final aggregated label (`positive`, `negative`, `neutral`) used for model training/testing. |

## License
This dataset is distributed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. You are free to share and adapt the material for any purpose, even commercially, as long as appropriate credit is given to the original authors.
