# Models and Experiments

## Reconstruction-error scoring

The reconstruction models use per-observation reconstruction mean squared error
(MSE) as an anomaly score. The final notebook sets the decision threshold to the
95th percentile of training reconstruction MSE for the matching experiment and
evaluates thresholded alerts with confusion matrices, precision, recall,
specificity, ROC curves, and AUC. Source: `Trabajo_Final.ipynb`, cells 51-60
and 63-66.

## PCA baseline

PCA is a 30-component reconstruction baseline. Its normal-only test result is
weak and internally inconsistent: the dissertation reports AUC 0.48 while the
notebook narrative reports 0.52. This documentation preserves, rather than
resolves, the discrepancy. Sources: `Trabajo Final de Master.pdf`, p. 36;
`Trabajo_Final.ipynb`, cells 80-82.

## Conventional autoencoder

The conventional autoencoder is an encoder-decoder model with ELU activations,
batch normalisation, dropout, and a bottleneck. The SMOTE-balanced variant is
deeper. It flags unusually large reconstruction errors. Sources:
`Trabajo_Final.ipynb`, cells 84 and 108; `Trabajo Final de Master.pdf`, p. 61.

## Variational autoencoder

The VAE uses a latent distribution and reparameterised sampling. Its custom
objective combines reconstruction loss and Kullback-Leibler divergence. It is
evaluated through the same reconstruction-error framework. Sources:
`Trabajo_Final.ipynb`, cells 68-70, 93, and 117; `Trabajo Final de Master.pdf`,
pp. 62-63.

## Experiment families

Normal-only and SMOTE-balanced results use separate data strategies, thresholds,
and reported outcomes. They must be labelled separately in every comparison.
Source: `Trabajo_Final.ipynb`, cells 25-28 and 105-125.
