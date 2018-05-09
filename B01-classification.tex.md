# Symbols, Patterns and Signals

## B1. Classification

There are two main classes of machine learning: supervised, where we assign classes in advance; and unsupervised, where the algorithm decides on classes.

A classifier is a program that performs supervised learning. Given

- a set of instances
- described by feature vectors, which can be numeric or symbolic,
- and a small set of classes,

a classifier tries to divide the d-dimensional instance space into regions of uniform class. In other words, it divides the input between distinct subsets, one for each class. A classifier shouldn’t just be able to classify the test data, but also classify future, unseen data well. Deterministic approaches tend to overfit the data, so probabilistic approaches generally work better.

### Classification techniques

- Decision tree based methods
- Rule-based method
- Neural nets
- Naïve Bayes networks
- Support vector machines

A decision boundary is a line separating points of different classes.

### Counting classifier

The simplest classifier is one based solely on the means of each classifier, and works based on a single feature. Given two classes $\omega_1$ and $\omega_2$, with means $\mu_1$ and $\mu_2$, where $\mu_1 < \mu_2$, the decision boundary is $l_0 = \left.\left(\mu_1+\mu_2\right)\middle/2\right.$. If a value is less than the decision boundary, it is classed as $\omega_1$. Otherwise is it classed as $\omega_2$.

This is the best classifier, provided that…

- we only have one feature,
- both classes have a normal distribution, and
- both classes are equally likely to occur (uniform prior).

The decision boundary is where the probabilities are equal: $p(l_0\mid \omega_1) = p(l_0\mid \omega_2)$.

### Creating a decision rule

1. Describe the data
    - features?
    - classes?
2. Select a classification model
    - How are the features distributed?
    - Is there any prior information we can use?
3. Estimate the parameters
    - For normal, what are the mean and variance?
4. Formulate the decision rule.
    - e.g. **if** $p(l\mid \omega_1) > p(l\mid \omega_2)$ **then** $\omega_1$ **else** $\omega_2$

#### What about with more than one class?

$$\arg\min_\omega p(l \mid \omega)$$

#### What about with non-uniform priors (MAP)?

$$\arg\min_\omega p(l \mid \omega)\, p(\omega))$$