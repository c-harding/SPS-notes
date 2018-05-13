# Symbols, Patterns and Signals

## B6. Gaussian Mixture Models

This is another method for performing clustering, and it works by modelling each cluster as a multivariate normal distribution, with its own mean and covariance matrix. This is the equivalent of maximum-likelihood estimation, but we don’t have the means/covariances.

We treat cluster membership as a continuous hidden variable. This similar to $k$-means, except $k$-means has discrete Bernoulli cluster membership.

We solve this using the general algorithm called **Expectation-Maximisation** (EM).

### ML example

Suppose $a$ students received an A, $b$ students got a B, $c$ got a C, and $d$ got a D, where we know the values of $a$, $b$, $c$ and $d$. We also know that $p(\mathsf A) = \frac12$, $p(\mathsf B) = \mu$, $p(\mathsf C) = 2\mu$ and $p(\mathsf D) = \frac12 - 3\mu$. What is $\mu$?

We can solve this with maximum likelihood:

$$ p(a,b,c,d \mid \mu) \propto \left(\tfrac12\right)^a\mu^b(2\mu)^c \left(\tfrac12-3\mu\right)^d$$
$$ \log p(a,b,c,d \mid \mu) = l + a\log\tfrac12 + b\log\mu + c\log2\mu+d\log\left(\tfrac12-3\mu\right)$$

Setting the derivative to zero:

$$\frac b \mu + \frac c\mu + \frac{3d}{\frac12-3\mu}=0 \implies \mu = \frac{b+c}{6(b+c+d)}$$

### EM example

But what about when we have even less information?

Suppose $h=a+b$ students got an A or a B, $c$ got a C and $d$ got a D ($h$, $c$ and $d$ known). As before, $p(\mathsf A) = \frac12$, $p(\mathsf B) = \mu$, $p(\mathsf C) = 2\mu$ and $p(\mathsf D) = \frac12 - 3\mu$. What is $\mu$?

$$\left.\begin{matrix}\frac ab = \frac{1/2}\mu\\a+b=h\end{matrix}\right\}
a = \frac{1/2}{1/2+\mu}h,\quad b = \frac\mu{1/2+\mu}h$$

If we knew $\mu$, we could calculate $a$ and $b$, and vice-versa. Instead, we can use Expectation-Maximisation.

- let $\mu(t)$ be the estimate of $\mu$ after the $t$th iteration.
- let $b(t)$ be the estimate of $b$ after the $t$th iteration.

**E-step**: assign expected value to hidden variables.
$$b(t) = E[b\mid\mu(t)] = \frac{\mu(t)}{1/2+\mu(t)}h$$
**M-step**: re-estimate parameters.
$$\mu(t+1) = \arg\max_\mu p(a(t),b(t),c,d\mid\mu) = \frac{b(t)+c}{6(b(t)+c+d}$$

These should converge on the right answer.

### Expectation-Maximisation for Gaussian Mixtures

Given data $x_i$ drawn from $k$ normal distributions with unknown means and equal variance (the actual variance is unimportant, so can be set to 1), we want to obtain estimates of the means $\mu_1\dots\mu_k$.

Introduce hidden variables $z_{ij}$ indicating the likelihood that x_i came from the $j$th cluster.

**E**: for each data point $x_i$, for each $j\le k$:

$\displaystyle z_{ij} = E\left[z_{ij}\mid x_i,\mu_j(t)\right]\propto e^{-(x_i-\mu_j(t))^2/2}$, normalised such that $\displaystyle\sum_j^kz_{ij}(t) = 1$

**M**: for each $j\le k$, estimate the mean as the weighted average:
$$\mu(t+1)=\arg\max_\mu p(x_1\dots x_n,z_{1j}\dots z_{nj}\mid\mu) = \left.\sum_i^nz_{ij}(t)x_i\middle/\sum_i^nz_{ij}(t)\right.$$