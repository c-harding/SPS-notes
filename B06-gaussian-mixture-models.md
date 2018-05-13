# Symbols, Patterns and Signals

## B6. Gaussian Mixture Models

This is another method for performing clustering, and it works by modelling each cluster as a multivariate normal distribution, with its own mean and covariance matrix. This is the equivalent of maximum-likelihood estimation, but we don’t have the means/covariances.

We treat cluster membership as a continuous hidden variable. This similar to <img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-means, except <img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/>-means has discrete Bernoulli cluster membership.

We solve this using the general algorithm called **Expectation-Maximisation** (EM).

### ML example

Suppose <img src="tex/44bc9d542a92714cac84e01cbbb7fd61.svg?invert_in_darkmode&sanitize=true" align=middle width=8.689230000000004pt height=14.155350000000013pt/> students received an A, <img src="tex/4bdc8d9bcfb35e1c9bfb51fc69687dfc.svg?invert_in_darkmode&sanitize=true" align=middle width=7.054855500000005pt height=22.831379999999992pt/> students got a B, <img src="tex/3e18a4a28fdee1744e5e3f79d13b9ff6.svg?invert_in_darkmode&sanitize=true" align=middle width=7.11380504999999pt height=14.15524440000002pt/> got a C, and <img src="tex/2103f85b8b1477f430fc407cad462224.svg?invert_in_darkmode&sanitize=true" align=middle width=8.556075000000003pt height=22.831379999999992pt/> got a D, where we know the values of <img src="tex/44bc9d542a92714cac84e01cbbb7fd61.svg?invert_in_darkmode&sanitize=true" align=middle width=8.689230000000004pt height=14.155350000000013pt/>, <img src="tex/4bdc8d9bcfb35e1c9bfb51fc69687dfc.svg?invert_in_darkmode&sanitize=true" align=middle width=7.054855500000005pt height=22.831379999999992pt/>, <img src="tex/3e18a4a28fdee1744e5e3f79d13b9ff6.svg?invert_in_darkmode&sanitize=true" align=middle width=7.11380504999999pt height=14.15524440000002pt/> and <img src="tex/2103f85b8b1477f430fc407cad462224.svg?invert_in_darkmode&sanitize=true" align=middle width=8.556075000000003pt height=22.831379999999992pt/>. We also know that <img src="tex/96959448a716b07f898d9ec92b496b5f.svg?invert_in_darkmode&sanitize=true" align=middle width=62.45778pt height=27.775769999999994pt/>, <img src="tex/11e49a4ba829bcfe13782a1a837ad01b.svg?invert_in_darkmode&sanitize=true" align=middle width=63.837509999999995pt height=24.65759999999998pt/>, <img src="tex/8b20913d5ab2a13bc78672a094257b2e.svg?invert_in_darkmode&sanitize=true" align=middle width=71.60010000000001pt height=24.65759999999998pt/> and <img src="tex/3f748a7ca98cfbb400fc49d3c37a0a00.svg?invert_in_darkmode&sanitize=true" align=middle width=103.55895pt height=27.775769999999994pt/>. What is <img src="tex/07617f9d8fe48b4a7b3f523d6730eef0.svg?invert_in_darkmode&sanitize=true" align=middle width=9.904950000000003pt height=14.155350000000013pt/>?

We can solve this with maximum likelihood:

<p align="center"><img src="tex/e4c4f335043cc19156e7a862b909bcc2.svg?invert_in_darkmode&sanitize=true" align=middle width=283.6449pt height=23.653245pt/></p>
<p align="center"><img src="tex/56371d332a287d6d6961443ac003e9af.svg?invert_in_darkmode&sanitize=true" align=middle width=470.0453999999999pt height=19.726245pt/></p>

Setting the derivative to zero:

<p align="center"><img src="tex/20ded31c49f24c1971c479435a510918.svg?invert_in_darkmode&sanitize=true" align=middle width=311.16029999999995pt height=40.284254999999995pt/></p>

### EM example

But what about when we have even less information?

Suppose <img src="tex/ecc80066805e9ab29b97c025f20f5f5f.svg?invert_in_darkmode&sanitize=true" align=middle width=67.22397000000001pt height=22.831379999999992pt/> students got an A or a B, <img src="tex/3e18a4a28fdee1744e5e3f79d13b9ff6.svg?invert_in_darkmode&sanitize=true" align=middle width=7.11380504999999pt height=14.15524440000002pt/> got a C and <img src="tex/2103f85b8b1477f430fc407cad462224.svg?invert_in_darkmode&sanitize=true" align=middle width=8.556075000000003pt height=22.831379999999992pt/> got a D (<img src="tex/2ad9d098b937e46f9f58968551adac57.svg?invert_in_darkmode&sanitize=true" align=middle width=9.471165000000003pt height=22.831379999999992pt/>, <img src="tex/3e18a4a28fdee1744e5e3f79d13b9ff6.svg?invert_in_darkmode&sanitize=true" align=middle width=7.11380504999999pt height=14.15524440000002pt/> and <img src="tex/2103f85b8b1477f430fc407cad462224.svg?invert_in_darkmode&sanitize=true" align=middle width=8.556075000000003pt height=22.831379999999992pt/> known). As before, <img src="tex/96959448a716b07f898d9ec92b496b5f.svg?invert_in_darkmode&sanitize=true" align=middle width=62.45778pt height=27.775769999999994pt/>, <img src="tex/11e49a4ba829bcfe13782a1a837ad01b.svg?invert_in_darkmode&sanitize=true" align=middle width=63.837509999999995pt height=24.65759999999998pt/>, <img src="tex/8b20913d5ab2a13bc78672a094257b2e.svg?invert_in_darkmode&sanitize=true" align=middle width=71.60010000000001pt height=24.65759999999998pt/> and <img src="tex/3f748a7ca98cfbb400fc49d3c37a0a00.svg?invert_in_darkmode&sanitize=true" align=middle width=103.55895pt height=27.775769999999994pt/>. What is <img src="tex/07617f9d8fe48b4a7b3f523d6730eef0.svg?invert_in_darkmode&sanitize=true" align=middle width=9.904950000000003pt height=14.155350000000013pt/>?

<p align="center"><img src="tex/2af7c9044c32246a2865f3a2fe741ade.svg?invert_in_darkmode&sanitize=true" align=middle width=302.6694pt height=49.31553pt/></p>

If we knew <img src="tex/07617f9d8fe48b4a7b3f523d6730eef0.svg?invert_in_darkmode&sanitize=true" align=middle width=9.904950000000003pt height=14.155350000000013pt/>, we could calculate <img src="tex/44bc9d542a92714cac84e01cbbb7fd61.svg?invert_in_darkmode&sanitize=true" align=middle width=8.689230000000004pt height=14.155350000000013pt/> and <img src="tex/4bdc8d9bcfb35e1c9bfb51fc69687dfc.svg?invert_in_darkmode&sanitize=true" align=middle width=7.054855500000005pt height=22.831379999999992pt/>, and vice-versa. Instead, we can use Expectation-Maximisation.

- let <img src="tex/22d825f24037e89b1b787b6a6a0362a8.svg?invert_in_darkmode&sanitize=true" align=middle width=28.626510000000003pt height=24.65759999999998pt/> be the estimate of <img src="tex/07617f9d8fe48b4a7b3f523d6730eef0.svg?invert_in_darkmode&sanitize=true" align=middle width=9.904950000000003pt height=14.155350000000013pt/> after the <img src="tex/4f4f4e395762a3af4575de74c019ebb5.svg?invert_in_darkmode&sanitize=true" align=middle width=5.936155500000004pt height=20.222069999999988pt/>th iteration.
- let <img src="tex/fd409d6eb3ce552243d618ae3a08260d.svg?invert_in_darkmode&sanitize=true" align=middle width=25.776465000000005pt height=24.65759999999998pt/> be the estimate of <img src="tex/4bdc8d9bcfb35e1c9bfb51fc69687dfc.svg?invert_in_darkmode&sanitize=true" align=middle width=7.054855500000005pt height=22.831379999999992pt/> after the <img src="tex/4f4f4e395762a3af4575de74c019ebb5.svg?invert_in_darkmode&sanitize=true" align=middle width=5.936155500000004pt height=20.222069999999988pt/>th iteration.

**E-step**: assign expected value to hidden variables.
<p align="center"><img src="tex/6ee9e156291d82d46325b4a5f7324142.svg?invert_in_darkmode&sanitize=true" align=middle width=227.99699999999999pt height=38.834894999999996pt/></p>
**M-step**: re-estimate parameters.
<p align="center"><img src="tex/0a21ead9d5ccd9db4533fed9a715c840.svg?invert_in_darkmode&sanitize=true" align=middle width=393.5976pt height=38.834894999999996pt/></p>

These should converge on the right answer.

### Expectation-Maximisation for Gaussian Mixtures

Given data <img src="tex/9fc20fb1d3825674c6a279cb0d5ca636.svg?invert_in_darkmode&sanitize=true" align=middle width=14.045887349999989pt height=14.15524440000002pt/> drawn from <img src="tex/63bb9849783d01d91403bc9a5fea12a2.svg?invert_in_darkmode&sanitize=true" align=middle width=9.075367949999992pt height=22.831056599999986pt/> normal distributions with unknown means and equal variance (the actual variance is unimportant, so can be set to 1), we want to obtain estimates of the means <img src="tex/57091836ec1aac540f8081fa8acf0270.svg?invert_in_darkmode&sanitize=true" align=middle width=59.10778500000001pt height=14.155350000000013pt/>.

Introduce hidden variables <img src="tex/08d3f8811f13a4996a4d3f266ab69695.svg?invert_in_darkmode&sanitize=true" align=middle width=18.400140000000004pt height=14.155350000000013pt/> indicating the likelihood that x_i came from the <img src="tex/36b5afebdba34564d884d347484ac0c7.svg?invert_in_darkmode&sanitize=true" align=middle width=7.710416999999989pt height=21.68300969999999pt/>th cluster.

**E**: for each data point <img src="tex/9fc20fb1d3825674c6a279cb0d5ca636.svg?invert_in_darkmode&sanitize=true" align=middle width=14.045887349999989pt height=14.15524440000002pt/>, for each <img src="tex/72824e8166a67f767bb319e6b2422e55.svg?invert_in_darkmode&sanitize=true" align=middle width=38.703555pt height=22.831379999999992pt/>:

<img src="tex/de260e95ea9fa470df906d1e1c6cb610.svg?invert_in_darkmode&sanitize=true" align=middle width=278.874255pt height=34.08965999999999pt/>, normalised such that <img src="tex/c77589987495db9a8e2bae934aa362b8.svg?invert_in_darkmode&sanitize=true" align=middle width=94.564305pt height=57.07778999999998pt/>

**M**: for each <img src="tex/72824e8166a67f767bb319e6b2422e55.svg?invert_in_darkmode&sanitize=true" align=middle width=38.703555pt height=22.831379999999992pt/>, estimate the mean as the weighted average:
<p align="center"><img src="tex/d94d4ebecb44e9dbb103da9c2d52d0c0.svg?invert_in_darkmode&sanitize=true" align=middle width=506.8635pt height=49.31553pt/></p>
