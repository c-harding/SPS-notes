# Symbols, Patterns and Signals

## B2. Decision trees

This method deterministically builds a model to separate into classes based on the training set. It is then adapted with a test set to avoid overfitting and to improve generalisation.

The tree consists of nodes, labelled by features; branches, labelled with values (or ranges) of their parent's feature; and leaves, each labelled with a class.

**Algorithm $\textsf{GrowTree}(D,F)$:**

To grow a tree, we start with a set of data $D$ and a set of features $F$. We will output a feature tree $T$, as described above.

1. if $\mathsf{Homogeneous}(D)$ then return $\mathsf{Label}(D)$
2. let $S = \mathsf{BestSplit}(D,F)$
3. split $D$ into subsets $D_i$ according to the literals in $S$
4. for each $i$
   1. let $\displaystyle T_i = \begin{cases}\mathsf{GrowTree}(D_i,F),&\text{if }D_i \ne \varnothing\\\mathsf{Leaf}(\mathsf{Label}(D)),&\text{otherwise}\end{cases}$
5. return a node labelled $S$, with branches $\forall i. i$ to nodes $\forall i. T_i$.

- $\mathsf{Homogeneous}(D)$ returns true iff the instances in $D$ all share a label, so D can be labelled with as such.
- $\mathsf{Label}(D)$ returns the most appropriate label for the set of instances $D$.
- $\mathsf{BestSplit}(D,F)$ returns the best set of literals to be put at the root of the tree.

### Finding the best split

Suppose a node with $N$ instances is split into $k$ nodes, with $n_i$ instances each ($\sum_i^k n_i = N$). The information gain of a split can be calculated as the decrease in impurity going from the parent parent to children.
$$\mathsf{Imp}(Parent) - \sum_i^k\frac{n_i}N\mathsf{Imp}(Child_i)$$

A node has less impurity when its instances are closer to being homogenous.

If we have $c$ different classes, and the proportion of class $j$ in a set is $p_j$, then the impurity of that set can be measured with entropy: $$\sum_{j=1}^c-p_j\log_2p_j$$

But what does this **entropy** mean? $-\log_2p_j$ measures the information content, in bits, of an event occurring with probability $p_j$. E.g. if an event occurs 25% of the time, there are $-\log_2\left(\frac14\right) = 2$ bits of information.

$\sum_j-p_j\log_2p_j$ is the average information content per event, or the ‘randomness’ of the distribution. The entropy is maximal for uniform distributions, and minimal (i.e. zero) iff $\exists!j. p_j\ne0$. For two mutually exclusive classes, the entropy is $-p_1\log_2p_1-(1-p_1)\log_2(1-p_1)$.

In this case, we use entropy to measure how much additional information a particular split tells us about the class.

What about for numerical features? Instead of enumerating every possibility, we choose a threshold that maximises the information gain.

### Pruning the tree

Once we have built the tree, our model will achieve perfect accuracy on the training set. However, this is because we have overfitted. In order to improve generalisation, we prune the tree back, using a separate test set.

1. unmark all leaves
2. choose a current, unmarked leaf $l$
3. mark $l$
5. let $N$ be the parent of $l$
5. let $\alpha$ be the test set accuracy of the current tree
6. let $\beta$ be the test set accuracy if $N$ and its children are replaced by a leaf, labelled with the most frequent class among $N$’s training instances
7. if $\alpha < \beta$ then prune (replace the subtree with a leaf)
8. if there are still unmarked leaves, go to 2.