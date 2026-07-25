# Codex task: portfolio publication audit

You are auditing a private source repository to prepare a separate public portfolio repository.

## Goal

Understand the project, identify its professional value, classify all relevant content by publication risk, and propose a public repository structure. Do not publish, delete, move or substantially rewrite source files during this task.

## Non-negotiable rules

1. Treat the current repository as private and as the source of truth.
2. Work in read-only analysis mode wherever possible.
3. Do not modify `main`.
4. Do not create a public repository.
5. Do not copy files to another repository.
6. Do not expose secrets, tokens, cookies, credentials, private endpoints or production configuration.
7. Do not assume that datasets can be redistributed.
8. Do not include personal or confidential information in generated documentation.
9. Do not invent metrics, results, technologies or project claims.
10. Cite the internal file or notebook supporting each important result.
11. Mark uncertain conclusions as `NEEDS OWNER CONFIRMATION`.
12. Preserve the original repository structure during the audit.
13. Do not remove files, even when they appear obsolete.
14. Do not publish complete strategic implementations when a high-level explanation is sufficient.

## Required analysis

### A. Project overview

Identify:

- Problem addressed.
- Intended users.
- Main deliverables.
- Technologies.
- Data sources.
- ETL or preprocessing flow.
- Analysis or modelling flow.
- Visualisation and product components.
- Main results.
- Limitations.
- Personal contribution, when it can be inferred.
- Information that requires owner confirmation.

### B. Repository inventory

For each important file or folder, record:

- Path.
- Purpose.
- Whether it is currently used.
- Dependencies.
- Relevance to the portfolio.
- Publication classification.
- Risk.
- Recommended public treatment.

Use these classifications exactly:

- `PUBLICAR`
- `RESUMIR`
- `RECREAR`
- `SUSTITUIR POR SINTÉTICO`
- `MANTENER PRIVADO`
- `ELIMINAR DE LA VERSIÓN PÚBLICA`
- `NEEDS OWNER CONFIRMATION`

### C. Security and privacy review

Search for and report without reproducing secret values:

- `.env` files.
- API keys.
- Access tokens.
- Cookies.
- Session files.
- Passwords.
- Database strings.
- Private endpoints.
- Local absolute paths.
- Personal information.
- Proprietary datasets.
- Production deployment configuration.
- Internal logs.
- Screenshots containing sensitive information.

Report only file paths and risk categories. Redact any discovered value.

### D. Data and licence review

For every dataset:

- Identify its source.
- Locate licence information.
- Determine whether redistribution is clearly allowed, clearly prohibited or unknown.
- Recommend public inclusion, download instructions, aggregated output or synthetic replacement.
- Mark ambiguous cases for owner review.

### E. Results verification

Create a table of portfolio-worthy results:

| Result | Value | Supporting file | Reproducible | Publication recommendation |
|---|---:|---|---|---|

Do not include unverified values as facts.

### F. Existing reusable assets

Identify:

- Images.
- Charts.
- Diagrams.
- Screenshots.
- Reports.
- Academic documents.
- Existing Markdown documentation.
- Notebooks.
- Videos or GIFs.
- Data dictionaries.
- Architecture documents.

Recommend which can be reused directly and which should be recreated.

### G. Public repository proposal

Propose:

- Repository name.
- One-sentence description.
- GitHub topics.
- README outline.
- Public folder structure.
- Files to copy.
- Files to rewrite.
- New visualisations.
- Synthetic samples.
- Reproducibility instructions.
- Limitations section.
- Links or demos.
- Content that must remain private.

## Required deliverables

Create these files in a new audit branch:

```text
docs/portfolio-audit.md
docs/content-inventory.md
docs/publication-risk-register.md
docs/proposed-public-structure.md
```

Do not modify other project files unless needed solely to create these reports.

## Completion checks

Before finishing:

- Confirm no secret value has been copied into the reports.
- Confirm no project metric was invented.
- Confirm each publication recommendation references its source path.
- Confirm all uncertainty is visibly marked.
- Confirm no public repository was created.
- Summarise the decisions the owner must make next.
