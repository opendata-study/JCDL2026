# JCDL2026

Classification prompts, coding manual, coverage-calculation formulas, and evaluation
results used in:

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
**Sample**: 653,490 records (653,356 unique PMCIDs) published 2010–2025 across ten major open-access
journals; 134 PMCIDs are represented by two Web of Science records (see `labels/DAS_labels.csv`).
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
  Articles, Excluded DAS Articles, Articles Without DAS) described in Section 2.2.

### `evaluation/`
All files are computed from the 1,200 human-annotated DASs (rows = human label, columns = prediction).
- `classification_metrics.csv` — Per-category precision, recall and F1 (with 95% Wilson / bootstrap CIs and counts)
  for each method: DeepSeek-V3.2, GPT-5.4, Mistral-Large-3, majority vote, Random Forest (5-fold CV) and
  Random Forest (LOJO).
- `classification_summary.csv` — Per-method accuracy, Cohen's kappa, and macro / weighted precision, recall and F1.
- `category_agreement.csv`, `category_recall.csv`, `category_precision.csv` — Per-category agreement statistics
  against human annotation (agreement = recall; recall / precision are for the majority vote).
- `confusion_matrix.csv` — Human vs. majority-vote confusion matrix (`human_label` = rows, `pred_*` = columns).
- `cross_validation_results.csv` — Random Forest 5-fold cross-validation and Leave-One-Journal-Out (LOJO) results
  (pooled predictions, mean over held-out journals, and each held-out journal).
- `verification_report.txt` — Comparison of the recomputed values with those reported in the paper.

### `labels/`
- `DAS_labels.csv` — Labels (PMCID, journal, analysis_year, ds32, gpt5, mil3, DAS) for the 653,490 analysed
  records. Web of Science data (e.g. citation counts) are not included.
  The file contains 653,490 rows (653,356 unique PMCIDs). 134 PMCIDs appear in two rows because more than one
  Web of Science record was matched to the same article; the labels are identical in all such cases (the
  citation counts, which are not distributed here, were identical for 49 of them and different for 85).
  The analyses in the paper use all 653,490 rows (keeping a single record per PMCID changed no DAS coefficient
  of the primary model by more than 0.001).

## Human Validation
A manually annotated reference dataset of 1,200 DASs (120 stratified per journal) was
used as the evaluation standard. Full agreement statistics, Cohen's κ, and confusion
matrices are provided in `evaluation/`.

## Ensemble Details
- **Majority vote**: the label chosen by at least two of the three models. If all three models disagree,
  the DeepSeek-V3.2 label is used (tie-break = first model).
- **Random Forest**: 500 trees, `random_state = 42`; the three model labels are integer-encoded per column
  (alphabetical order of labels) and used as features; target = human label. Evaluated with stratified
  5-fold CV (shuffled) and Leave-One-Journal-Out.
- `DAS` in `DAS_labels.csv` is the final category assigned to each article, i.e. the prediction of the
  Random Forest ensemble selected in the paper; it differs from the majority vote in about 6% of the records.
  `ds32`, `gpt5` and `mil3` are the raw labels of DeepSeek-V3.2, GPT-5.4 and Mistral-Large-3.

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
