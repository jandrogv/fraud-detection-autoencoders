# Fraud Detection Publication Brief

## Purpose

Prepare the existing repository to become a recruiter-facing public portfolio project. repository that demonstrates
an end-to-end fraud-anomaly-detection workflow without exposing private data,
personal information, internal configuration, or unverified claims.

## Public audience

The public repository is intended for technical recruiters, hiring managers,
and practitioners interested in machine learning, anomaly detection, and
reproducible data workflows.

## Public proposition

The portfolio version will explain and recreate the project workflow:

- exploratory analysis of an imbalanced transaction dataset;
- preprocessing and train/validation/test partitioning;
- PCA as a baseline;
- conventional autoencoder and variational autoencoder experiments;
- reconstruction-MSE anomaly scoring and percentile-based thresholding; and
- evaluation through ROC-AUC, precision, recall, specificity, and visual
  analysis.

Reported results must remain traceable to `Trabajo Final de Master.pdf` and
`Trabajo_Final.ipynb` until they are reproduced by the approved public
workflow.

## Publication constraints

- The private repository remains the source of truth.
- The complete dataset is not approved for redistribution.
- The public repository must have a separate Git history.
- Public documentation and new code must be in English.
- The original Spanish dissertation remains a private reference; an English
  executive summary will be created instead.
- Any public metric must cite a reproducible source and preserve its
  limitations, especially the false-positive trade-off.

## Release gate

The owner must approve the data-access wording, final public file list,
personal-attribution policy, metric narrative, and repository licence before
the public repository is created or made visible.
