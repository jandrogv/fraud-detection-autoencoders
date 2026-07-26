# Project Overview

## Problem and objective

This Master's project studies fraud anomaly detection in highly imbalanced
card-transaction data. It uses reconstruction-based methods to identify
observations that differ from patterns learned by PCA, a conventional
autoencoder, and a VAE. It is an academic analysis, not a deployed service.

The objectives were to explore class imbalance, prepare the data, compare the
three model families, score anomalies by reconstruction MSE, choose thresholds,
and evaluate the resulting alerts with multiple metrics. Sources: `Trabajo
Final de Master.pdf`, pp. 14-27; `Trabajo_Final.ipynb`, cells 20-70 and 77-125.

## Workflow

1. Explore class balance, time-related behaviour, and transaction amounts.
2. Transform fields and fit scaling on the training partition.
3. Run separate normal-only and SMOTE-balanced experimental paths.
4. Compare PCA, conventional autoencoder, and VAE reconstructions.
5. Use reconstruction error and a training-derived threshold for alerts.
6. Review ROC-AUC, precision, recall, specificity, confusion matrices, and
   reconstruction-error distributions.

Source: `Trabajo_Final.ipynb`, cells 10-18, 25-28, 38-42, 51-60, and 77-125.

## Professional skills demonstrated

- Imbalanced anomaly-detection framing and exploratory analysis.
- Feature preparation and leakage-aware scaling.
- PCA and deep-learning reconstruction models.
- Reconstruction-error thresholding and multi-metric evaluation.
- Clear reporting of limitations and false-positive trade-offs.

`Trabajo_Final.ipynb` is the final project record. `Pruebas autoencoder
0.ipynb` contains earlier development iterations and is distinct from the final
experiment narrative.
