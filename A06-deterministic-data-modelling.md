# Symbols, Patterns and Signals

## 6. Deterministic Data Modelling

A model is a description of data. They encode our assumptions about the data, enabling us to design *optimal* algorithms, and compare and contrast methods. All methods invoive an underlying meodel, but it may be implicit. When designing or using a method, it’s important to understand the underlying model.

Models don’t have to describe everything exactly. In some cases, we amy approximate the underlying physical processes, but in others this may be impossible and/or impractical. All we need is a model sufficient to define a method to solve the task. However, the better the model, the more performant the method will be. We choose a model based on how practical it will be to use, as well as on the assumptions we have about our data.

If we only have one dimension, the only option is usually just to choose thresholds for each class. However, when there are more dimensions, there are more possibilities for drawing the decision boundaries. It is a trade-off between complexity of the model and practicality of the method. However, complexity is not always a good thing: overfitting (image below) means the boundary is overly specific for the training data, rather than for the underlying data. In general, a simpler model usually gives good performance, and is more general.

![Overfitting example](A06-overfitting.png)

The simplest models are deterministic: they assume that relationships are fixed, and can be predicted over time. They do not allow for randomness or uncertainty, and the solution comes from minumising deviations from the model. This is in contrast to [probabilistic models](A07-probabilistic-modelling.md).

### Least Squares method

E.g. hypothesis that <img src="tex/78b7aee2e8a0fb2ee9a011438f683a1f.svg?invert_in_darkmode&sanitize=true" align=middle width=169.230105pt height=22.831379999999992pt/>, so we find the best values of <img src="https://rawgit.com/xsanda/SPS-notes/master//tex/44bc9d542a92714cac84e01cbbb7fd61.svg?invert_in_darkmode" align=middle width=8.689230000000004pt height=14.155350000000013pt/> and <img src="https://rawgit.com/xsanda/SPS-notes/master//tex/4bdc8d9bcfb35e1c9bfb51fc69687dfc.svg?invert_in_darkmode" align=middle width=7.054855500000005pt height=22.831379999999992pt/>: minimise the sum of the squares of the vertical offsets (the residual). The smaller the residual, the better the model.This is known as the least squares method.
<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/a18a10d700db0414de98e499e1f2e3b8.svg?invert_in_darkmode" align=middle width=210.55485pt height=36.655409999999996pt/></p>
<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/03a563134d6f952244b5829999833e3f.svg?invert_in_darkmode" align=middle width=486.90345pt height=41.931284999999995pt/></p>

<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/9b7430e4120f191df1216735aee7f7b5.svg?invert_in_darkmode" align=middle width=94.33809pt height=14.611871999999998pt/></p>
<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/5256a26068eabf223cf78aca9c26dacd.svg?invert_in_darkmode" align=middle width=157.28394pt height=39.878685pt/></p>

Alternatively, it can be solved in matrix form:

<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/9b70c233635cda0c8c02c01c2e45a7ab.svg?invert_in_darkmode" align=middle width=310.0977pt height=36.655409999999996pt/></p>
<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/6a147f743ef9ed7c548c549d2e2f64e6.svg?invert_in_darkmode" align=middle width=133.30432499999998pt height=19.789935pt/></p>
<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/002e0d2a09583cf73625e02696812d9e.svg?invert_in_darkmode" align=middle width=273.41985pt height=69.041775pt/></p>
<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/d8fbddd4c4f03549b3bea776b592375a.svg?invert_in_darkmode" align=middle width=375.7743pt height=69.041775pt/></p>

Need to find <img src="https://rawgit.com/xsanda/SPS-notes/master//tex/540d97bf8e291da014d74a43f40d92fa.svg?invert_in_darkmode" align=middle width=140.85027pt height=31.360889999999984pt/>. All vectors <img src="https://rawgit.com/xsanda/SPS-notes/master//tex/51780d57e815147aa365d4cb5bdb668f.svg?invert_in_darkmode" align=middle width=23.481645pt height=22.557149999999986pt/> can be represented together by a hyperplane. So we set <img src="https://rawgit.com/xsanda/SPS-notes/master//tex/d9222dbe094a3e19c675a52c0f38d815.svg?invert_in_darkmode" align=middle width=53.812605pt height=22.557149999999986pt/> perpendicular to the hyperplane, i.e. orthogonal to all columns in <img src="https://rawgit.com/xsanda/SPS-notes/master//tex/d05b996d2c08252f77613c25205a0f04.svg?invert_in_darkmode" align=middle width=14.292300000000003pt height=22.557149999999986pt/>.

<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/f2065c7793472779c46da73deb6af775.svg?invert_in_darkmode" align=middle width=146.040015pt height=69.041775pt/></p>
<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/3711f508d716f643202d74b489647647.svg?invert_in_darkmode" align=middle width=263.86635pt height=23.75538pt/></p>

### Polynomial generalisation

What about if we don't believe we have a linear relationship, but rather something else, like a polynomial?

<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/1df0bbe6513a77c07c13b61ef750e032.svg?invert_in_darkmode" align=middle width=258.63419999999996pt height=18.906029999999998pt/></p>

<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/8512304ac8387e1fa6f7468d5bc8a20a.svg?invert_in_darkmode" align=middle width=276.6588pt height=72.00897pt/></p>
<p align="center"><img src="https://rawgit.com/xsanda/SPS-notes/master//tex/8a4662e08aa028b04fd90771a0677739.svg?invert_in_darkmode" align=middle width=158.93229pt height=23.75538pt/></p>
