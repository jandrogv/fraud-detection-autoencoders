# Approved Public Content

This document defines the approved scope for a future public repository. New
public files listed below are deliverables to recreate; they are not existing
private source files to copy unchanged.

## Approved source code

- `src/preprocessing.py` - clean, English implementation of approved
  transformations and scaling.
- `src/autoencoder.py` - recreated conventional autoencoder architecture.
- `src/variational_autoencoder.py` - recreated VAE architecture, sampling,
  and loss logic.
- `src/evaluation.py` - reconstruction scoring, thresholding, metrics, and
  chart generation.

Each source file must be recreated from the approved methodology in
`Trabajo_Final.ipynb` and verified before public release.

## Approved notebooks

- `notebooks/01_exploratory_analysis.ipynb`
- `notebooks/02_pca_baseline.ipynb`
- `notebooks/03_autoencoders.ipynb`

The notebooks must be cleaned before publication. They must not contain raw
dataset rows, local paths, personal attribution, cached outputs, credentials,
or results that cannot be reproduced by the public workflow.

## Approved documentation

- English executive summary of the dissertation.
- Dataset dictionary and data-access policy.
- Methodology summary covering preprocessing, split design, and thresholding.
- Results summary with source-backed metrics and limitations.
- Reproducibility instructions, including environment setup and synthetic-data
  demonstration.

The original Spanish dissertation PDF is approved as a private reference for
these documents, not for direct inclusion in the public repository.

## Approved assets

- Recreated reconstruction-error distributions.
- Recreated ROC and precision-recall curves.
- Recreated confusion matrices.
- Recreated training-history figures after a verified rerun.
- Recreated autoencoder and VAE architecture diagrams.

## Not approved

- Full raw dataset or transaction records.
- Dataset redistribution without confirmed licence and owner approval.
- Local configuration, secrets, credentials, or absolute paths.
- Temporary model checkpoints, binary model weights, and cached notebook
  outputs.
- The original dissertation PDF, internal audit documents, or private Git
  history.
- Conflicting or unreproduced metrics presented as new public results.
