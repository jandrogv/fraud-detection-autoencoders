# Approved Content for the Future Public Repository

## Existing files proposed for publication

| Existing path | Proposed treatment | Conditions |
|---|---|---|
| `.gitignore` | Keep visible | Retain rules that prevent data, local outputs, environments, and notebook caches from being committed. |
| `Trabajo_Final.ipynb` | Keep visible, unchanged | The final project notebook. Review notebook metadata and outputs for privacy before release; describe it in English documentation rather than translating or refactoring it. |
| `Trabajo Final de Master.pdf` | Keep visible only after review | The original Spanish dissertation. Publication requires the privacy checks in `docs/portfolio/SIMPLIFIED_DOCUMENTATION_PLAN.md`. `NEEDS OWNER CONFIRMATION`. |

## Public-facing documentation to create later

The future public branch will contain new English documentation only after this
plan is approved:

- `README.md`
- `docs/project-overview.md`
- `docs/data-and-preprocessing.md`
- `docs/models-and-experiments.md`
- `docs/results-and-limitations.md`

These are future documentation deliverables, not files created by this task.

## Static assets that may be created later

- An English project-workflow diagram.
- English autoencoder and VAE architecture diagrams.
- A source-cited historical-results table.
- Privacy-reviewed exports of existing project figures or notebook outputs.

No new model execution is required to create these static documentation assets.

## Not approved for the visible public branch

- `creditcard.csv` - real dataset; redistribution rights are unresolved.
- `Pruebas autoencoder 0.ipynb` - earlier experimental notebook with many
  iterations and stale model references; default recommendation is to remove it
  from the visible branch. `NEEDS OWNER CONFIRMATION`.
- `modelos-minmax/` and any legacy `Modelos/` model/history artifacts - opaque
  binary files with no recruiter-facing explanation or verified public loading
  path.
- `AGENTS.md`, `docs/portfolio/`, and `docs/decisiones/` - internal audit,
  governance, and planning material to move to the portfolio workspace or
  remove before publication.
- Local configuration, cache folders, temporary notebook checkpoints, and any
  unreviewed generated output.

No source file is removed by this documentation task.
