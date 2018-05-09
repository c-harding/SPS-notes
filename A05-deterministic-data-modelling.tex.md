# Symbols, Patterns and Signals

## A5. Deterministic Data Modelling

A model is a description of data. They encode our assumptions about the data, enabling us to design *optimal* algorithms, and compare and contrast methods. All methods invoive an underlying meodel, but it may be implicit. When designing or using a method, it’s important to understand the underlying model.

Models don’t have to describe everything exactly. In some cases, we amy approximate the underlying physical processes, but in others this may be impossible and/or impractical. All we need is a model sufficient to define a method to solve the task. However, the better the model, the more performant the method will be. We choose a model based on how practical it will be to use, as well as on the assumptions we have about our data.

If we only have one dimension, the only option is usually just to choose thresholds for each class. However, when there are more dimensions, there are more possibilities for drawing the decision boundaries. It is a trade-off between complexity of the model and practicality of the method. However, complexity is not always a good thing: overfitting (image below) means the boundary is overly specific for the training data, rather than for the underlying data. In general, a simpler model usually gives good performance, and is more general.

![Overfitting example](A05-overfitting.png)

The simplest models are deterministic: they assume that relationships are fixed, and can be predicted over time. They do not allow for randomness or uncertainty, and the solution comes from minumising deviations from the model. This is in contrast to [probabilistic models](A06-probabilistic-modelling.md).

### Least Squares method

E.g. hypothesis that $weight = a + b \times length$, so we find the best values of $a$ and $b$: minimise the sum of the squares of the vertical offsets (the residual). The smaller the residual, the better the model.This is known as the least squares method.
$$ R(a,b) = \sum_i (y_i - (a+bx_i))^2 $$
$$ \frac{\partial R}{a} = -2\sum_i (y_i - (a+bx_i)) = 0 \\ \frac{\partial R}{b} = -2\sum_ix_i(y_i - (a+bx_i)) = 0 $$

$$ a_{LS} = \bar y - b\bar x$$
$$b_{LS} = \frac{\sum_i x_iy_i - N\bar x\bar y}{\sum_i x_i^2 - N\bar x^2}$$

Alternatively, it can be solved in matrix form:

$$R(a,b) = \sum_i (y_i - (a+bx_i))^2 = \left\|\mathbf y - \mathbf{Xa}\right\|^2$$
$$R(\mathbf a) = \left\|\mathbf y - \mathbf{Xa}\right\|^2$$
$$\mathbf y=\begin{bmatrix}y_1\\\vdots\\y_N\end{bmatrix}\quad\mathbf X=\begin{bmatrix}1&y_1\\\vdots&\vdots\\1&y_N\end{bmatrix}\quad\mathbf a=\begin{bmatrix}a\\b\end{bmatrix}$$
$$\mathbf{Xa} = a\begin{bmatrix}1\\\vdots\\1\end{bmatrix} + b\begin{bmatrix}x_1\\\vdots\\x_N\end{bmatrix}
\quad
\mathbf y - \mathbf{Xa} = \begin{bmatrix}y_1-a-bx_1\\\vdots\\y_N-a-bx_N\end{bmatrix}$$

Need to find $\arg\min_{\mathbf{a}}\left\|\mathbf y - \mathbf{Xa}\right\|^2$. All vectors $\mathbf{Xa}$ can be represented together by a hyperplane. So we set $\mathbf y - \mathbf{Xa}$ perpendicular to the hyperplane, i.e. orthogonal to all columns in $\mathbf{X}$.

$$\mathbf X^T\left(\mathbf y-\mathbf{Xa}\right) = \begin{bmatrix}0\\\vdots\\0\end{bmatrix}$$
$$\mathbf X^T\mathbf y = \mathbf X^T\mathbf X\mathbf a\\
\mathbf a_{LS} = \left(\mathbf X^T\mathbf X\right)^{-1}\mathbf X^T\mathbf y$$

### Polynomial generalisation

What about if we don't believe we have a linear relationship, but rather something else, like polynomial or sinusoidal?

$$y_i=a_1 + a_2x + a_3x^2 + \cdots + a_px^{p-1}$$

$$\mathbf X = \begin{bmatrix}1&x_1&\cdots&x_1^{p-1}\\\vdots&\vdots&\ddots&\vdots\\1&x_1&\cdots&x_p^{p-1}\end{bmatrix}\quad\mathbf a=\begin{bmatrix}a_1\\\vdots\\a_p\end{bmatrix}$$
$$\mathbf a_{LS} = \left(\mathbf X^T\mathbf X\right)^{-1}\mathbf X^T\mathbf y$$
