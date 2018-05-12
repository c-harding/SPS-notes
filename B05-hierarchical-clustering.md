# Symbols, Patterns and Signals

## B5. Hierarchical Clustering

Agglomerative hierarchical clustering: iteratively merging the closest pair of clusters:

- Start off with <img src="/tex/55a049b8f161ae7cfeb0197d75aff967.svg?invert_in_darkmode&sanitize=true" align=middle width=9.86687624999999pt height=14.15524440000002pt/> points, each in its own cluster. Generate an <img src="/tex/2be744f3276b5219af5f8dd5f793e02c.svg?invert_in_darkmode&sanitize=true" align=middle width=39.82494449999999pt height=19.1781018pt/> matrix <img src="/tex/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode&sanitize=true" align=middle width=14.06623184999999pt height=22.465723500000017pt/> of all pairwise distances, for example Euclidean distances.
- Let <img src="/tex/bb641b192184a764f15d07e57c69ac7c.svg?invert_in_darkmode&sanitize=true" align=middle width=134.52115709999998pt height=22.465723500000017pt/>, so <img src="/tex/eb9d118bc54ee2366c55493ee8aabe04.svg?invert_in_darkmode&sanitize=true" align=middle width=14.628015599999989pt height=14.611878600000017pt/> and <img src="/tex/6105f6b0adb44cb618b24d66255742da.svg?invert_in_darkmode&sanitize=true" align=middle width=16.08162434999999pt height=14.611878600000017pt/> are the closest pair of clusters.
- Merge <img src="/tex/eb9d118bc54ee2366c55493ee8aabe04.svg?invert_in_darkmode&sanitize=true" align=middle width=14.628015599999989pt height=14.611878600000017pt/> and <img src="/tex/6105f6b0adb44cb618b24d66255742da.svg?invert_in_darkmode&sanitize=true" align=middle width=16.08162434999999pt height=14.611878600000017pt/> into a new cluster <img src="/tex/30ce1f0554130108252e74028d4c4ae1.svg?invert_in_darkmode&sanitize=true" align=middle width=13.76707859999999pt height=24.7161288pt/>.
- Recompute the new distance matrix <img src="/tex/0e1538e015e88e0782ca754fc9e9959e.svg?invert_in_darkmode&sanitize=true" align=middle width=17.85619274999999pt height=24.7161288pt/> (see the [Linkage](#linkage) section).
- Iterate until one cluster remains.
- Output a [dendrogram](#dendrograms).

There is no need to know the number of clusters in advance, as the dendrogram contains information for every level. However, they're not great for efficiency: <img src="/tex/a737d3668bdf58070d096a833e4dee33.svg?invert_in_darkmode&sanitize=true" align=middle width=43.570210199999984pt height=26.76175259999998pt/> to <img src="/tex/02a611ccec884859ffca48621e9cf38b.svg?invert_in_darkmode&sanitize=true" align=middle width=80.14931429999999pt height=26.76175259999998pt/>. The algorithm also has no preprocessing, so all the processing has to be repeated for any change in input set.

### Linkage

There are different ways to determine the distance between two clusters:

- **Single linkage**: the minimum distance of a pair from each cluster
- **Complete linkage**: the maximum distance of a pair from each cluster
- **Average linkage**: the average distance of all pairs from each cluster
- **Centroid linkage**: the distance between the centroid of each cluster

### Dendrograms

A dendrogram is a tree where each node represents a merge of two clusters. Each node has a height, representing the distance between the clusters. The tree can then be cut at the desired number of clusters.

![A dendrogram](B05-single-linkage-dendrogram.png)  
An example of clustering one-dimensional data, using single linkage. The nodes are labelled with their heights.

### Silhouettes

<img src="/tex/0786a7b732d7242200d22552fe3630f1.svg?invert_in_darkmode&sanitize=true" align=middle width=30.869576099999993pt height=24.65753399999998pt/> is the average distance from a point to others in its cluster. <img src="/tex/dfe1b1c707e7d2ffd71fdb37b9b32166.svg?invert_in_darkmode&sanitize=true" align=middle width=29.23521809999999pt height=24.65753399999998pt/> is the average distance from a point to others in the nearest cluster.

The silhouette <img src="/tex/302165bc0ba8e7da0fed64171b167db8.svg?invert_in_darkmode&sanitize=true" align=middle width=252.98113995000003pt height=24.65753399999998pt/> should be large.

![Plots of 2D data, a dendrogram, and the silhouettes](B05-silhouette-plots.png)

Here, the rapidly decreasing silhouette values show that the clusters are not very strong. The negative value of one of the points shows that is has been grouped in the wrong cluster: it is on average closer to the points in the nearest cluster than those in its own.