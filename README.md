# Fraud Detection with Autoencoders and Variational Autoencoders

An academic machine-learning project on reconstruction-based anomaly detection
for highly imbalanced card-transaction data. It compares a PCA baseline, a
conventional autoencoder, and a variational autoencoder (VAE).

> **Data note:** the transaction dataset is not included in this repository.
> Its redistribution rights were not established during the project audit.

## Project at a glance

Fraud detection is an imbalanced-learning problem: a model can show strong
aggregate performance while still creating many false alerts. This Master's
project studies that trade-off through anomaly detection; it is not a production
fraud-detection system.

The original workflow covers exploratory analysis, preprocessing, PCA,
conventional autoencoder and VAE experiments, reconstruction-MSE scoring, a
threshold at the 95th percentile of training reconstruction error, and ROC-AUC,
precision, recall, specificity, confusion matrices, and error distributions.

## Historical reported results

The following are **results reported in the original project**, not values
reproduced while preparing this documentation.

| Experiment | AUC | Precision | Recall | Specificity | Source |
|---|---:|---:|---:|---:|---|
| Conventional autoencoder, normal-only test | 0.95 | 11.77% | 86.65% | 94.95% | `report/master-thesis-es.pdf`, p. 37; `notebooks/final/fraud-detection-analysis.ipynb`, cells 91-92 |
| VAE, normal-only test | 0.92 | 10.06% | 71.49% | 95.03% | `report/master-thesis-es.pdf`, p. 38; `notebooks/final/fraud-detection-analysis.ipynb`, cells 100-101 |
| Conventional autoencoder, SMOTE-balanced test | 0.94 | 2.30% | 82.83% | 93.86% | `report/master-thesis-es.pdf`, p. 48; `notebooks/final/fraud-detection-analysis.ipynb`, cells 108-116 |
| VAE, SMOTE-balanced test | 0.93 | 1.98% | 71.72% | 93.783% | `report/master-thesis-es.pdf`, p. 49; `notebooks/final/fraud-detection-analysis.ipynb`, cells 117-125 |

Low precision remains an important false-positive limitation. The PCA
normal-only test is not a headline result because the dissertation reports AUC
0.48 while the notebook narrative reports 0.52. See [results and limitations](docs/results-and-limitations.md).

## Technologies

Python, pandas, NumPy, scikit-learn, TensorFlow/Keras, imbalanced-learn,
Matplotlib, and Seaborn. Source: `notebooks/final/fraud-detection-analysis.ipynb`, cell 2.

## Repository contents

- [Final project notebook](notebooks/final/fraud-detection-analysis.ipynb) - primary implementation and analysis record.
- [Experimental notebook](notebooks/experiments/autoencoder-experiments.ipynb) - earlier experiments and tests.
- [Master's dissertation (Spanish)](report/master-thesis-es.pdf) - primary historical-results source.
- [Project overview](docs/project-overview.md)
- [Data and preprocessing](docs/data-and-preprocessing.md)
- [Models and experiments](docs/models-and-experiments.md)
- [Results and limitations](docs/results-and-limitations.md)

## Important limitations

No real data are included or redistributed. The normal-only and SMOTE-balanced
routes are separate experiment families. The reported metrics are historical,
not independently reproduced release results.
## Master's dissertation

The Master's dissertation PDF is © 2026 Jandro Gil. It is provided for
portfolio and academic-review purposes. Reuse or redistribution is not
authorised unless explicitly permitted by the author.

## Licence

The source code and code-related documentation in this repository are
available under the [MIT License](LICENSE).

The original transaction dataset is not included and remains subject to the
terms established by its original provider.

The Master's dissertation PDF and any third-party names, logos or materials
are not covered by the MIT Licence unless explicitly stated otherwise.
