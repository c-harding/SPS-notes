# Symbols, Patterns and Signals

## A7. Maximum Likelihood and Maximum a Posteriori estimation

Maximum likelihood instructions:

1. Determine <img src="tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.49583350000001pt height=22.063469999999988pt/>, <img src="tex/78ec2b7008296ce0561cf83393cb746d.svg?invert_in_darkmode&sanitize=true" align=middle width=14.388495000000008pt height=21.697829999999996pt/> and an expression for likelihood <img src="tex/be133e90bb7dc225c29fd23c55145668.svg?invert_in_darkmode&sanitize=true" align=middle width=57.316545000000005pt height=23.889689999999977pt/>
2. Take the natural log of the likelihood
   $$\arg\max_\theta p(D\mid\theta) = \arg\max_\theta\ln p(D\mid\theta)$$
   $$\arg\max_\theta p(D\mid\theta) = \arg\min_\theta\left(-\ln p(D\mid\theta)\right)$$
3. Take the derivative/partial derivatives of <img src="tex/4d2f698956e0aff9eb0ae7e3ca14e83d.svg?invert_in_darkmode&sanitize=true" align=middle width=73.754835pt height=23.889689999999977pt/> with respect to <img src="tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.49583350000001pt height=22.063469999999988pt/>.
4. Set the derivative(s) to zero, and solve for <img src="tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.49583350000001pt height=22.063469999999988pt/>.

While this gives the same solution as the deterministic approach, it tells us more information. For example, how much <img src="tex/b7ead6365bcea1f706f456ed3aea9b0d.svg?invert_in_darkmode&sanitize=true" align=middle width=31.799295000000008pt height=13.387440000000009pt/> varies for different data sets, i.e. how reliable it is.

<p align="center"><img src="tex/d83852ae8613bccff1841403793f11c6.svg?invert_in_darkmode&sanitize=true" align=middle width=235.7421pt height=29.589285pt/></p>

<p align="center"><img src="tex/df4505f463f76e1faf4308308c960456.svg?invert_in_darkmode&sanitize=true" align=middle width=174.64095pt height=29.589285pt/></p>

The more recordings/the larger the values of <img src="tex/332cc365a4987aacce0ead01b8bdcc0b.svg?invert_in_darkmode&sanitize=true" align=middle width=9.717345000000009pt height=13.387440000000009pt/>, the smaller the variance.

### Maximum a Posteriori estimation

ML does not take into account any prior information we have about the relative distribution of <img src="tex/27e556cf3caa0673ac49a8f0de3c73ca.svg?invert_in_darkmode&sanitize=true" align=middle width=8.49583350000001pt height=22.063469999999988pt/>. That is, it assumes that all outcomes are equally likely before considering the values.

MAP estimate: <img src="tex/6f0dc4d1756b5aadcf27eb6005abd3c5.svg?invert_in_darkmode&sanitize=true" align=middle width=155.11914000000002pt height=23.889689999999977pt/>

If <img src="tex/0d3b1c8bc45ee48700a21f044adb8cba.svg?invert_in_darkmode&sanitize=true" align=middle width=29.55183000000001pt height=23.889689999999977pt/> is constant (all outcomes are equally likely), then this simplifies down to ML.
