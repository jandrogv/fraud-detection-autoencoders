# Model Artifact Review

## Recommendation

**Exclude all model artifacts from the public repository.** The binary files
are useful private archives, but they do not explain the work to a recruiter,
have no supported public loading environment or model card, and some notebook
references use stale or different locations. The final notebook and English
documentation communicate the project more clearly.

No artifact is deleted or moved by this review. Private archival copies should
be retained outside the public repository before any cleanup.

## Inventory

| File | Apparent experiment | Size | Notebook reference | Clear public value | Recommendation |
|---|---|---:|---|---|---|
| `model_complete_v3_v34.h5` | Conventional autoencoder, normal-only path. | 214 KiB | Final notebook references `modelos-minmax/model_complete_v3_v34.h5`; experimental notebook also refers to this artifact name. | No; opaque binary without public context. | Exclude. |
| `model_complete_v3_v38.h5` | Conventional autoencoder, SMOTE-balanced path. | 235 KiB | Referenced by the final and experimental notebooks. | No; opaque binary without public context. | Exclude. |
| `model_complete_v2_7.h5` | VAE, SMOTE-balanced path. | 214 KiB | Referenced by the final and experimental notebooks. | No; requires undocumented custom-object context. | Exclude. |
| `vae_v5.h5` | VAE, normal-only path. | 237 KiB | Final notebook references the filename at the repository root, not this folder location; no exact experimental-notebook reference found. | No; location mismatch and no public loader. | Exclude. |
| `v3_34_hist.npy` | Conventional autoencoder training history. | 33 KiB | Final notebook references it through `../modelos-minmax/`; experimental notebook also references it. | No; array lacks readable run context. | Exclude. |
| `v3_38_hist.npy` | Conventional autoencoder training history. | 113 KiB | Referenced by the experimental notebook; the final notebook instead refers to `v3_36_hist.npy`. | No; reported epoch history is not a recruiter-facing artifact. | Exclude. |
| `v2_7_hist.npy` | SMOTE-balanced VAE training history. | 28 KiB | Referenced by the final and experimental notebooks. | No; array lacks readable run context. | Exclude. |
| `vae_hist_v5.npy` | Normal-only VAE training history. | 11 KiB | Final notebook references the filename at the repository root, not this folder location; no exact experimental-notebook reference found. | No; location mismatch and no public loader. | Exclude. |

## Decision required

The owner should confirm that private archival copies of all eight artifacts are
available before `modelos-minmax/` is removed from the visible public branch.
