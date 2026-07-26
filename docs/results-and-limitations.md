# Results and Limitations

## Status of these results

All metrics below are **results reported in the original project**. They were
not reproduced, retrained, or reevaluated while preparing this documentation.

| Experiment and split | Threshold / mean MSE where reported | AUC | Precision | Recall | Specificity | Original source |
|---|---:|---:|---:|---:|---:|---|
| PCA, normal-only test | Not reported in the dissertation table | 0.48 | 0.74% | 4.98% | 94.83% | `report/master-thesis-fraud-detection-es.pdf`, p. 36; `Trabajo_Final.ipynb`, cells 80-82 |
| Autoencoder, normal-only validation | 0.00364 / 0.0017 | 0.96 | 1.97% | 92.00% | 94.97% | `report/master-thesis-fraud-detection-es.pdf`, p. 32; `Trabajo_Final.ipynb`, cells 84-90 |
| Autoencoder, normal-only test | Not reported in the source table | 0.95 | 11.77% | 86.65% | 94.95% | `report/master-thesis-fraud-detection-es.pdf`, p. 37; `Trabajo_Final.ipynb`, cells 91-92 |
| VAE, normal-only validation | 0.017 / 0.0107 | 0.93 | 1.63% | 80.00% | 94.69% | `report/master-thesis-fraud-detection-es.pdf`, p. 35; `Trabajo_Final.ipynb`, cells 93-99 |
| VAE, normal-only test | 0.017 / 0.0109 | 0.92 | 10.06% | 71.49% | 95.03% | `report/master-thesis-fraud-detection-es.pdf`, p. 38; `Trabajo_Final.ipynb`, cells 100-101 |
| PCA, SMOTE-balanced validation | Not reported in the source table | 0.51 | 0.72% | 4.75% | 94.88% | `report/master-thesis-fraud-detection-es.pdf`, p. 47; `Trabajo_Final.ipynb`, cells 105-107 |
| Autoencoder, SMOTE-balanced test | 0.007 / 0.005 | 0.94 | 2.30% | 82.83% | 93.86% | `report/master-thesis-fraud-detection-es.pdf`, p. 48; `Trabajo_Final.ipynb`, cells 108-116 |
| VAE, SMOTE-balanced test | 0.0138 / 0.005 | 0.93 | 1.98% | 71.72% | 93.783% | `report/master-thesis-fraud-detection-es.pdf`, p. 49; `Trabajo_Final.ipynb`, cells 117-125 |

## PCA discrepancy

The dissertation reports normal-only PCA test AUC 0.48; the notebook narrative
reports 0.52. Both values are retained as historical evidence, and this
documentation does not choose one as definitive. Sources: `report/master-thesis-fraud-detection-es.pdf`, p. 36; `Trabajo_Final.ipynb`, cells 80-82.

## Interpretation and limitations

Several reported autoencoder and VAE runs combine high recall and specificity
with low precision. A model can therefore identify many fraud-labelled
observations while still generating many false alerts. Precision, recall,
specificity, threshold method, and AUC must be read together.

Other limitations are unverified data redistribution rights, anonymised
variables, distinct normal-only and SMOTE-balanced designs, stale model-artifact
paths, and the lack of a verified public environment. The repository documents
an academic project and makes no production-readiness claim. Sources:
`Trabajo_Final.ipynb`, cells 25-28, 51-60, and 80-125;
`report/master-thesis-fraud-detection-es.pdf`, pp. 36-49.
