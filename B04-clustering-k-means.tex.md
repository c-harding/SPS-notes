# Symbols, Patterns and Signals

## B4. Clustering: *k*-means

Clustering involves segmenting the instance space into regions of similar objects. There is no supervision in the learning: the regions are not labelled. We can use a distance metric for clustering. If we have $k$ clusters, this is known as **$k$-means clustering**.

function $\mathsf{kmeans}(xs, k)$

1. randomly initialise $k$ vectors $\mathbf μ_1, \dots, \mathbf μ_k$
2. **repeat until** each $\mathbf μ_i$ has stopped changing:
   1. assign each $\mathbf x \in xs$ to the nearest $\mathbf μ_j$
   2. recompute each $\mathbf μ_j$ as the mean of the instances assigned to it
3. **return** $\mathbf μ_1, \dots, \mathbf μ_k$

### Analysis

**Within-cluster scatter** is the total squared distance between points $\mathbf x_i$ and the centroid $\mu_k$ within the $k$th cluster: $$\sum_i\left\|\mathbf x_i-\mathbf μ_k\right\|^2$$

$k$-means clustering find the configuration $\mathbf μ_1, \dots, \mathbf μ_k$ with the minimal total within-cluster scatter across all clusters. This is equivalent to maximising the inter-cluster scatter: the sum of the differences from each instance’s cluster’s centroid to the global centroid.

#### Does the algorithm work?

It terminates: it always finds a stable configuration. This is a local optimum, from which local changes cannot make further improvements. However, this is not necessarily the global optimum. To combat this, we can run the algorithm multiple times with different initialisation vectors, to find the best solution.

**$k$-medoids** is a variant in which the cluster centre is chosen to be the data point in the cluster leading to the minimum within-cluster scatter, rather than taking the mean. This allows us to use distance metrics other than Euclidean distance, which can be overly affected by outliers.