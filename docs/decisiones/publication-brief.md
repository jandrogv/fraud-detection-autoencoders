# Fraud Detection Publication Brief

## Purpose

Prepare this existing repository for a later public release as a
recruiter-facing Master's-project portfolio. The release will present the
existing final notebook, original dissertation, and selected historical
outputs; it will not recreate the implementation or rerun the project.

## Public audience

Technical recruiters, hiring managers, and practitioners reviewing applied
machine-learning work in anomaly detection, deep learning, and data analysis.

## Professional proposition

The repository documents an end-to-end fraud-anomaly-detection project:

- exploratory analysis of highly imbalanced transaction data;
- documented preprocessing and partitioning;
- a PCA baseline, conventional autoencoder, and variational autoencoder;
- reconstruction-MSE anomaly scoring with percentile-based thresholding; and
- evaluation with ROC-AUC, precision, recall, specificity, confusion matrices,
  reconstruction-error analysis, and visual outputs.

Historical values must be labelled **results reported in the original project**
and cited to `Trabajo Final de Master.pdf` and/or `Trabajo_Final.ipynb`. They
must not be presented as newly reproduced results.

## Publication strategy

- This existing repository will be cleaned and later made public.
- No separate public repository, code reimplementation, refactor, translation,
  model run, or synthetic-data workflow is planned.
- `Trabajo_Final.ipynb` is the primary implementation record.
- `Pruebas autoencoder 0.ipynb` is an earlier experimental record and is not a
  recruiter-facing default. Its final visibility is `NEEDS OWNER CONFIRMATION`.
- The Spanish dissertation may be published after a privacy review.
- Public-facing documentation will be written in English.

## Reporting controls

- Keep normal-only and SMOTE-balanced experiments explicitly separate.
- Preserve the reported low-precision/false-positive limitation alongside
  recall, specificity, and AUC.
- Preserve the unresolved PCA discrepancy: the dissertation reports a
  normal-only test AUC of 0.48, while the notebook narrative reports 0.52.
  Do not select one as definitive without owner review.

## Release gate

Before visibility changes, the owner must approve the final visible file list,
dissertation privacy review, data and personal-information review, model-binary
decision, historical metric wording, repository licence, and security/Git
history review. Each unresolved item is `NEEDS OWNER CONFIRMATION`.
