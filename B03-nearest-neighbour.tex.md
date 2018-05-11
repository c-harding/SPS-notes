# Symbols, Patterns and Signals

## B3. Nearest Neighbour

A nearest-neighbour classifier stores a set of exemplars, i.e. the training data, and assigns a test instance to the class of its nearest exemplar. This means that the instance space is divided by Voronoi tessellation, i.e. linear decision boundaries.

![](https://upload.wikimedia.org/wikipedia/commons/c/cb/Delaunay_Voronoi.png)  
An example tessellation. Note the decision boundaries (red) perpendicular to the lines between exemplars (black).

### $k$-nearest neighbour classification

$k$-nearest neighbour classification takes the majority class of the $k$ nearest neighbours. With $k=1$, this is the same as nearest neighbour, and with $k$ equal to the size of the training set, every instance is classed as the majority class of the training data. The optimal value for $k$ can be found with a separate test set.

### Distance weighting

In $k$-NN, each of the $k$ neighbours is equally weighted. Distance weighting weights the closest more. For example with a Gaussian kernel, when weighting the neighbour $x_i$ compared to point $x$, $weight(x,x_i) \propto e^{-\left\|x - x_i\right\|^2}$. Now we can safely let $k \to \infty$, and still get a meaningful result.

### Concerns

k-nearest neighbour methods take all features into account. This can cause problems if there are many features: irrelevant features may dominate distance calculations. The training set will only cover a fraction of the instance space, which causes overfitting, and so the ‘curse of dimensionality’.

How can we resolve these? Stretch/shrink dimensions if this improves the performance on a separate test set. Perform **feature selection** in a pre-processing step, discarding the unimportant features.