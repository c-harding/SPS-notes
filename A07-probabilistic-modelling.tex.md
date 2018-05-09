# Symbols, Patterns and Signals

## 7. Probabilistic Data Modelling

With a deterministic model, we don’t model any uncertainties or ‘randomness’ in the data. In some applications this is not a problem, but in others, we can benefit from using a *probabilistic model*.

Now, instead of modelling $weight = a \times length$, we account for error with $weight = a \times length + e$, where $e$ is a random number, usually close to zero. This says that, if we have a large number of samples, on average, we expect to see a linear relationship between weight and length.

‘Random’ does not mean $e$ can take on arbitrary values at any time. It simply means we are uncertain as to what value it will have at any given time, and we build that uncertainty into our model. We do this formally with **random variables** and **probability theory**.

For example, we could model the length of a species as being distributed around the average length with a certain spread, i.e. length = average length + $e$. If we only take one sample, it’s hard to estimate what the average is, so we need lots of data to use the model.

### Continuous random variables

$$ P(a \le x \le b) = \int_a^bp(x)\,\mathrm dx$$
$$ P(a \le x \le b) = \int_{-\infty}^\infty p(x)\,\mathrm dx = 1$$

#### Normal distribution

$$X \sim N(\mu,\sigma^2)$$
$$p(x) = \frac{1}{\sigma\sqrt{2\pi}}\,\exp\frac{-(x-\mu)^2}{2\sigma^2}$$

##### Vector normal

$$p(\mathbf x) = \frac{1}{\sigma\sqrt{2\pi}}\,\exp\left(\frac{-1}{2}(\mathbf x-\mathbf μ)^TC^{-1}(\mathbf x-\mathbf μ)\right)$$

### Marginal distribution

For a vector (multi-dimensional) distribution, we can find the marginal distribution of one dimension, i.e. the distribution of one variable without assumption of the others, by summing/integrating over all the others:

For 2D continuous: $\displaystyle p_1(x_1) = \int_{-\infty}^\infty p(\mathbf x)\,\mathrm dx_2 \quad p_2(x_2) = \int_{-\infty}^\infty p(\mathbf x)\,\mathrm dx_1$

For independent dimensions, $p(\mathbf x) = \prod_i p_i(x_i)$

### Probabilistic line fitting

$$weight = a \times length + \varepsilon$$

Assume that $\varepsilon \sim N\left(0,\sigma^2\right)$. Use **Maximum Likelihood** estimation:

$$D = \left\{\left(x_1,y_1\right),\left(x_2,y_2\right),\dots,\left(x_N,y_N\right)\right\}$$
$$a_{ML} = \arg\max_ap(D\mid a)$$

Assume that all the measurements are independent: $\displaystyle p(D\mid a) = \prod_{i=1}^Np(y_i\mid x_i,a)$.

Since $\varepsilon \sim N\left(0,\sigma^2\right)$ in $y=ax+\varepsilon$, we get $p(y_i\mid x_i,a)\sim N\left(ax_i,\sigma^2\right)$.

$$a_{ML} = \arg\max_a p(D\mid a) = \frac{1}{\sigma\sqrt{2\pi}}\exp\frac{-(y_i-ax_i)^2}{2\sigma^2}$$
$$a_{ML}=\arg\max_a\sum_i\left(\ln\frac1{\sigma\sqrt{2\pi}}-\frac{(y_i-ax_i)^2}{2\sigma^2}\right)$$
$$a_{ML}=\arg\min_a\sum_i(y_i-ax_i)^2$$
$$a_{ML}=\frac{\sum_iy_ix_i}{\sum_ix_i^2}$$

This gives the same results as with deterministic model.