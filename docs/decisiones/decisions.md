# Publication Decisions

## Repository strategy

- The current private repository will be cleaned and later made public.
- A separate public repository will not be created.
- The existing project history may be preserved only if the full Git history
  passes the security review.
- No source-code refactoring, translation, model retraining, evaluation, or
  new implementation is planned.
- This documentation phase does not delete source files, alter models, change
  notebooks, or rewrite history.

## Dissertation

- The original Spanish dissertation may remain in the public repository after a
  manual privacy review.
- The English public documentation will provide its recruiter-facing context.
- A separate English executive summary is not part of the current plan.

## Source code

- Existing notebooks will remain technically unchanged.
- Documentation will explain the purpose of the final notebook.
- `Pruebas autoencoder 0.ipynb` is an earlier experimental notebook; the
  default recommendation is to remove it from the visible public branch while
  retaining a private copy. `NEEDS OWNER CONFIRMATION`.
- The normal-only and SMOTE-balanced experiments will be described as distinct
  historical experiment families.

## Model files

- The saved HDF5 models and NumPy histories in `modelos-minmax/` do not add
  sufficient value to the visible public branch by default: they are opaque,
  lack a supported public loading environment, and do not improve a recruiter's
  understanding beyond the notebook and documentation.
- Each model and history artifact is therefore a removal candidate from the
  visible branch; private archival copies remain available. `NEEDS OWNER
  CONFIRMATION`.

## Historical results

- Metrics may be published only as **results reported in the original project**
  with a source reference to the dissertation or final notebook.
- The known PCA discrepancy is preserved: the dissertation reports AUC 0.48
  for the normal-only PCA test, while the notebook narrative reports 0.52.
  Neither value is selected as definitive. `NEEDS OWNER CONFIRMATION`.
- Reported low precision and the resulting false-positive burden must appear
  with recall, specificity, and AUC; the repository must not claim a deployed
  or production-ready fraud system.
