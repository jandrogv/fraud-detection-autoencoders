# Portfolio Publication Audit

## Scope and audit basis

This is a documentation-only audit of the private Master's-dissertation repository. No training, model evaluation, or public release was performed as part of the audit. The 63-page dissertation is the primary source for the reported measurements below; the available notebook is the implementation source. The results should be presented publicly as *reported project results* until rerun from an approved public workflow.

Primary evidence reviewed:

- `Trabajo Final de Master.pdf` (63-page Master's dissertation)
- `Trabajo_Final.ipynb` (126 cells: 60 code and 66 Markdown cells; no standalone `.py` source file was present during this audit)
- `Modelos/` (four Keras HDF5 artifacts and four NumPy history artifacts)
- `creditcard.csv` (present locally but ignored by Git)
- `docs/portfolio/CODEX_AUDIT_PROMPT.md` and `docs/portfolio/PUBLICATION_CONTEXT.md`

## Project overview

The project investigates credit-card-fraud anomaly detection with reconstruction-based models. It compares a 30-component PCA baseline with a conventional autoencoder and a variational autoencoder (VAE). The intended portfolio value is a reproducible case study showing exploratory analysis, preprocessing for severely imbalanced data, reconstruction-error scoring, threshold-based anomaly detection, model comparison, and careful interpretation of false-positive trade-offs.

The dissertation identifies the dataset as a publicly available Kaggle-hosted, anonymised credit-card-fraud dataset from the ULB Machine Learning Group; it does not include the applicable licence or redistribution terms. The notebook reads `creditcard.csv`, converts `Time` to hour-of-day, replaces `Amount` with `log10_amount`, then applies `MinMaxScaler` fit on the training partition. It contains both a normal-only training path and a separate SMOTE-balanced path. Source: `Trabajo Final de Master.pdf`, pp. 4, 9, and 14-18; `Trabajo_Final.ipynb`, cells 20, 26, 28, and 38-42.

For both autoencoder paths, the anomaly score is per-observation reconstruction MSE and the decision threshold is the 95th percentile of training reconstruction MSE. Evaluation produces confusion matrices, precision, recall, specificity, ROC curves, and AUC where implemented. Source: `Trabajo_Final.ipynb`, cells 51-60 and 63-66.

The conventional autoencoder is described as an ELU encoder/decoder with batch normalization, dropout, and a bottleneck; the balanced variant is deeper. The VAE uses a reparameterized latent representation and a custom loss combining reconstruction loss with KL divergence. Source: `Trabajo_Final.ipynb`, cells 68-70, 84, 93, 108, and 117.

## Evidence-backed results

All values below are project-reported values, not values recomputed during this audit.

| Experiment and split | Reported result | Supporting internal source | Reproducibility and publication recommendation |
|---|---|---|---|
| PCA, normal-only test | AUC 0.48; precision 0.74%; recall 4.98%; specificity 94.83% | `Trabajo Final de Master.pdf`, p. 36; `Trabajo_Final.ipynb`, cells 80-82 | Summarise only as the weak baseline. The notebook reports a different normal-only PCA result; resolve this before public use. |
| Autoencoder, normal-only validation | Threshold 0.00364; mean MSE 0.0017; AUC 0.96; precision 1.97%; recall 92.00%; specificity 94.97% | `Trabajo_Final.ipynb`, cells 84-90; `Trabajo Final de Master.pdf`, p. 32 | Recreate charts and evaluation from an approved data route. |
| Autoencoder, normal-only test | AUC 0.95; precision 11.77%; recall 86.65%; specificity 94.95% | `Trabajo_Final.ipynb`, cells 91-92; `Trabajo Final de Master.pdf`, p. 37 | Use only with an explicit alert-volume/false-positive limitation. |
| VAE, normal-only validation | Threshold 0.017; mean MSE 0.0107; AUC 0.93; precision 1.63%; recall 80.00%; specificity 94.69% | `Trabajo_Final.ipynb`, cells 93-99; `Trabajo Final de Master.pdf`, p. 35 | Recreate after resolving model-path and environment gaps. |
| VAE, normal-only test | Threshold 0.017; mean MSE 0.0109; AUC 0.92; precision 10.06%; recall 71.49%; specificity 95.03% | `Trabajo_Final.ipynb`, cells 100-101; `Trabajo Final de Master.pdf`, p. 38 | Summarise as reported, with the same limitation. |
| PCA, SMOTE-balanced validation | AUC 0.51; precision 0.72%; recall 4.75%; specificity 94.88% | `Trabajo_Final.ipynb`, cells 105-107; `Trabajo Final de Master.pdf`, p. 47 | Summarise only as a baseline; do not present as a production candidate. |
| Autoencoder, SMOTE-balanced test | Threshold 0.007; mean MSE 0.005; AUC 0.94; precision 2.3%; recall 82.83%; specificity 93.86% | `Trabajo_Final.ipynb`, cells 108-116; `Trabajo Final de Master.pdf`, p. 48 | Needs methodological explanation and a rerun before a headline claim. |
| VAE, SMOTE-balanced test | Threshold 0.0138; mean MSE 0.005; AUC 0.93; precision 1.98%; recall 71.72%; specificity 93.783% | `Trabajo_Final.ipynb`, cells 117-125; `Trabajo Final de Master.pdf`, p. 49 | Needs methodological explanation and a rerun before a headline claim. |

The saved history artifacts provide additional training evidence: `Modelos/v3_34_hist.npy` contains 933 recorded epochs, `Modelos/v3_38_hist.npy` 3,197, and `Modelos/v2_7_hist.npy` 782. These counts do not fully align with some narrative training limits in the notebook, so they are not recommended as public headline metrics without owner review.

## Portfolio strengths

- A clear, end-to-end anomaly-detection workflow rather than a single model artifact.
- A useful PCA baseline that makes the model comparison credible.
- Explicit reconstruction-error distributions, threshold selection, ROC/AUC, and confusion-matrix evaluation in `Trabajo_Final.ipynb`, cells 50-66.
- Two experimental strategies: normal-only training and an explicitly documented SMOTE-balanced path (`Trabajo_Final.ipynb`, cells 25-28).
- A custom VAE sampling and loss implementation (`Trabajo_Final.ipynb`, cells 68-70).
- Existing chart outputs in the dissertation that can guide a polished English redraw; relevant image-bearing pages include 10-13, 31-38, 42-49, and 61-63 of `Trabajo Final de Master.pdf`.

## Limitations and publication blockers

1. The dissertation identifies Kaggle as the acquisition platform, but the repository contains no dataset licence, canonical source link, redistribution permission, or data card. The real CSV must not be copied to a public repository. `NEEDS OWNER CONFIRMATION`.
2. The notebook expects paths such as `modelos-minmax/...` and root-level model files, whereas the available tracked artifacts are under `Modelos/`; it also references a history filename not present in that directory. This prevents treating the current notebook as a verified public reproduction path. Source: `Trabajo_Final.ipynb`, cells 85, 88, 94, 97, 109, 112, 118, and 121; `Modelos/`.
3. No dependency lockfile, requirements file, environment specification, or public execution instructions exist. Source: repository inventory and `Trabajo_Final.ipynb`, cell 2.
4. The source documentation is predominantly Spanish. An English executive summary and rewritten public narrative are required; the Spanish dissertation should remain private. Source: `Trabajo_Final.ipynb`; `Trabajo Final de Master.pdf`, pp. 4-54.
5. The reported precision values are low despite strong recall/specificity in several experiments. A public README must state the false-positive trade-off and avoid describing the work as a deployable fraud system. Sources: result cells listed above.

## Audit conclusion

The project has strong portfolio potential as an honest, reproducible ML case study, provided the public version is rebuilt from an approved file list. Publish a clean English implementation and synthetic example rather than copying the private CSV, dissertation, binary weights, or notebook wholesale.

Required owner decisions are listed in `docs/portfolio/publication-risk-register.md` and `docs/portfolio/proposed-public-structure.md`.

5. No standalone `.py` file was present when the audit was updated. The available executable implementation is `Trabajo_Final.ipynb`; confirm whether a separate Python source exists before approving a final public file list. `NEEDS OWNER CONFIRMATION`.
