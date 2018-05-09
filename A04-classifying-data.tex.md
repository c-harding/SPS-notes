
# Symbols, Patterns and Signals

## A4. Classifying Data

For a set of scalar values, the simplest summaries are the mean and variance:

**Mean:** $\displaystyle\mu=\frac{1}{N}\sum_iv_i$

**Variance:** $\displaystyle\sigma^2=\frac{1}{N}\sum_i(v_i-\mu)^2 = \frac{1}{N}\sum_iv_i-\mu^2$

### Estimates from a sample

The sample mean for $N_s$ samples is $\bar x = \frac{1}{N_s}\sum_{i=1}^{N_s}x_i$. As $N_s \to \infty$, $\bar x \to \mu$.

The sample variance is likewise $s^2 = \frac{1}{N_s-1}\sum_{i=1}^{N_s}(x_i - \bar x)^2$. As $N_s \to \infty$, $s^2 \to \sigma^2$.

### Vectors

The mean vector is the sum of a collection of vectors, divided by the count, just like of scalars. $\displaystyle\mathbf{μ} = \sum_i\mathbf v_i$.

The covariance is a matrix: $\displaystyle\mathbf C=\frac{1}{N}\sum_i\begin{bmatrix}(v_i1-\mu_1)^2&(v_i1-\mu_1)(v_i2-\mu_2)\\(v_i1-\mu_1)(v_i2-\mu_2)&(v_i2-\mu_2)^2\end{bmatrix}$. The leading diagonal represents the variance in each dimension, and each other value is the covariance between components. The matrix is symmetrical across the leading diagonal.

Short notation: let $\mathbf e_i = \mathbf v_i - \mathbf μ$ in $\displaystyle\mathbf C=\frac{1}{N}\sum_i\begin{bmatrix}e_{i1}^2&e_{i1}e_{i2}\\e_{i1}e_{i2}&e_{i2}^2\end{bmatrix}$

      │ x  ┌     ┐      x │    ┌     ┐
      │x   │ + + │       x│    │ + - │
    ──x──  │ + + │      ──x──  │ - + │
     x│    └     ┘        │x   └     ┘
    x │                   │ x

      x    ┌     ┐        │    ┌     ┐
      x    │ 0 0 │        │    │ + 0 │
    ──x──  │ 0 + │      xxxxx  │ 0 0 │
      x    └     ┘        │    └     ┘
      x                   │  
      
    x │ x  ┌     ┐
     x│x   │ + 0 │
    ──x──  │ 0 + │
     x│x   └     ┘
    x │ x   

### Orientation and Spread

Assume all points lie on a line: $\displaystyle\mathbf e_i = \alpha_i \mathbf u$, where $\left\|\mathbf u\right\| = 1$, $u_1^2+u_2^2=1$

$\displaystyle\mathbf C=\frac1N\sum_i\begin{bmatrix}e_{i1}^2&e_{i1}e_{i2}\\e_{i1}e_{i2}&e_{i2}^2\end{bmatrix}=\lambda\begin{bmatrix}u_1^2&u_1 u_2\\u_1 u_2&u_2^2\end{bmatrix}$, where $\displaystyle\lambda=\frac1N\sum_i\alpha_i^2$.

$\displaystyle\mathbf{Cu}=\lambda\begin{bmatrix}u_1^2&u_1 u_2\\u_1 u_2&u_2^2\end{bmatrix}\begin{bmatrix}u_1\\u_2\end{bmatrix} = \begin{bmatrix}u_1^3+u_1u_2^2\\u_1^2u_2+u_2^3\end{bmatrix} = \begin{bmatrix}u_1\\u_2\end{bmatrix}=\lambda \mathbf u$

This means that, if all the points are in a straight line, $\mathbf{u}$ is an eigenvector, and $\lambda$ is an eigenvalue, for the covariance matrix. This means that the orientation of the data is in the line $\mathbf{u}$, and its spread in that direction is given by $\sqrt\lambda$.

For real 2D data, there are two such orthogonal eigenvector-eigenvalue pairs, which represent the principal axes of the data. The eccentricity of the data is the ratio of the larger of these eigenvalues to the smaller, and can be visualised by an ellipse with major and minor axes given by the larger and smaller eigenvector-eigenvalue products respectively.

### Outliers

Mean and variance become pretty inaccurate when outliers are present in the data. Outliers are a small number of points with values significantly different to the rest of the data. Likewise with vector data, they skew the vector mean and covariance. Alternatively, we can use the median value. This is the ‘middle’ value, or the midpoint of the two middle values if there are an even number of points. If the data is multidimensional, the median of each component is taken. However, the median is difficult to work with, e.g. the median of two sets cannot be defined in terms of the two sets' medians.

What about for the variance? Normally, the square of the difference between the value and the mean is used as the ‘variance kernel’, to calculate the variance. An outlier-resistant kernel could instead be used, which could flatten out at a given value. This is, however, also difficult to work with, especially with vector values.

### Location and spread

To find where the significant data is, and how spread out it is, in a numerical sequence, we can use the **centroid** (centre of mass) and the **moment of inertia** respectively.

For a 1D sequence $u(n)$, $0≤n<n$, where $\displaystyle M= \sum_nu(n)$:

- centroid: $\displaystyle\bar n = \frac1M\sum_nu(n)n$
- moment of inertia: $\displaystyle I = \frac1M\sum_nu(n)(n-\bar n)^2$

For a multi-dimensional sequence $u(\mathbf x_i)$:

- centroid: $\displaystyle\bar{\mathbf x} = \frac1M\sum_nu(\mathbf x_i)\mathbf x_i$
- moment of inertia: $\displaystyle I = \frac1M\sum_nu(\mathbf x_i)(\mathbf x_i-\bar{\mathbf x})(\mathbf x_i-\bar{\mathbf x})^T$

The eigenvectors and eigenvalues of the moment of inertia define the orientation and spread of the data. Again, beware of outliers: could treat values below a certain threshold as zero.

The centroid and moment of inertia of a histogram are the same as the mean and covariance respectively of the underlying data.
