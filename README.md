# Machine Learning for Malicious URL Classification

A supervised machine-learning project that classifies URLs using the ISCX-URL2016 dataset and pre-engineered numerical URL features.

## Problem

Malicious URLs are commonly associated with phishing, malware distribution, spam and defacement. This project studies a multi-class classification approach using structural and statistical URL features rather than raw URL strings.

## Dataset

- **Dataset:** ISCX-URL2016
- **Samples:** approximately 26,953 (as documented in the experiment)
- **Features:** 72 numerical features
- **Target column:** `URL_Type_obf_Type`
- **Classes:** benign, phishing, malware, defacement and spam

The repository includes the notebook, a CSV data file, model artefacts and figures. Review the dataset's original terms and citation requirements before redistribution.

## Methodology

1. Inspect the dataset and target distribution.
2. Handle missing and infinite values and examine extreme values.
3. Remove low-variance features.
4. Rank features using XGBoost feature importance and investigate a top-40 subset.
5. Compare Logistic Regression, Random Forest and XGBoost.
6. Use stratified splitting and randomized hyperparameter search.
7. Evaluate with accuracy, precision, recall, F1-score, ROC-AUC and false-positive rate.

## Reported experiment results

The existing project report records the following results for its selected run:

| Metric | Reported value |
|---|---:|
| Accuracy | 97.18% |
| Weighted F1-score | 97.16% |
| ROC-AUC | 0.9983 |
| Mean false-positive rate | 0.75% |

These are the results documented by the project, not a guarantee of performance on new or live URLs. In particular, the notebook notes weaker malware recall (approximately 70%), which deserves focused error analysis.

## Run

Install the core dependencies:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib seaborn joblib jupyter
```

Then launch:

```bash
jupyter notebook malicious_url_detection.ipynb
```

Check the notebook's data and model paths before running. The CSV in this repository is approximately 11 MB.

## Important limitations

- The model consumes pre-engineered numerical features, not raw URL strings.
- A production system would need a reliable and safe feature-extraction pipeline.
- Dataset-level results may not generalize to new campaigns, domains or temporal shifts.
- Malware recall is a known weakness in the reported experiment.
- Evaluation should guard against duplicate records and train/test leakage.

## Further work

- Add raw-URL feature extraction and a documented inference API.
- Use temporal or domain-separated evaluation to test generalization.
- Report per-class precision/recall and a confusion matrix.
- Investigate class imbalance and malware false negatives.
- Add reproducible environment and data-version information.

## Tech stack

Python · Pandas · scikit-learn · XGBoost · Matplotlib · Seaborn · Jupyter

## License

No license is currently specified. Contact the repository owner before reuse.
