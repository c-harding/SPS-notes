
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

The simplest classifier is one based solely on the means of each classifier, and works based on a single feature. Given two classes <img src="tex/d7b3f21735902404cb0e0d7ba7d13d5f.svg?invert_in_darkmode" align=middle width=16.78467779999999pt height=14.15524440000002pt/> and <img src="tex/e9a9c83358af33f100cf032f1fae035e.svg?invert_in_darkmode" align=middle width=16.78467779999999pt height=14.15524440000002pt/>, with means <img src="tex/d4c22567d6bf353815350caad68420a0.svg?invert_in_darkmode" align=middle width=16.45747124999999pt height=14.15524440000002pt/> and <img src="tex/d9324c21b00105263d6f54123813d99c.svg?invert_in_darkmode" align=middle width=16.45747124999999pt height=14.15524440000002pt/>, where <img src="tex/25bb4756fb670549cb348f4fe296c6e5.svg?invert_in_darkmode" align=middle width=55.654485149999985pt height=17.723762100000005pt/>, the decision boundary is <img src="tex/6ef612fdb290c7ef7a1f14964f72cc5c.svg?invert_in_darkmode" align=middle width=120.04331129999997pt height=24.65753399999998pt/>. If a value is less than the decision boundary, it is classed as <img src="tex/d7b3f21735902404cb0e0d7ba7d13d5f.svg?invert_in_darkmode" align=middle width=16.78467779999999pt height=14.15524440000002pt/>. Otherwise is it classed as <img src="tex/e9a9c83358af33f100cf032f1fae035e.svg?invert_in_darkmode" align=middle width=16.78467779999999pt height=14.15524440000002pt/>.

This is the best classifier, provided that…

- we only have one feature,
- both classes have a normal distribution, and
- both classes are equally likely to occur (uniform prior).

The decision boundary is where the probabilities are equal: <img src="tex/8461313dc729e7a1070a6953a1a22ddc.svg?invert_in_darkmode" align=middle width=151.19832584999997pt height=24.65753399999998pt/>.

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

<p align="center"><img src="tex/844f225464a6d9b18af9207f7a253aea.svg?invert_in_darkmode" align=middle width=106.78638464999999pt height=22.1917806pt/></p>

#### What about with non-uniform priors (MAP)?

<p align="center"><img src="tex/01b1a499290e229449f9b6ab17b9c65d.svg?invert_in_darkmode" align=middle width=147.7966677pt height=22.1917806pt/></p>
