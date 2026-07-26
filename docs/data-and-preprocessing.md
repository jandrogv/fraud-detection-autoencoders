# Data and Preprocessing

## Data availability

The original work uses a Kaggle-hosted anonymised credit-card-fraud dataset
attributed in the dissertation to the ULB Machine Learning Group. The dataset
is not included here, and the repository does not establish redistribution
permission. Source: `Trabajo Final de Master.pdf`, p. 9;
`docs/portfolio/publication-risk-register.md`, R1-R2.

The audited local dataset contained 284,807 transactions and 492 fraud-labelled
transactions. This aggregate describes the imbalance only; no transaction row
is reproduced. Source: `docs/portfolio/content-inventory.md`, `creditcard.csv`
entry.

## Fields and transformations

The original schema includes `Time`, anonymised variables `V1` to `V28`,
`Amount`, and binary label `Class`. The final notebook converts `Time` to
hour-of-day, replaces `Amount` with `log10_amount`, and fits `MinMaxScaler` on
the training partition before applying it to later partitions. Sources:
`Trabajo_Final.ipynb`, cells 4-5, 20, and 38-42; `Trabajo Final de Master.pdf`,
pp. 14-18.

## Experimental data strategies

| Strategy | Training treatment | Meaning |
|---|---|---|
| Normal-only | Reconstruction models train on normal transactions. | Reconstruction-based anomaly-detection path. |
| SMOTE-balanced | SMOTE is used in a separately balanced training route. | Different experiment design; not interchangeable with normal-only training. |

Thresholds are derived from the relevant training reconstruction-error
distribution. Source: `Trabajo_Final.ipynb`, cells 25-28 and 51-60.

## Limitation

The anonymised variables limit business interpretation. This repository does
not provide a dataset download workflow or claim that the original CSV can be
shared.
