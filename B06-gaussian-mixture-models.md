# Symbols, Patterns and Signals

## B6. Gaussian Mixture Models

This is another method for performing clustering, and it works by modelling each cluster as a multivariate normal distribution, with its own mean and covariance matrix. This is the equivalent of maximum-likelihood estimation, but we don’t have the means/covariances.

We treat cluster membership as a continuous hidden variable. This similar to <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-means, except <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-means has discrete Bernoulli cluster membership.

We solve this using the general algorithm called **Expectation-Maximisation** (EM).