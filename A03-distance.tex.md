# Symbols, Patterns and Signals

## A3. Distance

Distance is a measure of separation between data. It can be defined for inividual data units, or for sequences/lists. It is important, as it allows for data to be ordered, and so allows numeric calculations.

### Distance measure

For a distance measure $D(a,b)$ to be valid, it must have the following properties:

- nonnegativity: $D(a,b) ≥ 0$
- reflexivity: $D(a,b) = 0 \Leftrightarrow a = b$
- symmetry: $D(a,b) = D(b,a)$
- triangle inequality: $D(a,b) + D(b,c) ‏≥ D(a,c)$

### Numeric data

The typical distance measure used for numeric data is Euclidean distance (straight-line distance): $$D(\mathbf{u},\mathbf{v}) = (\mathbf{u}-\mathbf{v})^T(\mathbf{u}-\mathbf{v}) = \left(\sum_i(u_i-v_i)^2\right)^{^1/_2}$$

This can be extended to P-norm distances: $$L_p(\mathbf{u},\mathbf{v}) = \left(\sum_i(u_i-v_i)^p\right)^{^1/_p}$$

Special cases of this include $p=1$ (Manhattan distance: sum of differences), $p=2$ (Euclidean distance, as above), $p=\infty$ (max-norm: maximum difference)

#### Weighted distance

Sometimes we want to weight the different dimensions differently. If we have a vector $w$ of weights, the distance can be calculated with $$D_w(\mathbf{u},\mathbf{v}) =(\mathbf{u}-\mathbf{v})^T\mathbf{W}(\mathbf{u}-\mathbf{v}) = \left(\sum_i w_i(u_i-v_i)^2\right)^{^1/_2}$$

The matrix form $\mathbf{W}$ is a diagonal form of the vector $w$.

### Symbolic distances

Distance between symbolic data is less well-defined. E.g. between words, the difference could be between spelling (syntactic distance) or meaning (semantic distance). The former is simpler, but has limited application. The latter is much harder, except for limited applications (e.g. ordered attributes: *small*, *medium*, *large*).

#### Syntactic distances

**Hamming distance**: defined for symbolic sequences of equal length. It represents the number of positions at which the string is different. 

    (BRISTOL, BLISTER): 3
    (ASLEEP, SLEEPS): 5

**Edit distance**: defined for symbolic sequences of possibly differing length. It represents the minimum number of edits (insertions, deletions, substitutions) needed to transform one into the other.

    (BRISTOL, BLISTER): 3
    (ASLEEP, SLEEP): 1
    (ASLEEP, SLEEPS): 2

#### Semantic distances

A semantic distance can be derived from hierarchies of words, as assembled by humans, e.g. WordNet. These contain many synsets (sets of synonyms), and relationships between them (hyponymy: is-a; meronymy: part-of).

An example of such a distance is the *WUP* distance, named after Wu and Palmer. It represents the length of the path from the root word to the common ancestor, scaled by the sum of the path lengths from the root to the two words.

### Sequential distances

To compare two sequences, we can compare the difference between each point (normalised for mean and variation: $(x_i-\mu_x)/\sigma_x$). Multiplying each pair together and taking the average is a good way to find how similar the sequences are.

$$c_{uv} = \frac{1}{N\sigma_u\sigma_v}\sum_i\left(u_i-\mu_u\right)\left(v_i-\mu_v\right)$$

However, this does not account for a shift between the sequences. To do this, find the maximum value of $r_{uv}$:

$$r_{uv}(m) = \frac{1}{N\sigma_u\sigma_v}\sum_i\left(u_i-\mu_u\right)\left(v_{i-m}-\mu_v\right)$$

There is still nothing to account for time compression/warping, for which we use **Dynamic Time Warping** (DTW). Given inputs $u$ and $v$ of length $n_u$ and $n_v$, $p$ is a sequence of length $m$ such that

- $p_1 = (1,1)$
- $p_m = (n_u,n_v)$
- for each $k < m-1$, given $p_k = (x,y)$,  
  $p_{k+1} \in \left\{(x+1,y),(x+1,y+1),(x,y+1)\right\}$

**DTW distance**: $C_{p^*}(x,y)$, where $p^* = \arg\min_pC_p(x,y)$
