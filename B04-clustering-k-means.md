# Symbols, Patterns and Signals

## B4. Clustering: *k*-means

Clustering involves segmenting the instance space into regions of similar objects. There is no supervision in the learning: the regions are not labelled. We can use a distance metric for clustering. If we have <img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39774000000001pt height=22.063469999999988pt/> clusters, this is known as **<img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39774000000001pt height=22.063469999999988pt/>-means clustering**.

function <img src="tex/4e50773f30bf5d635345035116fe6c80.svg?invert_in_darkmode&sanitize=true" align=middle width=97.685445pt height=23.889689999999977pt/>

1. randomly initialise <img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39774000000001pt height=22.063469999999988pt/> vectors <img src="tex/db23570dd407dca4b949935269d8d766.svg?invert_in_darkmode&sanitize=true" align=middle width=51.49221000000001pt height=13.387440000000009pt/>
2. **repeat until** each <img src="tex/b10f1a73c4bbb9953fac419cd1828d3c.svg?invert_in_darkmode&sanitize=true" align=middle width=4.973215500000009pt height=13.387440000000009pt/> has stopped changing:
   1. assign each $\mathbf x \in xs$ to the nearest $\mathbf μ_j$
   2. recompute each $\mathbf μ_j$ as the mean of the instances assigned to it
3. **return** <img src="tex/db23570dd407dca4b949935269d8d766.svg?invert_in_darkmode&sanitize=true" align=middle width=51.49221000000001pt height=13.387440000000009pt/>

### Analysis

**Within-cluster scatter** is the total squared distance between points <img src="tex/eb9d118bc54ee2366c55493ee8aabe04.svg?invert_in_darkmode&sanitize=true" align=middle width=14.950320000000008pt height=13.844159999999976pt/> and the centroid <img src="tex/9e98439d61e709ce950ff5b0fdc9f315.svg?invert_in_darkmode&sanitize=true" align=middle width=17.49330000000001pt height=13.387440000000009pt/> within the <img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39774000000001pt height=22.063469999999988pt/>th cluster: <p align="center"><img src="tex/7a7b3efd0eb9afced1843f00afee9e2c.svg?invert_in_darkmode&sanitize=true" align=middle width=93.10405499999999pt height=36.655409999999996pt/></p>

<img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39774000000001pt height=22.063469999999988pt/>-means clustering find the configuration <img src="tex/db23570dd407dca4b949935269d8d766.svg?invert_in_darkmode&sanitize=true" align=middle width=51.49221000000001pt height=13.387440000000009pt/> with the minimal total within-cluster scatter across all clusters. This is equivalent to maximising the inter-cluster scatter: the sum of the differences from each instance’s cluster’s centroid to the global centroid.

#### Does the algorithm work?

It terminates: it always finds a stable configuration. This is a local optimum, from which local changes cannot make further improvements. However, this is not necessarily the global optimum. To combat this, we can run the algorithm multiple times with different initialisation vectors, to find the best solution.

**<img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.39774000000001pt height=22.063469999999988pt/>-medoids** is a variant in which the cluster centre is chosen to be the data point in the cluster leading to the minimum within-cluster scatter, rather than taking the mean. This allows us to use distance metrics other than Euclidean distance, which can be overly affected by outliers.