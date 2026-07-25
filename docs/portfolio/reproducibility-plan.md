# Reproducibility Plan

## Scope and status

This is the target reproducibility contract for the separate public repository.
It does not claim that the private notebook currently satisfies the contract.
The available source is `Trabajo_Final.ipynb`, which imports the project
libraries in cell 2 and records `RANDOM_SEED = 10`; no requirements file,
lockfile, or standalone Python source was present in the audit. Source:
`docs/portfolio/portfolio-audit.md`, “Scope and audit basis” and “Limitations
and publication blockers”.

## Runtime and Dependency Strategy

| Item | Plan | Status |
|---|---|---|
| Supported Python version | Select one Python version that is compatible with the chosen TensorFlow/Keras release, validate it in a clean clone, and record it in `README.md` and `requirements.txt`. The private source does not state an exact version. | `NEEDS OWNER CONFIRMATION` |
| Core dependencies | Start from the imports evidenced in `Trabajo_Final.ipynb`, cell 2: pandas, NumPy, scikit-learn, TensorFlow/Keras, imbalanced-learn, Matplotlib, and Seaborn. | Exact versions `NEEDS OWNER CONFIRMATION` |
| Dependency file | Use a pinned `requirements.txt` generated only after the first successful clean run; do not rely on unpinned notebook imports. | `NEEDS OWNER CONFIRMATION` for final pins |
| Environment isolation | Use a project-local virtual environment; do not depend on a global notebook environment. | Required |

Target setup commands for the future public repository are:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

These are target public instructions, not commands available in the current
private repository. The documented `python` executable must resolve to the
owner-approved supported version.

## Expected local directory structure

```text
fraud-detection-autoencoders/
├── data/
│   ├── synthetic/sample_transactions.csv
│   └── external/                 # Optional, ignored, never committed
├── outputs/                      # Ignored: generated models, metrics, figures
├── figures/                      # Approved generated figures only
├── scripts/
├── src/
└── tests/
```

`data/external/` is optional and must stay ignored. A real input file may be
used only after its acquisition route and licence are approved. The default
workflow must use `data/synthetic/sample_transactions.csv`.

## Data strategy

1. Generate or include a schema-compatible synthetic sample only.
2. Keep `creditcard.csv` and all real transaction records outside the public
   repository and its Git history.
3. Document `Time`, `V1`-`V28`, `Amount`, and `Class` as the private source
   schema only after verifying the public data-card wording.
4. If the owner confirms a lawful external acquisition route, accept it through
   an explicit ignored `data/external/` path; do not download or redistribute it
   automatically.

The source and redistribution wording remain `NEEDS OWNER CONFIRMATION`.
Sources: `creditcard.csv`; `Trabajo Final de Master.pdf`, p. 9;
`docs/portfolio/publication-risk-register.md`, R1-R2.

## Target public workflow

The commands below specify the CLI that the future public implementation must
provide. They are not present in the private repository today and therefore
remain implementation targets.

```powershell
# Create safe example data
python scripts/generate_synthetic_data.py --output data/synthetic/sample_transactions.csv --seed 10

# Preprocess the synthetic example
python scripts/run_experiment.py preprocess --data data/synthetic/sample_transactions.csv --output outputs/preprocessed --seed 10

# Train normal-only models
python scripts/run_experiment.py train --experiment normal-only --input outputs/preprocessed --output outputs/normal-only --seed 10

# Train the separately labelled SMOTE-balanced experiment
python scripts/run_experiment.py train --experiment smote-balanced --input outputs/preprocessed --output outputs/smote-balanced --seed 10

# Evaluate one completed experiment and create figures
python scripts/run_experiment.py evaluate --input outputs/normal-only --output outputs/evaluation --seed 10
```

The exact CLI argument names and supported modes are `NEEDS OWNER CONFIRMATION`.
The separate labels are required because the private notebook has a normal-only
path and a distinct SMOTE-balanced path. Source: `Trabajo_Final.ipynb`, cells
25-28, 38-42, and 51-60.

## Preprocessing and evaluation invariants

- Transform `Time` to hour-of-day and transform `Amount` to `log10_amount` only
  when the final public implementation confirms the same semantics.
- Split before fitting the scaler; fit `MinMaxScaler` on the training partition
  only and apply it to validation/test partitions.
- Calculate reconstruction MSE per observation.
- Derive the anomaly threshold from the 95th percentile of training
  reconstruction MSE for the matching experiment.
- Report threshold, AUC, precision, recall, specificity, confusion matrix, and
  ROC output together when they are available.

Sources: `Trabajo_Final.ipynb`, cells 20, 38-42, 51-60, and 63-66; `Trabajo
Final de Master.pdf`, pp. 14-18 and 31-38.

## Randomness and determinism

The documented private seed is `RANDOM_SEED = 10` (`Trabajo_Final.ipynb`, cell
2). The public implementation must set Python, NumPy, and TensorFlow random
seeds through one configuration path and record the seed in each run's metadata.
Exact reproducibility may still vary by TensorFlow version, hardware, and
deterministic-operation support; that caveat must remain in the README.

The exact TensorFlow deterministic-operation configuration is
`NEEDS OWNER CONFIRMATION` after the supported runtime is selected.

## Model-output handling

- Store checkpoints, trained weights, histories, metrics, and intermediate data
  under ignored `outputs/` paths.
- Do not commit generated model files by default.
- Promote only reviewed, regenerated figures to `figures/`.
- Do not reuse the private `Modelos/*.h5` or `Modelos/*_hist.npy` artifacts.
- Consider publishing new model files only after model-card, size, data,
  licensing, and owner review. `NEEDS OWNER CONFIRMATION`.

Sources: `docs/portfolio/content-inventory.md`, entries for `Modelos/` and its
artifacts; `docs/portfolio/publication-risk-register.md`, R5 and R7.

## Expected reproducible outputs

A clean synthetic demonstration must produce:

- a preprocessing summary and recorded seed;
- independently labelled normal-only and, if implemented, SMOTE-balanced run
  metadata;
- reconstruction-MSE scores and the matching threshold;
- evaluation tables and figures generated from the same evaluation path;
- English architecture and comparison visuals only when their inputs have been
  validated.

It must not claim to reproduce the dissertation's historical metrics from
synthetic data. Reported private-project values may be shown only as historical
results with citations, or replaced by verified values from an owner-approved
data route. The conflicting PCA AUC narrative must be resolved before it is
used in a public comparison. Sources: `Trabajo Final de Master.pdf`, p. 36;
`Trabajo_Final.ipynb`, cells 80-82; `docs/portfolio/publication-risk-register.md`,
R10.

## Clean-clone validation procedure

1. Create the new public repository with independent history only after owner
   approval; do not derive it from the private repository history.
2. Clone it into a new empty directory and verify that no real CSV, binary
   private model, original dissertation, internal audit file, secret, or local
   absolute path is present.
3. Create the documented virtual environment and install the pinned
   `requirements.txt` successfully.
4. Generate the synthetic sample and run preprocessing, training, evaluation,
   and tests using only the documented commands.
5. Confirm all tests pass, figures render, and all metric captions identify the
   model, split, threshold method, data route, and seed.
6. Compare any historical result table against its cited private evidence;
   remove or correct values that are not reconciled.
7. Run a final secret, large-file, licence, and content review before changing
   repository visibility.

Completion of this procedure and the exact supported runtime remain
`NEEDS OWNER CONFIRMATION` before public release.
