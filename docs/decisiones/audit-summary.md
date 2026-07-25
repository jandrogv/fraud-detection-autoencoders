# Fraud Detection Audit Summary

## Project status

The private source repository has been audited and is suitable for preparing
a separate public portfolio version. The public version must be recreated from
an approved file list rather than copied from the private repository.

## Main strengths

- End-to-end reconstruction-based anomaly-detection workflow.
- Conventional autoencoder and variational autoencoder implementations.
- Data preprocessing and severe-imbalance analysis.
- Reconstruction-error threshold selection using the 95th training-MSE
  percentile.
- Evaluation using ROC-AUC, precision, recall, specificity, confusion
  matrices, and visual analysis.
- A Master's dissertation supporting the methodology, results, limitations,
  and reusable figure concepts.

## Main publication risks

- Full dataset redistribution has not been approved.
- Large data files must remain outside the public repository.
- Notebook paths and binary model artifacts require a clean public
  implementation.
- One PCA baseline value differs between the dissertation and notebook and
  must be reconciled before public use.
- Spanish academic documentation requires an English executive summary.
- No standalone Python source file is currently present; the notebook is the
  available implementation source and requires owner confirmation.

## Recommended public format

A reproducible machine-learning portfolio repository containing recreated
English source code, selected cleaned notebooks, regenerated visual results,
synthetic sample data, concise documentation, and an English summary of the
dissertation.

## Evidence

The audit evidence is recorded in `docs/portfolio/portfolio-audit.md`,
`docs/portfolio/content-inventory.md`, and
`docs/portfolio/publication-risk-register.md`.
