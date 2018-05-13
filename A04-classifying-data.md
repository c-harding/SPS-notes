# Symbols, Patterns and Signals

## A4. Classifying Data

For a set of scalar values, the simplest summaries are the mean and variance:

**Mean:** <img src="tex/d77004cc242b85b415ca08ccd100f0fc.svg?invert_in_darkmode&sanitize=true" align=middle width=92.93262000000001pt height=42.70035000000001pt/>

**Variance:** <img src="tex/b9ee4866824d8bd3d2c7982457fd0e91.svg?invert_in_darkmode&sanitize=true" align=middle width=268.69919999999996pt height=42.70035000000001pt/>

### Estimates from a sample

The sample mean for <img src="tex/29fb78801f1c792da0c00b3ed4246275.svg?invert_in_darkmode&sanitize=true" align=middle width=19.73449500000001pt height=21.697829999999996pt/> samples is <img src="tex/5ae97bf40c67f319cc62ab53c390f849.svg?invert_in_darkmode&sanitize=true" align=middle width=111.315765pt height=31.488269999999968pt/>. As <img src="tex/5ff37d1f0d708cdd22fc6691116992c0.svg?invert_in_darkmode&sanitize=true" align=middle width=62.565360000000005pt height=21.697829999999996pt/>, <img src="tex/b9c21977d9f09f8cd23cae40a53489c8.svg?invert_in_darkmode&sanitize=true" align=middle width=45.19284000000001pt height=17.898869999999988pt/>.

The sample variance is likewise <img src="tex/51e53a30066b07e77f46d39adb554ec2.svg?invert_in_darkmode&sanitize=true" align=middle width=180.7344pt height=31.488269999999968pt/>. As <img src="tex/5ff37d1f0d708cdd22fc6691116992c0.svg?invert_in_darkmode&sanitize=true" align=middle width=62.565360000000005pt height=21.697829999999996pt/>, <img src="tex/fc2635040699190ee3922b67c588ede8.svg?invert_in_darkmode&sanitize=true" align=middle width=57.508275000000005pt height=25.994100000000007pt/>.

### Vectors

The mean vector is the sum of a collection of vectors, divided by the count, just like of scalars. <img src="tex/0c27dc68272b945b4888d9298d7950b7.svg?invert_in_darkmode&sanitize=true" align=middle width=58.768710000000006pt height=39.551489999999994pt/>.

The covariance is a matrix: <img src="tex/2e7a5e55ced7e4e0ce1a02ed1863749b.svg?invert_in_darkmode&sanitize=true" align=middle width=405.11625pt height=46.95933pt/>. The leading diagonal represents the variance in each dimension, and each other value is the covariance between components. The matrix is symmetrical across the leading diagonal.

Short notation: let <img src="tex/b0484ed4eca04432aaea07d2fcc1c994.svg?invert_in_darkmode&sanitize=true" align=middle width=68.265285pt height=18.41036999999999pt/> in <img src="tex/08591089ab83884d91e0e3eba6ccf1b1.svg?invert_in_darkmode&sanitize=true" align=middle width=196.56945000000002pt height=46.95933pt/>

      │ x  ┌     ┐      x │    ┌     ┐
      │x   │ + + │       x│    │ + - │
    ──x──  │ + + │      ──x──  │ - + │
     x│    └     ┘        │x   └     ┘
    x │                   │ x

      x    ┌     ┐        │    ┌     ┐
      x    │ 0 0 │        │    │ + 0 │
    ──x──  │ 0 + │      xxxxx  │ 0 0 │
      x    └     ┘        │    └     ┘
      x                   │  
      
    x │ x  ┌     ┐
     x│x   │ + 0 │
    ──x──  │ 0 + │
     x│x   └     ┘
    x │ x   

### Orientation and Spread

Assume all points lie on a line: <img src="tex/037fa6961f6d6c959349d91de0a8bc3d.svg?invert_in_darkmode&sanitize=true" align=middle width=62.86780500000001pt height=13.844159999999976pt/>, where <img src="tex/36bef777be1f81f983fd9021d07e8cdf.svg?invert_in_darkmode&sanitize=true" align=middle width=57.39970500000001pt height=23.889689999999977pt/>, <img src="tex/d96021bdacdf0e6d3d6baf31e5eee0ef.svg?invert_in_darkmode&sanitize=true" align=middle width=84.119805pt height=25.994100000000007pt/>

<img src="tex/2e6407b223f3ae0d0ea0ee964a617f39.svg?invert_in_darkmode&sanitize=true" align=middle width=331.74569999999994pt height=46.95933pt/>, where <img src="tex/7059ed61bd14072f575514680fec4882.svg?invert_in_darkmode&sanitize=true" align=middle width=97.12692pt height=42.70035000000001pt/>.

<img src="tex/50b03f3c329c19676fb445d8c8f7f89c.svg?invert_in_darkmode&sanitize=true" align=middle width=404.30609999999996pt height=46.95933pt/>

This means that, if all the points are in a straight line, <img src="tex/129c5b884ff47d80be4d6261a476e9f1.svg?invert_in_darkmode&sanitize=true" align=middle width=10.824495000000008pt height=13.844159999999976pt/> is an eigenvector, and <img src="tex/fd8be73b54f5436a5cd2e73ba9b6bfa9.svg?invert_in_darkmode&sanitize=true" align=middle width=9.911385000000008pt height=22.063469999999988pt/> is an eigenvalue, for the covariance matrix. This means that the orientation of the data is in the line <img src="tex/129c5b884ff47d80be4d6261a476e9f1.svg?invert_in_darkmode&sanitize=true" align=middle width=10.824495000000008pt height=13.844159999999976pt/>, and its spread in that direction is given by <img src="tex/2b7da88f9b0bf79a0b9a3f5bb699a6b6.svg?invert_in_darkmode&sanitize=true" align=middle width=23.610015000000004pt height=28.56545999999997pt/>.

For real 2D data, there are two such orthogonal eigenvector-eigenvalue pairs, which represent the principal axes of the data. The eccentricity of the data is the ratio of the larger of these eigenvalues to the smaller, and can be visualised by an ellipse with major and minor axes given by the larger and smaller eigenvector-eigenvalue products respectively.

### Outliers

Mean and variance become pretty inaccurate when outliers are present in the data. Outliers are a small number of points with values significantly different to the rest of the data. Likewise with vector data, they skew the vector mean and covariance. Alternatively, we can use the median value. This is the ‘middle’ value, or the midpoint of the two middle values if there are an even number of points. If the data is multidimensional, the median of each component is taken. However, the median is difficult to work with, e.g. the median of two sets cannot be defined in terms of the two sets' medians.

What about for the variance? Normally, the square of the difference between the value and the mean is used as the ‘variance kernel’, to calculate the variance. An outlier-resistant kernel could instead be used, which could flatten out at a given value. This is, however, also difficult to work with, especially with vector values.

### Location and spread

To find where the significant data is, and how spread out it is, in a numerical sequence, we can use the **centroid** (centre of mass) and the **moment of inertia** respectively.

For a 1D sequence <img src="tex/45d97e035705ae9f1182e42225f6c2f5.svg?invert_in_darkmode&sanitize=true" align=middle width=32.38488000000001pt height=23.889689999999977pt/>, <img src="tex/76c8a4215015e974b19128a62c339ebd.svg?invert_in_darkmode&sanitize=true" align=middle width=50.19283500000001pt height=20.419409999999996pt/>, where <img src="tex/a353d89506f9abd5b940bad37bbd7ca1.svg?invert_in_darkmode&sanitize=true" align=middle width=98.52628500000002pt height=38.569739999999996pt/>:

- centroid: <img src="tex/fac7b0d9849660975450ca0bd0434f38.svg?invert_in_darkmode&sanitize=true" align=middle width=124.94476499999998pt height=42.70035000000001pt/>
- moment of inertia: <img src="tex/b6318409f686538db49340906bcf979e.svg?invert_in_darkmode&sanitize=true" align=middle width=172.8903pt height=42.70035000000001pt/>

For a multi-dimensional sequence <img src="tex/c84fd9ebaa4d5f2a028c98f42365f125.svg?invert_in_darkmode&sanitize=true" align=middle width=37.967985000000006pt height=23.889689999999977pt/>:

- centroid: <img src="tex/e9910a56c5d47b922310a809957ff09c.svg?invert_in_darkmode&sanitize=true" align=middle width=135.39933000000002pt height=42.70035000000001pt/>
- moment of inertia: <img src="tex/7890312cf92fea8d757e12a9d0d1289d.svg?invert_in_darkmode&sanitize=true" align=middle width=245.4507pt height=42.70035000000001pt/>

The eigenvectors and eigenvalues of the moment of inertia define the orientation and spread of the data. Again, beware of outliers: could treat values below a certain threshold as zero.

The centroid and moment of inertia of a histogram are the same as the mean and covariance respectively of the underlying data.
