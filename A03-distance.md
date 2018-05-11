# Symbols, Patterns and Signals

## A3. Distance

Distance is a measure of separation between data. It can be defined for inividual data units, or for sequences/lists. It is important, as it allows for data to be ordered, and so allows numeric calculations.

### Distance measure

For a distance measure <img src="tex/e3e57af6c1c20313ddc1ed85ee3abd7c.svg?invert_in_darkmode&sanitize=true" align=middle width=49.90149779999999pt height=24.65753399999998pt/> to be valid, it must have the following properties:

- nonnegativity: <img src="tex/6d7fe8f48e3609aa4b912160faf7bf2b.svg?invert_in_darkmode&sanitize=true" align=middle width=58.12070714999999pt height=24.65753399999998pt/>
- reflexivity: <img src="tex/41541533eaff49d276b52e461451dacd.svg?invert_in_darkmode&sanitize=true" align=middle width=143.2705197pt height=24.65753399999998pt/>
- symmetry: <img src="tex/fa151dda85ee9073aba955b1dfc4911c.svg?invert_in_darkmode&sanitize=true" align=middle width=121.72062704999999pt height=24.65753399999998pt/>
- triangle inequality: <img src="tex/76326c2886282ae0bb4e100d87e30b17.svg?invert_in_darkmode&sanitize=true" align=middle width=168.27934364999996pt height=24.65753399999998pt/>

### Numeric data

The typical distance measure used for numeric data is Euclidean distance (straight-line distance): <p align="center"><img src="tex/97573c4eeeb4f926d1bbf644501a15f0.svg?invert_in_darkmode&sanitize=true" align=middle width=353.41867605pt height=55.509229049999995pt/></p>

This can be extended to <img src="tex/bfb6e556d3874a3157379133a8d7917a.svg?invert_in_darkmode&sanitize=true" align=middle width=18.45327164999999pt height=22.465723500000017pt/> norm/Minkowski distances: <p align="center"><img src="tex/6eb277cbc69a8776c724c3b49b953874.svg?invert_in_darkmode&sanitize=true" align=middle width=219.33779174999998pt height=55.509229049999995pt/></p>

Special cases of this include <img src="tex/61d5974753c6aba73418ea29b31f7808.svg?invert_in_darkmode&sanitize=true" align=middle width=38.40740639999999pt height=21.18721440000001pt/> (Manhattan distance: sum of differences), <img src="tex/90264925fb137831c8f410cd14c75cff.svg?invert_in_darkmode&sanitize=true" align=middle width=38.40740639999999pt height=21.18721440000001pt/> (Euclidean distance, as above), <img src="tex/2f6cebdb6c3c548301c28df275d905c2.svg?invert_in_darkmode&sanitize=true" align=middle width=46.62660089999999pt height=14.15524440000002pt/> (max-norm: maximum difference)

#### Weighted distance

Sometimes we want to weight the different dimensions differently. If we have a vector <img src="tex/31fae8b8b78ebe01cbfbe2fe53832624.svg?invert_in_darkmode&sanitize=true" align=middle width=12.210846449999991pt height=14.15524440000002pt/> of weights, the distance can be calculated with <p align="center"><img src="tex/fedd010168beecb6f0e86464ebacfd15.svg?invert_in_darkmode&sanitize=true" align=middle width=403.39004639999996pt height=55.509229049999995pt/></p>

The matrix form <img src="tex/380c103b60c66d6420ec8923cdc6e6e8.svg?invert_in_darkmode&sanitize=true" align=middle width=19.80585089999999pt height=22.55708729999998pt/> is a diagonal form of the vector <img src="tex/31fae8b8b78ebe01cbfbe2fe53832624.svg?invert_in_darkmode&sanitize=true" align=middle width=12.210846449999991pt height=14.15524440000002pt/>. For example, <img src="tex/31fae8b8b78ebe01cbfbe2fe53832624.svg?invert_in_darkmode&sanitize=true" align=middle width=12.210846449999991pt height=14.15524440000002pt/> may be <img src="tex/f573e966f29e96dd26a18ca812b3efbf.svg?invert_in_darkmode&sanitize=true" align=middle width=140.42801685pt height=28.894955100000008pt/>, so that each dimension has unit invariance. 

Alternatively, to eliminate correlations between features, we can set <img src="tex/84c95f91a742c9ceb460a83f9b5090bf.svg?invert_in_darkmode&sanitize=true" align=middle width=17.80826024999999pt height=22.465723500000017pt/> to the inverse of the covariance matrix. This is known as the **Mahalanobis distance**.

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

To compare two sequences, we can compare the difference between each point (normalised for mean and variation: <img src="tex/2870e18dfbb4c1fe274682f0f4a75dc5.svg?invert_in_darkmode&sanitize=true" align=middle width=90.99228929999998pt height=24.65753399999998pt/>). Multiplying each pair together and taking the average is a good way to find how similar the sequences are.

<p align="center"><img src="tex/ed3a3a116e720f8e2469d9e572e5b966.svg?invert_in_darkmode&sanitize=true" align=middle width=261.00386564999997pt height=41.10931275pt/></p>

However, this does not account for a shift between the sequences. To do this, find the maximum value of <img src="tex/94c36683602b3f3f15fc16551809bf0f.svg?invert_in_darkmode&sanitize=true" align=middle width=22.17673259999999pt height=14.15524440000002pt/>:

<p align="center"><img src="tex/21f40f6ef69475dcff649c3cf4b8c489.svg?invert_in_darkmode&sanitize=true" align=middle width=310.4637591pt height=41.10931275pt/></p>

There is still nothing to account for time compression/warping, for which we use **Dynamic Time Warping** (DTW). Given inputs <img src="tex/6dbb78540bd76da3f1625782d42d6d16.svg?invert_in_darkmode&sanitize=true" align=middle width=9.41027339999999pt height=14.15524440000002pt/> and <img src="tex/6c4adbc36120d62b98deef2a20d5d303.svg?invert_in_darkmode&sanitize=true" align=middle width=8.55786029999999pt height=14.15524440000002pt/> of length <img src="tex/47fb7e3ce83222b949d5f7e44e0a08e0.svg?invert_in_darkmode&sanitize=true" align=middle width=17.63902799999999pt height=14.15524440000002pt/> and <img src="tex/da6bcff3e68efc4ff1c088e75a8eb2ac.svg?invert_in_darkmode&sanitize=true" align=middle width=16.85513774999999pt height=14.15524440000002pt/>, <img src="tex/2ec6e630f199f589a2402fdf3e0289d5.svg?invert_in_darkmode&sanitize=true" align=middle width=8.270567249999992pt height=14.15524440000002pt/> is a sequence of length <img src="tex/0e51a2dede42189d77627c4d742822c3.svg?invert_in_darkmode&sanitize=true" align=middle width=14.433101099999991pt height=14.15524440000002pt/> such that

- <img src="tex/24064ab42b8f69d06363d709a76a23a9.svg?invert_in_darkmode&sanitize=true" align=middle width=74.09239199999999pt height=24.65753399999998pt/>
- <img src="tex/0cc39667b40e7c36da29f9d643747d83.svg?invert_in_darkmode&sanitize=true" align=middle width=98.90427524999997pt height=24.65753399999998pt/>
- for each <img src="tex/c235e81aed1a774e997070b9988349db.svg?invert_in_darkmode&sanitize=true" align=middle width=73.73649359999997pt height=22.831056599999986pt/>, given <img src="tex/7c3624ca04cfa2718ddfb05bf0c392a6.svg?invert_in_darkmode&sanitize=true" align=middle width=76.41165179999999pt height=24.65753399999998pt/>,  
  <img src="tex/31ac9030a36cb09fcdd77df32acc5485.svg?invert_in_darkmode&sanitize=true" align=middle width=311.79187379999996pt height=24.65753399999998pt/>

**DTW distance**: <img src="tex/6e6b9791cfce5269b8c1598d4839194a.svg?invert_in_darkmode&sanitize=true" align=middle width=64.35493514999999pt height=24.65753399999998pt/>, where <img src="tex/2d6b076580ca4c1a5245e050837d9ce1.svg?invert_in_darkmode&sanitize=true" align=middle width=158.80810935pt height=24.65753399999998pt/>
