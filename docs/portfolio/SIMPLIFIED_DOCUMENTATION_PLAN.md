# Simplified Documentation and Publication Plan

## Status and scope

This plan supersedes the earlier separate-repository, code-reimplementation,
synthetic-data, test-suite, and rerun proposals. The approved direction is to
clean this existing repository and later make it public. This is a planning
document only: it does not modify source code, notebooks, models, the PDF, or
Git history.

The final implementation record is `Trabajo_Final.ipynb`. `Pruebas
autoencoder 0.ipynb` is an earlier experimental notebook, not a second final
implementation. Sources: `Trabajo_Final.ipynb`; `Pruebas autoencoder 0.ipynb`;
`docs/portfolio/content-inventory.md`.

## 1. Exact existing files proposed for the final public repository

| Existing path | Purpose in the public repository | Decision |
|---|---|---|
| `.gitignore` | Keeps real data, local outputs, environments, and temporary files outside the visible branch. | Keep, after final rule review. |
| `Trabajo_Final.ipynb` | Original final project notebook showing the analysis, preprocessing, model experiments, reconstruction-error scoring, and evaluation. | Keep unchanged, after a privacy/metadata/output review. |
| `Trabajo Final de Master.pdf` | Complete original dissertation in Spanish, supporting the historical methodology and results. | Keep unchanged. |

The future English documentation files listed in section 6 will be added only
after this plan is approved; they do not yet exist and are not created by this
task.

## 2. Existing files proposed for removal from the visible public branch

These are future cleanup decisions, not deletions performed by this task.
Private archival copies should be retained before any visible-branch cleanup.

| Existing path | Reason for removal from the visible branch | Decision |
|---|---|---|
| `creditcard.csv` | Real transaction data; the audit found no redistribution permission or data card. | Remove from visible branch; do not publish. |
| `Pruebas autoencoder 0.ipynb` | Large experimental notebook with many earlier iterations, paths, and saved-model references; it dilutes the recruiter-facing narrative. | Remove |
| `modelos-minmax/` | Eight HDF5/NumPy artifacts are opaque, lack a public model card/loading environment, and add little explanatory value. | Remove from visible branch |
| Any legacy `Modelos/` path in Git history | Legacy location for the same type of binary model/history artifacts. | Remove from visible branch and inspect history |
| `AGENTS.md` | Internal workspace instruction file. | Move to the separate portfolio workspace or remove before publication. |
| `docs/portfolio/` | Internal audits, risk registers, prior specifications, and planning records. | Move to the separate portfolio workspace or remove before publication. |
| `docs/decisiones/` | Internal approval and planning records. | Move to the separate portfolio workspace or remove before publication. |
| Local configuration, caches, checkpoints, and unreviewed generated files | No recruiter value and possible privacy/configuration risk. | Remove from visible branch after an inventory review. |

## 3. Internal documents to move or remove before publication

The complete `docs/portfolio/` and `docs/decisiones/` directories are internal
working material. In particular, the audit prompt, audit report, content
inventory, risk register, prior public-repository specification, manifest,
visual-assets plan, reproducibility plan, publication brief, approved-content
record, decisions, and this plan should not be visible in the final
recruiter-facing repository. Store them in the separate portfolio workspace or
retain them privately outside the public Git history.

## 4. Saved-model value assessment

All saved files currently found in `modelos-minmax/` are valuable as private
project archives but insufficiently useful as visible public portfolio content.
They are binary artifacts, provide no self-contained explanation to a recruiter,
and the notebook contains inconsistent or stale artifact paths. No model needs
to be published to demonstrate the work.

| Saved artifact | Experiment association from the final notebook/audit | Visible-branch value | Proposed treatment |
|---|---|---|---|
| `modelos-minmax/model_complete_v3_v34.h5` | Conventional autoencoder, normal-only path; source: `Trabajo_Final.ipynb`, cell 85. | No: opaque binary, no public loader or model card. | Keep private; remove from visible branch. |
| `modelos-minmax/model_complete_v3_v38.h5` | Conventional autoencoder, SMOTE-balanced path; source: `Trabajo_Final.ipynb`, cell 109. | No: same binary-context limitation. | Keep private; remove from visible branch. |
| `modelos-minmax/model_complete_v2_7.h5` | VAE, SMOTE-balanced path; source: `Trabajo_Final.ipynb`, cell 118. | No: custom-object loading context is not documented publicly. | Keep private; remove from visible branch.|
| `modelos-minmax/vae_v5.h5` | VAE, normal-only path; source: `Trabajo_Final.ipynb`, cell 94. | No: notebook path differs from current artifact location. | Keep private; remove from visible branch. |
| `modelos-minmax/v3_34_hist.npy` | Conventional autoencoder training history. | No: opaque array without readable run context. | Keep private; remove from visible branch. |
| `modelos-minmax/v3_38_hist.npy` | Conventional autoencoder training history. | No: recorded epochs conflict with parts of the narrative. | Keep private; remove from visible branch. |
| `modelos-minmax/v2_7_hist.npy` | SMOTE-balanced VAE training history. | No: opaque array without readable run context. | Keep private; remove from visible branch. |
| `modelos-minmax/vae_hist_v5.npy` | Normal-only VAE training history. | No: opaque array and stale path context. | Keep private; remove from visible branch. |

## 5. Dissertation PDF privacy checks

Before publishing `Trabajo Final de Master.pdf`, the owner must review:

1. Author name, signature, student number, email address, institutional
   identifiers, tutor/reviewer names, acknowledgements, and other personal
   information.
2. Embedded PDF metadata, document properties, creation tools, attachment
   objects, links, comments, and bookmarks.
3. Screenshots, tables, figures, and appendices for transaction-level data,
   confidential references, local paths, or personal information.
4. Dataset attribution and wording: the report names a Kaggle-hosted,
   anonymised ULB dataset but does not establish redistribution permission.
5. The right to publish the dissertation under the selected repository licence
   or with a clear separate copyright notice.

Publication of the PDF remains `NEEDS OWNER CONFIRMATION` after this review.

`Owner Confirmaion`
Publication its available after the review of the owner


## 6. Public-facing documentation structure and purpose

All public-facing documentation will be newly written in English. It will
describe the existing project without modifying or translating the notebooks.

| Future path | Purpose |
|---|---|
| `README.md` | Recruiter-facing entry point, project scope, visible assets, historical-results notice, key limitations, and navigation. |
| `docs/project-overview.md` | Problem framing, academic context, scope, repository contents, and professional skills demonstrated. |
| `docs/data-and-preprocessing.md` | Dataset availability restriction; existing `Time` and `Amount` transformations; train-only scaling; and the distinction between normal-only and SMOTE-balanced paths. |
| `docs/models-and-experiments.md` | PCA, conventional autoencoder, and VAE descriptions; experiment families; reconstruction-MSE scoring; and the 95th-percentile threshold method. |
| `docs/results-and-limitations.md` | Clearly labelled historical results with exact internal source references, the PCA discrepancy, low-precision/false-positive limitation, non-production scope, and data-rights limitation. |

## 7. Proposed README structure

1. Project title and one-sentence scope.
2. What this repository demonstrates.
3. Repository contents and how to read the final notebook.
4. Data availability statement: no dataset is included or redistributed.
5. Method overview: preprocessing, model families, reconstruction error, and
   thresholding.
6. Experiments: clearly separate normal-only training from SMOTE-balanced
   experiments.
7. Historical reported results: cite the dissertation/final notebook and state
   the PCA discrepancy.
8. Limitations and responsible interpretation: class imbalance, low precision,
   false positives, anonymised features, and non-production status.
9. Visuals and dissertation link, subject to the privacy review.
10. Licence and attribution, subject to owner approval.

## 8. Existing figures and notebook outputs that may be reused without rerunning

Reuse means selecting or exporting an already existing visual without executing
the machine-learning workflow. Every selected asset still requires the PDF or
notebook privacy review and an English contextual caption.

| Existing evidence | Candidate reusable output | Conditions |
|---|---|---|
| `Trabajo_Final.ipynb`, cells 10-18; `Trabajo Final de Master.pdf`, pp. 10-13 | Class-imbalance, time-of-day, and amount-transformation exploratory figures. | Preserve as historical visuals; do not expose records; add English caption. |
| `Trabajo_Final.ipynb`, cells 54-60 and 63-66; `Trabajo Final de Master.pdf`, pp. 31-38 and 42-49 | Reconstruction-error distributions, threshold illustrations, ROC curves, and confusion matrices. | Keep model, split, threshold, and metric context together. |
| `Trabajo_Final.ipynb`, cells 80-125; `Trabajo Final de Master.pdf`, pp. 36-49 | Existing result tables/comparisons. | Label as reported historical results; preserve the normal-only PCA discrepancy (AUC 0.48 in `Trabajo Final de Master.pdf`, p. 36, versus 0.52 in `Trabajo_Final.ipynb`, cells 80-82) and separate experiment families. |
| `Trabajo Final de Master.pdf`, pp. 61-63 | Existing architecture explanations. | Use only after privacy/copyright review; prefer new English static diagrams where clarity requires it. |

## 9. New static diagrams allowed without code execution

- A project workflow diagram: data availability restriction -> documented
  preprocessing -> normal-only and SMOTE-balanced experiment branches -> PCA,
  autoencoder, and VAE -> reconstruction MSE -> percentile threshold ->
  evaluation.
- A conventional-autoencoder architecture diagram based on the final notebook
  model definition.
- A VAE diagram showing encoder, latent sampling, decoder, reconstruction loss,
  and KL-divergence term, based on the final notebook.
- A result-interpretation diagram explaining why high recall/specificity can
  coexist with low precision and a substantial false-positive burden.

These are explanatory static documentation assets. They must not imply a new
run, alter the existing code, or introduce unsupported numerical results.

## 10. Final security and Git-history review checklist

Before changing repository visibility, complete and record the following:

1. Confirm the visible file list contains only approved content and excludes
   `creditcard.csv`, model binaries, experimental notebook if excluded,
   internal planning directories, caches, and local configuration.
2. Scan the working tree, staged files, all commits, branches, tags, and
   reachable blobs for credentials, tokens, passwords, personal information,
   local paths, real dataset files, and large binaries.
3. Inspect `.gitignore` and verify it blocks the real CSV, virtual environments,
   notebook checkpoints, local outputs, and future model artifacts.
4. Review Git remotes, branches, tags, release assets, Git LFS objects, commit
   messages, author data, and historical copies of files proposed for removal.
5. If restricted content appears in history, decide whether it requires a
   history rewrite before publication. Do not rewrite history without explicit
   owner approval. `NEEDS OWNER CONFIRMATION`.
6. Complete the dissertation privacy review and confirm its publication right.
7. Review notebook metadata and existing outputs for personal data, local paths,
   secrets, and dataset exposure without modifying the notebook during this
   planning phase.
8. Verify every public metric is labelled as historical, cites its original
   source, separates normal-only from SMOTE-balanced experiments, preserves the
   PCA discrepancy, and states the false-positive limitation.
9. Obtain owner approval for the final visible file list, licence, attribution,
   data wording, model-binary treatment, and publication timing.

`Question answers;`

1. In the documentation and in the git the `creditcard.csv` cant be uploaded as it wights more than 100MB,
   so include only the url and explanation from where it comes.
5. I want to clean the histiry records before making it public. 

## Superseded recommendations

The following earlier recommendations are superseded: creating a separate
public repository; rebuilding source into modules; creating cleaned notebooks;
generating synthetic data; adding scripts, tests, command-line interfaces, and
dependency-driven rerun instructions; retraining/evaluating models; and
recreating figures from new runs. The audit evidence remains valid as a factual
reference, but those implementation proposals are no longer the publication
strategy.
