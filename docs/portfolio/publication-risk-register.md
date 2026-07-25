# Publication Risk Register

This register records paths and risk categories only. It intentionally contains no secret values, credentials, personal identifiers, or transaction records.

| ID | Risk category | Affected path(s) | Evidence | Impact | Required action | Treatment |
|---|---|---|---|---|---|---|
| R1 | Dataset origin and redistribution rights unknown | `creditcard.csv`; `Trabajo Final de Master.pdf`, p. 9; `Trabajo_Final.ipynb`, cells 4-5 | The dissertation names Kaggle as the acquisition platform, but the repository retains no licence, canonical source link, permission, or data card. The CSV is ignored by Git. | High: public redistribution cannot be assumed. | Obtain owner confirmation of source and licence; otherwise use synthetic data and a generic data-access note. | `NEEDS OWNER CONFIRMATION` |
| R2 | Restricted data / large file | `creditcard.csv` | 150,828,752 bytes; 284,807 rows. | High: unsuitable for public Git history and not required for a portfolio demonstration. | Do not publish; provide a schema-compatible synthetic sample only. | `REPLACE WITH SYNTHETIC DATA` |
| R3 | Personal or confidential information | `Trabajo_Final.ipynb`; `Trabajo Final de Master.pdf` | The original academic materials contain personal attribution. | High: a public portfolio should not copy it without explicit consent and review. | Keep originals private; remove attribution from recreated public materials unless the owner explicitly chooses otherwise. | `KEEP PRIVATE` |
| R4 | Potential endpoint/configuration review required | `Trabajo_Final.ipynb` | Path-only keyword scan found content requiring review; no environment files were found and the notebook source scan found no absolute Windows paths or email addresses. | Medium: no secret value is reported by this audit, but the notebook must be redacted before publication. | Recreate focused source files and perform a final secret scan before any release. | `RECREATE` |
| R5 | Broken or stale artifact paths | `Trabajo_Final.ipynb`, cells 85, 88, 94, 97, 109, 112, 118, 121; `Modelos/` | Notebook references `modelos-minmax/...`, root-level VAE files, and a history filename not present in the committed artifact directory. | High: current execution path is not a reliable public reproduction workflow. | Resolve paths in a clean public implementation and rerun before presenting outputs as reproduced. | `RECREATE` |
| R6 | Missing environment specification | repository root; `Trabajo_Final.ipynb`, cell 2 | Imports identify packages, but there is no requirements/lockfile or setup guide. | High: others cannot reliably reproduce results. | Add an owner-approved `requirements`/lockfile, Python version, deterministic seed notes, and run instructions to the new repository. | `RECREATE` |
| R7 | Binary artifacts lack public context | `Modelos/*.h5`; `Modelos/*_hist.npy` | HDF5 weights and NumPy histories are present but have no model card, licence, or stable public loader. | Medium: binaries add little recruiter value and can create unsupported claims. | Keep private; regenerate approved plots/checkpoints from the clean workflow if needed. | `KEEP PRIVATE` |
| R8 | Metric interpretation risk | `Trabajo_Final.ipynb`, cells 81, 89, 91, 98, 100, 106, 113, 115, 122, 124 | Several experiments report high recall/AUC but very low precision. | High: a headline-only presentation could misrepresent alert burden and operational usefulness. | Present AUC, precision, recall, specificity, threshold method, and limitations together; do not make deployment or business-impact claims. | `SUMMARISE` |
| R9 | Experiment-design clarity | `Trabajo_Final.ipynb`, cells 25-28, 51-60, 113-124 | One path trains on normal data only; another uses SMOTE to include synthetic fraud in training. Thresholds are derived from each training reconstruction-error distribution. | Medium: the two approaches must not be conflated as the same anomaly-detection design. | Explain both experiments clearly and obtain owner approval for the public narrative and comparison. | `NEEDS OWNER CONFIRMATION` |
| R10 | Narrative/artifact/result inconsistency | `Trabajo_Final.ipynb`, cells 80-82, 86, 95, 110, 119; `Modelos/*_hist.npy`; `Trabajo Final de Master.pdf`, pp. 30, 36, and 41-44 | The dissertation reports normal-only PCA test AUC 0.48, while the notebook narrative reports 0.52. Some stated training limits also do not exactly match recorded history lengths. | High: competing internal sources weaken the credibility of unqualified public claims. | Treat all values as reported; reconcile the experiment versions or omit conflicting values after rerunning. | `NEEDS OWNER CONFIRMATION` |
| R11 | Language and academic-format mismatch | `Trabajo_Final.ipynb`; `Trabajo Final de Master.pdf` | The technical narrative is primarily Spanish and the PDF is an academic-length report. | Medium: copying it would not meet the English recruiter-facing objective. | Produce an English executive summary, concise README, and recreated figures. | `SUMMARISE` |
| R13 | Intended Python source absent | repository root; `Trabajo_Final.ipynb` | No standalone `.py` file is present. The notebook is the only executable analysis source found. | Medium: the final public implementation basis cannot yet be confirmed. | Provide the intended Python file or confirm that the notebook is the sole implementation source. | `NEEDS OWNER CONFIRMATION` |
| R12 | Internal-process leakage | `AGENTS.md`; `docs/portfolio/` | These files are portfolio-workspace instructions and audit records, not public project documentation. | Low: no recruiter value and unnecessary internal context. | Exclude from the public repository. | `EXCLUDE FROM PUBLIC VERSION` |

## Security-review outcome

- No `.env` files were found in the repository tree.
- No secret, token, password, cookie, or credential value is reproduced in any audit deliverable.
- No transaction record was copied into the audit reports.
- The final public-release process still requires a fresh secret scan after the approved public files are assembled.

## Owner approvals required

1. Confirm the dataset source, licence, and whether public download instructions may name it.
2. Confirm whether any personal attribution may appear in the public repository.
3. Approve the public interpretation of normal-only versus SMOTE-balanced experiments.
4. Approve which reported metric set, if any, may appear before a clean rerun.
5. Approve the proposed repository name and the final public file list.
6. Confirm whether `Trabajo_Final.ipynb` is the intended Python implementation source or provide the missing standalone `.py` file.
