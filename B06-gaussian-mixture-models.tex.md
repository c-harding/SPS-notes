# Symbols, Patterns and Signals

## B6. Gaussian Mixture Models

This is another method for performing clustering, and it works by modelling each cluster as a multivariate normal distribution, with its own mean and covariance matrix. This is the equivalent of maximum-likelihood estimation, but we don’t have the means/covariances.

We treat cluster membership as a continuous hidden variable. This similar to $k$-means, except $k$-means has discrete Bernoulli cluster membership.

We solve this using the general algorithm called **Expectation-Maximisation** (EM).