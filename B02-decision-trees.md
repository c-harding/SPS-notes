# Symbols, Patterns and Signals

## B2. Decision trees

This method deterministically builds a model to separate into classes based on the training set. It is then adapted with a test set to avoid overfitting and to improve generalisation.

The tree consists of nodes, labelled by features; branches, labelled with values (or ranges) of their parent's feature; and leaves, each labelled with a class.

**Algorithm <img src="tex/e1187a9eb2ca9705c38ba9fcc89a2fa8.svg?invert_in_darkmode&sanitize=true" align=middle width=112.62806774999999pt height=24.65753399999998pt/>:**

To grow a tree, we start with a set of data <img src="tex/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode&sanitize=true" align=middle width=14.06623184999999pt height=22.465723500000017pt/> and a set of features <img src="tex/b8bc815b5e9d5177af01fd4d3d3c2f10.svg?invert_in_darkmode&sanitize=true" align=middle width=12.85392569999999pt height=22.465723500000017pt/>. We will output a feature tree <img src="tex/2f118ee06d05f3c2d98361d9c30e38ce.svg?invert_in_darkmode&sanitize=true" align=middle width=11.889314249999991pt height=22.465723500000017pt/>, as described above.

1. if <img src="tex/3edc7af54eab44d6c78d5a26d980526e.svg?invert_in_darkmode&sanitize=true" align=middle width=122.33130854999999pt height=24.65753399999998pt/> then return <img src="tex/6ac84a27072f36ce9694461f017df535.svg?invert_in_darkmode&sanitize=true" align=middle width=63.83804129999999pt height=24.65753399999998pt/>
2. let <img src="tex/350e5f23984faabe02b3ca08d216e728.svg?invert_in_darkmode&sanitize=true" align=middle width=141.87435075pt height=24.65753399999998pt/>
3. split <img src="tex/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode&sanitize=true" align=middle width=14.06623184999999pt height=22.465723500000017pt/> into subsets <img src="tex/3bdf20a1d3bb8900a92e3b28088057f1.svg?invert_in_darkmode&sanitize=true" align=middle width=18.26049554999999pt height=22.465723500000017pt/> according to the literals in <img src="tex/e257acd1ccbe7fcb654708f1a866bfe9.svg?invert_in_darkmode&sanitize=true" align=middle width=11.027402099999989pt height=22.465723500000017pt/>
4. for each <img src="tex/77a3b857d53fb44e33b53e4c8b68351a.svg?invert_in_darkmode&sanitize=true" align=middle width=5.663225699999989pt height=21.68300969999999pt/>
   1. let $\displaystyle T_i = \begin{cases}\mathsf{GrowTree}(D_i,F),&\text{if }D_i \ne \varnothing\\\mathsf{Leaf}(\mathsf{Label}(D)),&\text{otherwise}\end{cases}$
5. return a node labelled <img src="tex/e257acd1ccbe7fcb654708f1a866bfe9.svg?invert_in_darkmode&sanitize=true" align=middle width=11.027402099999989pt height=22.465723500000017pt/>, with branches <img src="tex/96f2b018aaa9578a374cdb19c7c1ac3b.svg?invert_in_darkmode&sanitize=true" align=middle width=25.02512429999999pt height=22.831056599999986pt/> to nodes <img src="tex/c4b26722bc62f8e067ee4f8ef384944c.svg?invert_in_darkmode&sanitize=true" align=middle width=33.61898429999999pt height=22.831056599999986pt/>.

- <img src="tex/3edc7af54eab44d6c78d5a26d980526e.svg?invert_in_darkmode&sanitize=true" align=middle width=122.33130854999999pt height=24.65753399999998pt/> returns true iff the instances in <img src="tex/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode&sanitize=true" align=middle width=14.06623184999999pt height=22.465723500000017pt/> all share a label, so D can be labelled with as such.
- <img src="tex/6ac84a27072f36ce9694461f017df535.svg?invert_in_darkmode&sanitize=true" align=middle width=63.83804129999999pt height=24.65753399999998pt/> returns the most appropriate label for the set of instances <img src="tex/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode&sanitize=true" align=middle width=14.06623184999999pt height=22.465723500000017pt/>.
- <img src="tex/04d2ef72fb296e1001562cdda69cf9cb.svg?invert_in_darkmode&sanitize=true" align=middle width=108.92933699999998pt height=24.65753399999998pt/> returns the best set of literals to be put at the root of the tree.

### Finding the best split

Suppose a node with <img src="tex/f9c4988898e7f532b9f826a75014ed3c.svg?invert_in_darkmode&sanitize=true" align=middle width=14.99998994999999pt height=22.465723500000017pt/> instances is split into <img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/> nodes, with <img src="tex/de3e4ddbaf93c2db6b330ad1998cc995.svg?invert_in_darkmode&sanitize=true" align=middle width=14.517775799999992pt height=14.15524440000002pt/> instances each (<img src="tex/6167f6ecd3000aff1c37f3441880223a.svg?invert_in_darkmode&sanitize=true" align=middle width=80.43654959999999pt height=32.51169900000002pt/>). The information gain of a split can be calculated as the decrease in impurity going from the parent parent to children.
<p align="center"><img src="tex/72d9a0589081b13183d7a82d44b18595.svg?invert_in_darkmode&sanitize=true" align=middle width=243.8405838pt height=47.93392394999999pt/></p>

A node has less impurity when its instances are closer to being homogenous.

If we have <img src="tex/3e18a4a28fdee1744e5e3f79d13b9ff6.svg?invert_in_darkmode&sanitize=true" align=middle width=7.11380504999999pt height=14.15524440000002pt/> different classes, and the proportion of class <img src="tex/36b5afebdba34564d884d347484ac0c7.svg?invert_in_darkmode&sanitize=true" align=middle width=7.710416999999989pt height=21.68300969999999pt/> in a set is <img src="tex/7f131a60c8e7bb2b22f383f7bd49e2c0.svg?invert_in_darkmode&sanitize=true" align=middle width=14.37507554999999pt height=14.15524440000002pt/>, then the impurity of that set can be measured with entropy: <p align="center"><img src="tex/dc16f4f3bd0060ba2faabcc38e961488.svg?invert_in_darkmode&sanitize=true" align=middle width=102.92816655pt height=47.1348339pt/></p>

But what does this **entropy** mean? <img src="tex/36ed306e4c4c6bba92bf302a03716f49.svg?invert_in_darkmode&sanitize=true" align=middle width=61.24719809999999pt height=22.831056599999986pt/> measures the information content, in bits, of an event occurring with probability <img src="tex/7f131a60c8e7bb2b22f383f7bd49e2c0.svg?invert_in_darkmode&sanitize=true" align=middle width=14.37507554999999pt height=14.15524440000002pt/>. E.g. if an event occurs 25% of the time, there are <img src="tex/f5abf034bd2109d15c203ff770be6e24.svg?invert_in_darkmode&sanitize=true" align=middle width=102.57527609999998pt height=27.94539330000001pt/> bits of information.

<img src="tex/3923e1fa3097936000342b569cb1d258.svg?invert_in_darkmode&sanitize=true" align=middle width=103.46188049999998pt height=24.657735299999988pt/> is the average information content per event, or the ‘randomness’ of the distribution. The entropy is maximal for uniform distributions, and minimal (i.e. zero) iff <img src="tex/61d276b9c3a3a9e7ace6e7deb263d094.svg?invert_in_darkmode&sanitize=true" align=middle width=70.39587884999999pt height=22.831056599999986pt/>. For two mutually exclusive classes, the entropy is <img src="tex/fab97832111721e6c374c2614f44ceaa.svg?invert_in_darkmode&sanitize=true" align=middle width=243.08211674999998pt height=24.65753399999998pt/>.

In this case, we use entropy to measure how much additional information a particular split tells us about the class.

What about for numerical features? Instead of enumerating every possibility, we choose a threshold that maximises the information gain.

### Pruning the tree

Once we have built the tree, our model will achieve perfect accuracy on the training set. However, this is because we have overfitted. In order to improve generalisation, we prune the tree back, using a separate test set.

1. unmark all leaves
2. choose a current, unmarked leaf <img src="tex/2f2322dff5bde89c37bcae4116fe20a8.svg?invert_in_darkmode&sanitize=true" align=middle width=5.2283516999999895pt height=22.831056599999986pt/>
3. mark <img src="tex/2f2322dff5bde89c37bcae4116fe20a8.svg?invert_in_darkmode&sanitize=true" align=middle width=5.2283516999999895pt height=22.831056599999986pt/>
5. let <img src="tex/f9c4988898e7f532b9f826a75014ed3c.svg?invert_in_darkmode&sanitize=true" align=middle width=14.99998994999999pt height=22.465723500000017pt/> be the parent of <img src="tex/2f2322dff5bde89c37bcae4116fe20a8.svg?invert_in_darkmode&sanitize=true" align=middle width=5.2283516999999895pt height=22.831056599999986pt/>
5. let <img src="tex/c745b9b57c145ec5577b82542b2df546.svg?invert_in_darkmode&sanitize=true" align=middle width=10.57650494999999pt height=14.15524440000002pt/> be the test set accuracy of the current tree
6. let <img src="tex/8217ed3c32a785f0b5aad4055f432ad8.svg?invert_in_darkmode&sanitize=true" align=middle width=10.16555099999999pt height=22.831056599999986pt/> be the test set accuracy if <img src="tex/f9c4988898e7f532b9f826a75014ed3c.svg?invert_in_darkmode&sanitize=true" align=middle width=14.99998994999999pt height=22.465723500000017pt/> and its children are replaced by a leaf, labelled with the most frequent class among <img src="tex/f9c4988898e7f532b9f826a75014ed3c.svg?invert_in_darkmode&sanitize=true" align=middle width=14.99998994999999pt height=22.465723500000017pt/>’s training instances
7. if <img src="tex/d5f2466db584f693401f531195a9266c.svg?invert_in_darkmode&sanitize=true" align=middle width=42.65968079999999pt height=22.831056599999986pt/> then prune (replace the subtree with a leaf)
8. if there are still unmarked leaves, go to 2.
