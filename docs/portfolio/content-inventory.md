# Content Inventory and Proposed Treatment

Labels in this inventory use the required publication vocabulary exactly. A treatment is a recommendation for a separate public repository, not an instruction to change this private repository.

| Path | Purpose and evidence | Portfolio relevance | Proposed treatment | Risk and recommended public handling |
|---|---|---|---|---|
| `.gitignore` | Ignores `creditcard.csv`. | Shows the private dataset was intentionally kept out of Git. | `PUBLISH` | Recreate the equivalent ignore rule in the public repository; retain no dataset file. |
| `AGENTS.md` | Workspace-level publication instructions; currently untracked. | Not project evidence for a recruiter. | `EXCLUDE FROM PUBLIC VERSION` | Internal process material; do not copy. |
| `docs/portfolio/` | Internal audit prompt, context, and audit outputs. | Useful for the owner, not for the public case study. | `KEEP PRIVATE` | Keep decision records separate from the public repository. |
| `docs/portfolio/CODEX_AUDIT_PROMPT.md` | Internal audit requirements. | None for public users. | `EXCLUDE FROM PUBLIC VERSION` | Internal governance document. |
| `docs/portfolio/PUBLICATION_CONTEXT.md` | Internal publication context and language policy. | None for public users. | `EXCLUDE FROM PUBLIC VERSION` | Internal governance document. |
| `creditcard.csv` | Local transaction dataset: 284,807 rows, 492 fraud-labelled rows; fields `Time`, `V1`-`V28`, `Amount`, and `Class`. The dissertation identifies Kaggle as the acquisition platform but does not retain licence terms. Source: direct metadata read; `Trabajo Final de Master.pdf`, p. 9. | Necessary for private verification, but not needed in a public Git history. | `REPLACE WITH SYNTHETIC DATA` | Redistribution rights remain unverified. Provide a synthetic schema-compatible sample and documented owner-approved download instructions only if rights are confirmed. |
| `Trabajo_Final.ipynb` | Only available executable analysis source; Spanish notebook covering EDA, preprocessing, two split strategies, PCA, autoencoder/VAE evaluation, figures, and results. Source: cells 2-125. | Highest-value implementation evidence. | `RECREATE` | Rebuild as focused English modules/notebooks; remove personal attribution, stale paths, embedded outputs, and unverified narrative claims. |
| `Trabajo Final de Master.pdf` | 63-page Spanish Master's dissertation with an abstract, methodology, formal results, conclusions, references, and appendix code. Source: pp. 4-63. | Primary results source and visual reference. | `SUMMARISE` | Keep the original private. Produce a concise English executive summary and redraw only approved figures. |
| Standalone Python source (`*.py`) | No `.py` file was present during the updated audit; `Trabajo_Final.ipynb` is the available executable source. | A missing source file prevents confirmation of the intended public implementation basis. | `NEEDS OWNER CONFIRMATION` | Provide the intended Python file or confirm that the notebook is the sole source of truth. |
| `Modelos/` | Tracked binary model and history artifact directory. | Supports the existence of completed experiments but is not a readable portfolio interface. | `KEEP PRIVATE` | Do not publish binary weights by default. Recreate training artifacts from an approved public workflow only. |
| `Modelos/model_complete_v3_v34.h5` | Conventional autoencoder artifact associated by name with the normal-only experiment. Source: `Trabajo_Final.ipynb`, cell 85. | Secondary evidence only. | `KEEP PRIVATE` | Binary artifact; notebook path does not match the stored location. |
| `Modelos/model_complete_v3_v38.h5` | Conventional autoencoder artifact associated by name with the SMOTE-balanced experiment. Source: `Trabajo_Final.ipynb`, cell 109. | Secondary evidence only. | `KEEP PRIVATE` | Binary artifact; publish only after a clean reproduction and owner approval. |
| `Modelos/model_complete_v2_7.h5` | VAE artifact associated by name with the SMOTE-balanced experiment. Source: `Trabajo_Final.ipynb`, cell 118. | Secondary evidence only. | `KEEP PRIVATE` | Custom objects are required to load it; no public model-card or environment exists. |
| `Modelos/vae_v5.h5` | VAE artifact associated by name with the normal-only experiment. Source: `Trabajo_Final.ipynb`, cell 94. | Secondary evidence only. | `KEEP PRIVATE` | Notebook expects a different location; retain privately. |
| `Modelos/v3_34_hist.npy` | Training-history artifact with loss/validation-loss and accuracy/validation-accuracy series. | Can inform a recreated learning-curve figure. | `RECREATE` | Redraw only from a verified rerun; do not use the binary array as a public interface. |
| `Modelos/v3_38_hist.npy` | Training-history artifact for the deeper conventional autoencoder. | Can inform a recreated learning-curve figure. | `RECREATE` | The recorded 3,197 epochs conflict with the notebook narrative; validate before use. |
| `Modelos/v2_7_hist.npy` | Training-history artifact associated with the balanced VAE. | Can inform a recreated learning-curve figure. | `RECREATE` | Validate model/artifact linkage and environment before use. |
| `Modelos/vae_hist_v5.npy` | Training-history artifact associated with the normal-only VAE. | Can inform a recreated learning-curve figure. | `RECREATE` | Notebook expects a root-level path, not `Modelos/`; do not publish unchanged. |

## Reusable content by type

| Asset type | Evidence | Proposed treatment | Notes |
|---|---|---|---|
| EDA charts | `Trabajo_Final.ipynb`, cells 10-18; `Trabajo Final de Master.pdf`, pp. 10-13 | `RECREATE` | Redraw in English from synthetic data or an owner-approved data acquisition path. |
| Reconstruction-error and confusion-matrix charts | `Trabajo_Final.ipynb`, cells 54-60; `Trabajo Final de Master.pdf`, pp. 31-38 and 42-49 | `RECREATE` | Preserve the analytical idea; use consistent English labels and source-backed captions. |
| ROC curves | `Trabajo_Final.ipynb`, cells 56-60 and result cells 89-124; `Trabajo Final de Master.pdf`, pp. 32, 35, 37-38, and 46-49 | `RECREATE` | Include only after reproducing the matching experiment. |
| Architecture explanations | `Trabajo_Final.ipynb`, cells 84, 93, 108, 117; `Trabajo Final de Master.pdf`, pp. 61-63 | `RECREATE` | Create simple English diagrams; do not reuse the Spanish report verbatim. |
| Academic methodology narrative | `Trabajo_Final.ipynb`; `Trabajo Final de Master.pdf`, pp. 14-27 and 50-54 | `SUMMARISE` | Convert to a short English executive summary, methodology section, and limitations section. |
| Dataset documentation | `Trabajo_Final.ipynb`, cell 4; `Trabajo Final de Master.pdf`, p. 9; CSV header | `NEEDS OWNER CONFIRMATION` | Add a public data card only after source/licence and redistribution status are confirmed. |

## Non-value-adding content for a recruiter-facing repository

- The full private CSV and all binary model weights.
- The complete Spanish dissertation/export and internal audit/governance documents.
- Notebook execution outputs that duplicate charts without a reproducible environment.
- Any personal attribution or institutional material contained in the original notebook/PDF.
