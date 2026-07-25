# Visual Assets Plan

## Governing rule

All public visuals are newly generated or redrawn in English. The original
notebook outputs and dissertation figures are evidence and design references,
not assets to copy. A figure may be published only when its data, caption,
experiment label, and reported metric values can be validated against the
identified private source or a clean public rerun.

| Visual asset | Purpose | Supporting private source | Proposed filename | Destination | Treatment | Data sensitivity | Validation requirement | Intended README location |
|---|---|---|---|---|---|---|---|---|
| Class-imbalance overview | Establish the imbalanced-data context without overstating business meaning. | `Trabajo_Final.ipynb`, cells 10-12; `Trabajo Final de Master.pdf`, pp. 10-13 | `class-imbalance.png` | `figures/class-imbalance.png` | `RECREATE` | Use synthetic data or an aggregate, approved rerun only; no real rows. | Confirm labels, aggregate counts, and caption source. | Problem and scope |
| Time-of-day activity overview | Show the original exploratory workflow's temporal aggregation. | `Trabajo_Final.ipynb`, cells 13-15; `Trabajo Final de Master.pdf`, pp. 10-13 | `transaction-time-profile.png` | `figures/transaction-time-profile.png` | `RECREATE` | Synthetic data by default; real-data aggregation requires approved source terms. | Confirm transformation from `Time` to hour-of-day and no exposed records. | Exploratory analysis |
| Amount-transformation overview | Explain the `Amount` to `log10_amount` preprocessing choice. | `Trabajo_Final.ipynb`, cells 16-18; `Trabajo Final de Master.pdf`, pp. 10-13 | `amount-transformation.png` | `figures/amount-transformation.png` | `RECREATE` | Synthetic data by default. | Confirm the transformation and English labels match methodology. | Methodology |
| Conventional autoencoder diagram | Make encoder, bottleneck, decoder, and reconstruction objective clear. | `Trabajo_Final.ipynb`, cells 84 and 108; `Trabajo Final de Master.pdf`, p. 61 | `architecture-autoencoder.svg` | `figures/architecture-autoencoder.svg` | `RECREATE` | No data content. | Technical review against the final public model definition. | Models |
| Variational autoencoder diagram | Explain latent sampling and reconstruction-plus-KL-loss structure. | `Trabajo_Final.ipynb`, cells 68-70, 93, and 117; `Trabajo Final de Master.pdf`, pp. 62-63 | `architecture-vae.svg` | `figures/architecture-vae.svg` | `RECREATE` | No data content. | Technical review against the final public VAE implementation. | Models |
| Training-history curve | Show convergence only for a run whose model, configuration, and epoch count are known. | `Trabajo_Final.ipynb`, cells 84-125; `Modelos/*_hist.npy`; `docs/portfolio/portfolio-audit.md`, “Evidence-backed results” | `training-history.png` | `figures/training-history.png` | `RECREATE` | No real rows, but existing history artifacts remain private. | Regenerate from the public run; verify model linkage and epoch count. | Reproducibility |
| Reconstruction-error distribution and threshold | Explain MSE anomaly scores and the 95th-percentile training threshold. | `Trabajo_Final.ipynb`, cells 51-60; `Trabajo Final de Master.pdf`, pp. 31-38 and 42-49 | `reconstruction-error.png` | `figures/reconstruction-error.png` | `RECREATE` | Synthetic data or an approved rerun only. | Verify model, split, MSE calculation, threshold source, and caption. | Methodology and results |
| ROC curve | Show ranking performance only for a precisely identified experiment. | `Trabajo_Final.ipynb`, cells 56-60 and 89-124; `Trabajo Final de Master.pdf`, pp. 32, 35, 37-38, and 46-49 | `roc-curve.png` | `figures/roc-curve.png` | `RECREATE` | Synthetic data or an approved rerun only. | Match AUC, split, model, and experiment label to results table. | Results |
| Confusion matrix | Show the thresholded error trade-off with precision, recall, and specificity context. | `Trabajo_Final.ipynb`, cells 54-60 and 63-66; `Trabajo Final de Master.pdf`, pp. 31-38 and 42-49 | `confusion-matrix.png` | `figures/confusion-matrix.png` | `RECREATE` | Synthetic data or an approved rerun only. | Verify threshold, split, class labels, and associated metrics. | Results |
| Model-comparison figure | Compare PCA, autoencoder, and VAE without hiding the low-precision trade-off. | `Trabajo_Final.ipynb`, cells 80-125; `Trabajo Final de Master.pdf`, pp. 36-49; `docs/portfolio/portfolio-audit.md`, “Evidence-backed results” | `model-comparison.png` | `figures/model-comparison.png` | `RECREATE` | Aggregate metrics only; no real records. | Reconcile PCA discrepancy, distinguish normal-only and SMOTE-balanced paths, and cite each value. | Results |

## Deferred asset

A precision-recall curve is not listed as an approved initial asset because the
audited sources evidence ROC and confusion-matrix evaluation, but do not
identify a reusable precision-recall visual. It may be generated from a clean
public evaluation only after its data route, calculation, and caption are
validated. `NEEDS OWNER CONFIRMATION`.

## Historical-result controls

The model-comparison and ROC visuals must not treat historical values as newly
reproduced results. In particular, the normal-only PCA result differs between
the dissertation and notebook narrative, and the SMOTE-balanced experiments
need explicit methodological labels. Sources:
`docs/portfolio/publication-risk-register.md`, R9-R10; `Trabajo Final de
Master.pdf`, pp. 36-49; `Trabajo_Final.ipynb`, cells 80-125.

## Visual-release checklist

1. Redraw or regenerate each visual in English; do not copy the dissertation
   image or notebook output.
2. Confirm that no visual contains real records, personal information, local
   paths, or secret values.
3. Confirm the model, split, threshold, and metric context in each caption.
4. Publish historical values only with their internal source reference in the
   public documentation, or replace them with clean-rerun values.
5. Obtain owner approval for the final visual set and any result-bearing asset.
