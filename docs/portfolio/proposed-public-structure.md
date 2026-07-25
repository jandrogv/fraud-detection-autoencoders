# Proposed Public Repository Structure

## Proposal

- **Provisional name:** `fraud-detection-autoencoders` - `NEEDS OWNER CONFIRMATION`.
- **One-sentence description:** A reproducible educational case study of reconstruction-based anomaly detection for imbalanced card-transaction data, comparing PCA, autoencoders, and variational autoencoders.
- **Suggested topics:** `machine-learning`, `anomaly-detection`, `fraud-detection`, `autoencoders`, `variational-autoencoder`, `tensorflow`, `reproducible-research`.

The public repository should be a clean implementation and explanation, with its own history. It must not be created by copying this repository's Git history or files wholesale.

## Recommended tree

```text
fraud-detection-autoencoders/
├── README.md
├── LICENSE                         # Choose only after owner confirmation
├── requirements.txt                # Pinned, owner-approved environment
├── .gitignore
├── data/
│   ├── README.md                   # Data source/licence/access statement
│   └── synthetic/
│       └── sample_transactions.csv # Schema-compatible synthetic sample only
├── docs/
│   ├── executive-summary.md        # English summary of the dissertation
│   ├── methodology.md              # Splits, scaling, scoring, thresholding
│   ├── results.md                  # Source-backed, rerun-verified comparison
│   └── limitations.md              # Data, imbalance, precision, scope limits
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
    ├── reconstruction-error.png
    └── model-comparison.png
```

## Migration map

| Private source | Public target | Treatment | Conditions |
|---|---|---|---|
| `Trabajo_Final.ipynb`, cells 2-76 | `src/`, `notebooks/`, and `docs/methodology.md` | `RECREATE` | Rebuild in English, preserve the documented seed/split/threshold logic, and remove stale paths and embedded outputs. |
| `Trabajo_Final.ipynb`, cells 77-125 | `docs/results.md` and rerun notebooks | `SUMMARISE` | Cite a matching rerun for every public metric; otherwise label results as historical reported results or omit them. |
| `Trabajo Final de Master.pdf` | `docs/executive-summary.md` | `SUMMARISE` | English-only executive summary; original PDF remains private. |
| Existing report figures | `figures/` | `RECREATE` | Redraw in English with source-backed captions. Relevant private references: `Trabajo Final de Master.pdf`, pp. 10-13, 31-38, 42-49, and 61-63. |
| `creditcard.csv` | `data/synthetic/sample_transactions.csv` | `REPLACE WITH SYNTHETIC DATA` | Do not copy real records. Include only a schema-compatible synthetic sample and data-access statement. |
| `Modelos/` | none by default | `KEEP PRIVATE` | Publish no weights/history arrays without a clean rerun, model card, and owner approval. |
| Internal audit/governance files | none | `EXCLUDE FROM PUBLIC VERSION` | Do not copy `AGENTS.md` or `docs/portfolio/`. |

## README outline

1. Problem framing and scope: educational anomaly-detection case study, not a production fraud system.
2. What is implemented: PCA baseline, autoencoder, VAE, reconstruction-MSE scoring, thresholding, and evaluation.
3. Data policy: no dataset included; licence/source status and synthetic-data policy.
4. Reproducible quick start: environment creation, synthetic demo, and optional approved data instructions.
5. Method: preprocessing, split design, normal-only and SMOTE-balanced experiments, and the 95th-percentile threshold method. Source: `Trabajo_Final.ipynb`, cells 20, 25-28, 51-52.
6. Results: only rerun-verified metrics, with AUC, precision, recall, specificity, and limitations shown together.
7. Visuals: recreated architecture diagram, reconstruction-error distribution, ROC/PR curves, and comparison table.
8. Limitations and ethics: dataset rights, strong class imbalance, low precision/alert burden, anonymised features, and non-production scope.

## Reproducibility standard for the new repository

- Pin the Python and package versions identified from `Trabajo_Final.ipynb`, cell 2, after validating them in a new environment.
- Keep the recorded random seed visible (`RANDOM_SEED = 10` in notebook cell 2), while documenting that complete determinism can depend on the TensorFlow runtime.
- Fit preprocessing only on the training partition and test it with automated checks. The existing notebook follows this scaler pattern in cells 38-42.
- Keep normal-only and SMOTE-balanced experiments separate, with explicit labels and independently generated result tables.
- Generate threshold, ROC, precision-recall, and confusion-matrix outputs from one evaluation module so the public values cannot diverge from the charts.
- Do not claim the historical values in `Trabajo_Final.ipynb`, cells 81-124, have been independently reproduced until the clean workflow has generated them again.

## Decisions requiring owner approval before publication

1. Dataset source/licence, download wording, and whether a public data-access link may be used.
2. Repository name, licence, and public description.
3. The public metric set and whether historical results are shown before rerunning.
4. The methodological framing of SMOTE-balanced training.
5. Any personal attribution and any reusable dissertation figures.
6. The final approved file list after a secret scan and reproduction run.
7. Whether `Trabajo_Final.ipynb` is the intended Python source or a separate `.py` file must be supplied.
