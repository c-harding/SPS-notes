# Symbols, Patterns and Signals

## A7. Maximum Likelihood and Maximum a Posteriori estimation

Maximum likelihood instructions:

1. Determine $\theta$, $D$ and an expression for likelihood $p(D\mid\theta)$
2. Take the natural log of the likelihood
   $$\arg\max_\theta p(D\mid\theta) = \arg\max_\theta\ln p(D\mid\theta)$$
   $$\arg\max_\theta p(D\mid\theta) = \arg\min_\theta\left(-\ln p(D\mid\theta)\right)$$
3. Take the derivative/partial derivatives of $\ln p(D\mid\theta)$ with respect to $\theta$.
4. Set the derivative(s) to zero, and solve for $\theta$.

While this gives the same solution as the deterministic approach, it tells us more information. For example, how much $a_{ML}$ varies for different data sets, i.e. how reliable it is.

$$Var\left(a_{ML}\right)=E\left[\left(a_{ML} - \bar a_{ML}\right)^2\right]$$

$$Var\left(a_{ML}\right)=\left.\sigma^2\middle/\sum x_i^2\right.$$

The more recordings/the larger the values of $x$, the smaller the variance.

### Maximum a Posteriori estimation

ML does not take into account any prior information we have about the relative distribution of $\theta$. That is, it assumes that all outcomes are equally likely before considering the values.

MAP estimate: $\displaystyle \arg\max_\theta p(xD\mid \theta)p(\theta)$

If $p(\theta)$ is constant (all outcomes are equally likely), then this simplifies down to ML.
