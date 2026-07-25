# AGENTS.md — Portfolio publication workspace

## Purpose

This workspace coordinates the transformation of private projects into safe, clear public portfolio repositories.

## Language Policy

- Portfolio language: English.
- Repository documentation: English.
- Profile README: English.
- Future portfolio website: English.
- New or safely refactored source code: English.
- Original academic reports may remain in Spanish, but each report must include an English executive summary.
- A Spanish version of the portfolio is not required initially.
- New filenames, headings, diagrams, chart labels and repository descriptions must be written in English.
- Existing Spanish variable names, dataset fields and identifiers must only be translated when doing so is safe and does not break reproducibility.
- Original field names from Spanish datasets may remain unchanged when documented through an English data dictionary.
- Do not translate official project results, labels or technical terms in a way that changes their meaning.

## Source-of-truth rule

Private source repositories remain the source of truth. This workspace stores plans, audits and publication decisions. It must not become a container for complete copies of all projects.

## Publication safety

- Never assume a file is safe to publish.
- Never assume a dataset permits redistribution.
- Never expose credentials, cookies, sessions, API keys or internal endpoints.
- Never transfer production configuration to a public repository.
- Never publish personal or confidential data.
- Never publish strategic implementation merely because it exists in the source repository.
- Use synthetic examples when real data is not necessary.
- Keep the private repository history separate from the public repository history.
- Create public repositories from an approved file list.

## Working method

1. Audit one source repository at a time.
2. Produce documentation before implementation.
3. Classify content as public, summarised, recreated, synthetic, private or excluded.
4. Require owner approval of the publication specification.
5. Work on branches; do not modify `main` directly.
6. Use small commits.
7. Open a reviewable pull request.
8. Verify outputs and links.
9. Run a final security review before changing repository visibility.

## Accuracy

- Do not invent project results.
- Every important metric must reference a source file, notebook or report.
- Mark uncertain claims as `NEEDS OWNER CONFIRMATION`.
- Preserve limitations and negative results.
- Distinguish measured facts from recommendations.

## Scope

The projects are:

1. Fraud detection using autoencoders and variational autoencoders.
2. Analysis of water levels and birth rates in Spain using R and Power BI.
3. Tennis data platform with scraping, modelling and prediction.
4. Geospatial parcel management platform.

The parcel project will initially be published as documentation and a case study. A public demo with synthetic data is a later project.
