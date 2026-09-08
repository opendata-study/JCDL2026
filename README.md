# JCDL2026

Classification prompts, coding manual, coverage-calculation formulas, and full
evaluation metrics used in:

Hiroyuki Tsunoda, Yuan Sun, Masaki Nishizawa, Xiaomin Liu, Kou Amano, and Shuntaro Kawamura.
2026. *Research Data-Sharing Practices Through the Lens of Data Availability Statements*.
In Proceedings of the 2026 ACM/IEEE Joint Conference on Digital Libraries (JCDL '26).

## Purpose of This Repository
This repository ensures:
- Transparency of the LLM-based DAS classification workflow
- Reproducibility of the seven-category DAS classification framework
- Auditability of model prompts and decision criteria
- Verification of the ensemble evaluation metrics reported in the paper

## Study Overview
**Data Source**: PubMed Central (PMC) Open Access Subset, matched to Web of Science
Core Collection via DOI.
**Sample**: 653,490 articles published 2010–2025 across ten major open-access journals.
**Classification**: Data Availability Statements (DASs) classified into seven categories
(F, M, P, R, C, A, N) using three generative AI models (DeepSeek-V3.2, GPT-5.4,
Mistral-Large-3), aggregated via majority-vote and Random Forest ensembles.

## Repository Structure

### `prompts/`
- `category_prompt.md` — Full classification prompt used with all three LLMs, including
  the evidentiary-data definition, public-repository definition, GitHub/data-journal
  edge-case handling, and the F > M > P > R > C > A > N priority rule.

### `coding-manual/`
- `category_definitions.md` — Full operational definitions for each of the seven DAS
  categories, extending the summary in Table 1 of the paper.

### `formulas/`
- `coverage_calculation.md` — Formulas for the dataset-coverage proportions (Included
  Articles, Unmatched DAS Articles, Articles Without DAS) described in Section 2.2.

### `evaluation/`
- `classification_metrics.csv` — Category-level precision, recall, and F1-scores for
  each model and the ensemble methods.
- `category_agreement.csv`, `category_recall.csv`, `category_precision.csv` — Per-category
  agreement statistics against human annotation.
- `confusion_matrix.csv` — Human vs. majority-vote confusion matrix.
- `cross_validation_results.csv` — 5-fold cross-validation and Leave-One-Journal-Out
  (LOJO) results.

## Human Validation
A manually annotated reference dataset of 1,200 DASs (120 stratified per journal) was
used as the evaluation standard. Full agreement statistics, Cohen's κ, and confusion
matrices are provided in `evaluation/`.

## Reproducibility and Transparency
- Prompts are provided verbatim to enable independent replication.
- All evaluation outputs are archived as generated at the time of analysis.
- Because generative AI systems evolve over time, archived outputs and metrics ensure
  reproducibility independent of future model updates.

## Data Source and Licensing
Citation counts were obtained from the Web of Science Core Collection. Due to licensing
restrictions, full Web of Science records are not redistributed here; only DAS category
labels, derived variables, prompts, and classification/evaluation outputs are included.
Users are responsible for complying with applicable database licensing agreements when
obtaining the underlying Web of Science data.

## Citation
If you use this repository, please cite the paper above.

## Contact
Hiroyuki Tsunoda, The University of Tokyo — hiroyuki-tsunoda@g.ecc.u-tokyo.ac.jp
