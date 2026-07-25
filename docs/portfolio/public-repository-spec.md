# Public Portfolio Repository Specification

## Status and scope

This specification translates the approved private-repository audit into a
reviewable plan for a separate public portfolio repository. It does not create
that repository, copy source code, redistribute data, or validate a new model
run. The private repository remains the source of truth.

## Repository identity

| Item | Specification |
|---|---|
| Proposed name | `fraud-detection-autoencoders` — `NEEDS OWNER CONFIRMATION` |
| GitHub description | An educational, reproducible case study of reconstruction-based anomaly detection for imbalanced transaction data, comparing PCA, autoencoders, and variational autoencoders. |
| Target audience | Recruiters, hiring managers, and technical peers reviewing applied machine-learning portfolio work. |
| Target roles | Machine Learning Engineer, Data Scientist, Applied AI Engineer, and Data/ML Analyst roles. |
| GitHub topics | `machine-learning`, `anomaly-detection`, `fraud-detection`, `autoencoders`, `variational-autoencoder`, `tensorflow`, `reproducible-research` |

## Professional narrative

The public repository should present a well-scoped Master's project as an
honest engineering case study: exploratory analysis, leakage-aware
preprocessing, reconstruction-error scoring, threshold selection, model
comparison, and transparent evaluation of an imbalanced classification
problem. It must describe the work as educational research, not as a deployed
fraud-detection system or a claim of operational impact.

The implementation will be rebuilt in English from the private notebook and
dissertation evidence, rather than copied wholesale. The primary implementation
source is `Trabajo_Final.ipynb`; no standalone Python source was found in the
audit. Source: `docs/portfolio/portfolio-audit.md`, “Scope and audit basis” and
“Limitations and publication blockers”.

## Complete public folder structure

```text
fraud-detection-autoencoders/
├── README.md
├── LICENSE                              # License choice requires approval
├── requirements.txt                     # Pinned after a validated clean run
├── .gitignore
├── data/
│   ├── README.md
│   └── synthetic/
│       └── sample_transactions.csv      # Synthetic, schema-compatible only
├── docs/
│   ├── executive-summary.md
│   ├── methodology.md
│   ├── results.md
│   └── limitations.md
├── notebooks/
│   ├── 01_exploration.ipynb
│   ├── 02_baseline-pca.ipynb
│   └── 03_autoencoders.ipynb
├── src/
│   ├── data.py
│   ├── preprocessing.py
│   ├── models.py
│   ├── evaluation.py
│   └── visualisation.py
├── scripts/
│   ├── generate_synthetic_data.py
│   └── run_experiment.py
├── tests/
│   ├── test_preprocessing.py
│   ├── test_thresholding.py
│   └── test_evaluation.py
└── figures/
    ├── architecture-autoencoder.svg
    ├── architecture-vae.svg
    ├── class-imbalance.png
    ├── transaction-time-profile.png
    ├── amount-transformation.png
    ├── training-history.png
    ├── reconstruction-error.png
    ├── roc-curve.png
    ├── confusion-matrix.png
    ├── model-comparison.png
```

This is a proposed new repository tree, not a request to create files in the
private repository. The source-to-destination status of every item is recorded
in `docs/portfolio/public-content-manifest.md`.

## README structure

1. **Problem and scope** — Define the project as an educational anomaly-
   detection case study.
2. **What is implemented** — PCA baseline, conventional autoencoder, VAE,
   reconstruction-MSE scoring, thresholding, and evaluation.
3. **Data policy** — State that no real transaction dataset is included;
   explain the synthetic sample and any approved acquisition route.
4. **Quick start** — Show the validated synthetic-data workflow only.
5. **Methodology** — Explain time and amount transformations, train-only
   scaling, normal-only and SMOTE-balanced experiments, and thresholding.
6. **Results** — Present only reconciled rerun metrics, or label historical
   values as reported project results with their sources.
7. **Visuals** — Link to recreated architecture, error-distribution, ROC, and
   comparison visuals.
8. **Limitations, ethics, and reproducibility** — Address data rights,
   imbalance, false-positive burden, anonymised features, and non-production
   scope.

## Technologies to highlight

The future public implementation may highlight the technologies evidenced by
`Trabajo_Final.ipynb`, cell 2: Python, pandas, NumPy, scikit-learn,
TensorFlow/Keras, imbalanced-learn, Matplotlib, and Seaborn. Exact package and
Python versions are not available in the private repository and remain
`NEEDS OWNER CONFIRMATION` after a validated environment is selected.

## Evidence-backed results to present

All figures below are historical project-reported values, not results
reproduced during the audit or by this specification. If included before a
clean rerun, they must retain that label and the cited source.

| Candidate result | Reported value | Internal evidence | Public-use condition |
|---|---|---|---|
| Conventional autoencoder, normal-only test | AUC 0.95; precision 11.77%; recall 86.65%; specificity 94.95% | `Trabajo Final de Master.pdf`, p. 37; `Trabajo_Final.ipynb`, cells 91-92 | Present all four values and the false-positive limitation together; preferably replace with a validated rerun. |
| VAE, normal-only test | AUC 0.92; precision 10.06%; recall 71.49%; specificity 95.03% | `Trabajo Final de Master.pdf`, p. 38; `Trabajo_Final.ipynb`, cells 100-101 | Same condition as above. |
| PCA, normal-only test | AUC 0.48; precision 0.74%; recall 4.98%; specificity 94.83% | `Trabajo Final de Master.pdf`, p. 36; `Trabajo_Final.ipynb`, cells 80-82 | Use only after reconciling the notebook's differing AUC narrative. `NEEDS OWNER CONFIRMATION`. |
| SMOTE-balanced autoencoder and VAE | Autoencoder: AUC 0.94, precision 2.3%, recall 82.83%, specificity 93.86%. VAE: AUC 0.93, precision 1.98%, recall 71.72%, specificity 93.783%. | `Trabajo Final de Master.pdf`, pp. 48-49; `Trabajo_Final.ipynb`, cells 108-125 | Explain the distinct SMOTE training design and rerun before using as a headline comparison. `NEEDS OWNER CONFIRMATION`. |

The normal-only validation results and all threshold and mean-MSE values remain
traceable in `docs/portfolio/portfolio-audit.md`, “Evidence-backed results”.
They should be included publicly only when a matching experiment and split are
made unambiguous.

## Limitations that must be disclosed

- The real dataset's licence and redistribution permission are unverified;
  therefore it must not be included in the public repository.
- The private data are highly imbalanced. Reported recall and AUC do not remove
  the practical alert burden implied by low precision.
- The source experiments use anonymised input features, limiting business
  interpretation.
- Normal-only and SMOTE-balanced training are different experimental designs
  and must never be presented as interchangeable.
- Current notebook artifact paths are stale or inconsistent, and no dependency
  lockfile exists. Historical results are not yet a verified public workflow.
- The repository demonstrates a research workflow, not a production-ready
  fraud system.

Sources: `docs/portfolio/publication-risk-register.md`, risks R1, R5, R6, R8,
R9, R10, and R13; `docs/portfolio/portfolio-audit.md`, “Limitations and
publication blockers”.

## Dissertation and documentation treatment

The original Spanish dissertation, `Trabajo Final de Master.pdf`, remains
private. The separate public repository must contain a newly written English
`docs/executive-summary.md` that covers problem framing, methods, historical
evidence, limitations, and the public data policy. It must not reproduce the
dissertation wholesale or include personal or institutional material without
explicit owner approval.

## Data availability and redistribution strategy

The public repository will contain only a generated, schema-compatible
synthetic sample and documentation explaining that it is not real transaction
data. It will not contain `creditcard.csv`, real records, or a claim that the
original data can be redistributed.

Any reference to an external original-data acquisition route requires confirmed
source, licence, and wording approval. Until then, it is
`NEEDS OWNER CONFIRMATION`. Sources: `creditcard.csv`; `Trabajo Final de
Master.pdf`, p. 9; `docs/portfolio/publication-risk-register.md`, R1-R2.

## Model-file strategy

Existing `Modelos/*.h5` files and `Modelos/*_hist.npy` files remain private.
The default public repository publishes no trained weights or history arrays.
Only new model outputs generated through the validated public workflow may be
considered later, after size, data implications, licensing, model-card content,
and owner approval are reviewed. `NEEDS OWNER CONFIRMATION`.

## Licence considerations

The future repository needs a licence selected by the owner after verifying
that it covers newly written code, documentation, figures, and any third-party
dependency or data references. MIT and Apache-2.0 are possible code-licence
options, but neither is approved here. The final licence choice is
`NEEDS OWNER CONFIRMATION`.

## Required owner approvals before implementation

1. Repository name, description, topics, and final licence.
2. Dataset source, licence, and any public acquisition wording.
3. Whether any personal attribution may appear in public materials.
4. The public framing of normal-only versus SMOTE-balanced experiments.
5. The reconciled, rerun-verified metric set and visual assets.
6. The supported Python/package versions and whether any new model files may
   be released.
7. Confirmation that `Trabajo_Final.ipynb` is the implementation source, or
   provision of the missing standalone Python source.
