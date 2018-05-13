# Symbols, Patterns and Signals

## B7. Evaluating classifiers

When classifying with two classes, there are four possible responses: true positives, true negatives, false positives and false negatives.

Normally classifiers are evaluated by running <img src="tex/55a049b8f161ae7cfeb0197d75aff967.svg?invert_in_darkmode&sanitize=true" align=middle width=10.189245000000009pt height=13.387440000000009pt/> tests, and finding the proportion of mistakes <img src="tex/63af3a09e3814001b9f842ca0fd11978.svg?invert_in_darkmode&sanitize=true" align=middle width=71.424705pt height=27.902819999999966pt/>. However, this assumes that positives and negatives are equally important. The profit of an extra true positive = the profit of an extra true negative = <img src="tex/2d77e685bfa7e0c249fa2e10b3d67677.svg?invert_in_darkmode&sanitize=true" align=middle width=26.62753500000001pt height=23.889689999999977pt/>, and the cost of an extra false positive = the cost of an extra false negative = <img src="tex/6bbe562b15b5555a0aae71b69d95b9b8.svg?invert_in_darkmode&sanitize=true" align=middle width=39.41305500000001pt height=23.889689999999977pt/>.

This is often not the case. In a medical diagnosis, the cost of mistakenly classing someone as healthy (false negative) is often much higher than a false positive. In spam filtering, it is more important that every non-spam email gets through than that every spam email is filtered out.

The true positive rate (TPR) is the proportion of positives correctly reported, whereas the false positive rate (FPR) is the proportion of negatives incorrectly reported.

**ROC** (formerly Receiver Operating Characteristic) graphs plot the true positive against false positive rates. In the example below, A is a decent classifier. C is wrong more than it is right, so negating all its answers (Cʹ) produces a more accurate result. B gives identical results to guessing, with a 3:1 bias to positive. The perfect classifier would be in the top left: 100% true positives, and 0% false positives.

![ROC graph example](https://upload.wikimedia.org/wikipedia/commons/thumb/3/36/ROC_space-2.png/1024px-ROC_space-2.png)

If the profit of extra true positives and of extra true negatives are equal, then any point on a line with a slope 1 (such as any point on the red dotted line) is as good as any other. More generally, if the cost ratio <img src="tex/3e18a4a28fdee1744e5e3f79d13b9ff6.svg?invert_in_darkmode&sanitize=true" align=middle width=7.43612100000001pt height=13.387440000000009pt/> (cost of false positive vs cost of false negative) is high, then a low FPR is more important than a high TPR, and vice-versa. All points on a line with slope <img src="tex/3e18a4a28fdee1744e5e3f79d13b9ff6.svg?invert_in_darkmode&sanitize=true" align=middle width=7.43612100000001pt height=13.387440000000009pt/> are equally as good.

![Convex hull](B07-convex-hull.png)  
The classifiers form a “convex hull”. All classifiers under this hull are suboptimal. To obtain a classifier midway between two classifiers on this hull, randomly combine the results.

### AUC metric

If we have a classifier, it will appear as one point on an ROC graph. If we try to change the decision threshold many times and plot each result on an ROC graph, we should hopefully get a convex hull. We can evaluate the classifier by measuring the area under the curve (AUC) of the ROC graph. The higher the AUC the better.