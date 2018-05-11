# Symbols, Patterns and Signals

## B3. Nearest Neighbour

A nearest-neighbour classifier stores a set of exemplars, i.e. the training data, and assigns a test instance to the class of its nearest exemplar. This means that the instance space is divided by Voronoi tessellation, i.e. linear decision boundaries.

![](https://upload.wikimedia.org/wikipedia/commons/c/cb/Delaunay_Voronoi.png)  
An example tessellation. Note the decision boundaries (red) perpendicular to the lines between exemplars (black).

### <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-nearest neighbour classification

<img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-nearest neighbour classification takes the majority class of the <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/> nearest neighbours. With <img src="/tex/7eb22be4bf74527b54b6d60938478147.svg?invert_in_darkmode&sanitize=true" align=middle width=39.21220214999999pt height=22.831056599999986pt/>, this is the same as nearest neighbour, and with <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/> equal to the size of the training set, every instance is classed as the majority class of the training data. The optimal value for <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/> can be found with a separate test set.

### Distance weighting

In <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-NN, each of the <img src="/tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/> neighbours is equally weighted. Distance weighting weights the closest more. For example with a Gaussian kernel, when weighting the neighbour <img src="/tex/9fc20fb1d3825674c6a279cb0d5ca636.svg?invert_in_darkmode&sanitize=true" align=middle width=14.045887349999989pt height=14.15524440000002pt/> compared to point <img src="/tex/332cc365a4987aacce0ead01b8bdcc0b.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39498779999999pt height=14.15524440000002pt/>, <img src="/tex/f931f8e6e07ae4c9756731b60a62af0e.svg?invert_in_darkmode&sanitize=true" align=middle width=183.019815pt height=32.44583099999998pt/>. Now we can safely let <img src="/tex/43fdff0de41ddbaaf5cf1b6b6d8bc051.svg?invert_in_darkmode&sanitize=true" align=middle width=51.084366299999985pt height=22.831056599999986pt/>, and still get a meaningful result.

### Concerns

k-nearest neighbour methods take all features into account. This can cause problems if there are many features: irrelevant features may dominate distance calculations. The training set will only cover a fraction of the instance space, which causes overfitting, and so the ‘curse of dimensionality’.

How can we resolve these? Stretch/shrink dimensions if this improves the performance on a separate test set. Perform **feature selection** in a pre-processing step, discarding the unimportant features.