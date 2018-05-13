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

The simplest classifier is one based solely on the means of each classifier, and works based on a single feature. Given two classes <img src="tex/d7b3f21735902404cb0e0d7ba7d13d5f.svg?invert_in_darkmode&sanitize=true" align=middle width=17.10703500000001pt height=13.387440000000009pt/> and <img src="tex/e9a9c83358af33f100cf032f1fae035e.svg?invert_in_darkmode&sanitize=true" align=middle width=17.10703500000001pt height=13.387440000000009pt/>, with means <img src="tex/d4c22567d6bf353815350caad68420a0.svg?invert_in_darkmode&sanitize=true" align=middle width=16.77984000000001pt height=13.387440000000009pt/> and <img src="tex/d9324c21b00105263d6f54123813d99c.svg?invert_in_darkmode&sanitize=true" align=middle width=16.77984000000001pt height=13.387440000000009pt/>, where <img src="tex/25bb4756fb670549cb348f4fe296c6e5.svg?invert_in_darkmode&sanitize=true" align=middle width=55.97674500000001pt height=16.95605999999997pt/>, the decision boundary is <img src="tex/6ef612fdb290c7ef7a1f14964f72cc5c.svg?invert_in_darkmode&sanitize=true" align=middle width=120.36568500000001pt height=23.889689999999977pt/>. If a value is less than the decision boundary, it is classed as <img src="tex/d7b3f21735902404cb0e0d7ba7d13d5f.svg?invert_in_darkmode&sanitize=true" align=middle width=17.10703500000001pt height=13.387440000000009pt/>. Otherwise is it classed as <img src="tex/e9a9c83358af33f100cf032f1fae035e.svg?invert_in_darkmode&sanitize=true" align=middle width=17.10703500000001pt height=13.387440000000009pt/>.

This is the best classifier, provided that…

- we only have one feature,
- both classes have a normal distribution, and
- both classes are equally likely to occur (uniform prior).

The decision boundary is where the probabilities are equal: <img src="tex/8461313dc729e7a1070a6953a1a22ddc.svg?invert_in_darkmode&sanitize=true" align=middle width=151.520655pt height=23.889689999999977pt/>.

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

<p align="center"><img src="tex/05b2ecf9974aefd5efadd7edc59e750d.svg?invert_in_darkmode&sanitize=true" align=middle width=109.98272999999999pt height=22.19184pt/></p>

#### What about with non-uniform priors (MAP)?

<p align="center"><img src="tex/cc8c805cebaffe8172cb342efcc9212d.svg?invert_in_darkmode&sanitize=true" align=middle width=165.17159999999998pt height=16.438356pt/></p>

#### Why does this work?

Bayes’ theorem: <img src="tex/fe54f62437ed8a830512086daa3a23b5.svg?invert_in_darkmode&sanitize=true" align=middle width=168.77355pt height=46.18383pt/>, where

- Posterior: <img src="tex/e4ccbccbfa80384ddf1e5a8d79a9ce65.svg?invert_in_darkmode&sanitize=true" align=middle width=55.293645000000005pt height=23.889689999999977pt/>
- Likelihood: <img src="tex/9fc6ea2f638ad155847bad95a91f4da5.svg?invert_in_darkmode&sanitize=true" align=middle width=55.293645000000005pt height=23.889689999999977pt/>
- Prior: <img src="tex/bff8f90d708e2e66c7ec7f0ee2f8ccaf.svg?invert_in_darkmode&sanitize=true" align=middle width=32.20024500000001pt height=23.889689999999977pt/>
- Evidence: <img src="tex/c9ea84eb1460d2895e0cf5125bd7f7b5.svg?invert_in_darkmode&sanitize=true" align=middle width=30.773325000000007pt height=23.889689999999977pt/>

Since the evidence is independent of <img src="tex/ae4fb5973f393577570881fc24fc2054.svg?invert_in_darkmode&sanitize=true" align=middle width=11.14426500000001pt height=13.387440000000009pt/>, it can be safely ignored when finding the <img src="tex/c2a1065518f3cfc6a486f07409a65c67.svg?invert_in_darkmode&sanitize=true" align=middle width=65.45484pt height=13.387440000000009pt/>.

#### What if we have multiple features?

If they are independent, this is easy:

<p align="center"><img src="tex/bcbb2c2c9b0ce7b65ff12b7e14b1c72d.svg?invert_in_darkmode&sanitize=true" align=middle width=204.01094999999998pt height=49.31553pt/></p>

If they are dependent, we need to take into account the mean vectors and covariance matrices:

<p align="center"><img src="tex/23f93f55cda47a03ac082377e79b8dbd.svg?invert_in_darkmode&sanitize=true" align=middle width=149.34909pt height=22.19184pt/></p>

With non-equal covariance matrices, the decision boundaries will not be linear, and the decision regions may not even be contiguous.

### Naïve Bayes Classifier

The naïve Bayes classifier works on the assumption that the features are independent.

<p align="center"><img src="tex/21c879dc4b53d9fa955ad4b2a11fdc74.svg?invert_in_darkmode&sanitize=true" align=middle width=511.92735pt height=49.31553pt/></p>

This works for symbolic features too, for example words in an email. Each word is modelled as a Bernoulli random variable, i.e. Boolean of whether it is present or not. The likelihoods are then found of appearing/not appearing in spam emails from a large test set.

<p align="center"><img src="tex/bac16588e914441d2eba33159826bd2c.svg?invert_in_darkmode&sanitize=true" align=middle width=252.27675pt height=44.897324999999995pt/></p>
<p align="center"><img src="tex/f77c3ec427a893d24eb8098b652aa88b.svg?invert_in_darkmode&sanitize=true" align=middle width=274.1937pt height=44.897324999999995pt/></p>

Then an email is classed as spam iff <p align="center"><img src="tex/ad21beac322d14f42eaf7b1fa965d069.svg?invert_in_darkmode&sanitize=true" align=middle width=395.18489999999997pt height=16.438356pt/></p>

For simplification, we assume that

- words do not have order or context
- words not found in spam/non-spam emails can be ignored
- repeated words are irrelevant (a set of words).

#### Laplace correction
Pronounced 🇫🇷 La place 🇫🇷

Add one pseudo-count to each outcome, so each word appears at least once in spam/non-spam emails. This is so that, if a word doesn't appear in any spam (resp. non-spam) emails, it won't zero the total probability of the email being spam (resp. not spam).
