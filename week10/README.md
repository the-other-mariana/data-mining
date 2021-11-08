# Notes

Remember the Confusion Matrix:

![img](res/1.png)

![\Large \kappa=\frac{P_o-P_e}{1-P_e}](https://latex.codecogs.com/svg.latex?\large&space;Sensitivity=TPR=\boxed{\frac{TP}{TP+FN}})

![\Large \kappa=\frac{P_o-P_e}{1-P_e}](https://latex.codecogs.com/svg.latex?\large&space;Specificity=TNR=\boxed{\frac{TN}{TN+FP}})

and if we compute:

![\Large \kappa=\frac{P_o-P_e}{1-P_e}](https://latex.codecogs.com/svg.latex?\large&space;FPR=1-Specificity=1-\frac{TN}{TN+FP}=\frac{TN+FP-TN}{TN+FP}=\boxed{\frac{FP}{TN+FP}})

so that our Y axis is the **sensitivity** and **specificity** the X axis. But, specificity starts from 1 - 0, so we compute the **FPR (1-specificity)** to have 0-1 in Y axis and 0-1 in X axis for the ROC plot. If we take the last time example, where the confusion matrix was:

![img](res/2.png)

*Note: the '0' does not mean 'negative' in the axes, but 'class 0 (positive)' and '1' is 'class 1 (negative)'.*

![\Large \kappa=\frac{P_o-P_e}{1-P_e}](https://latex.codecogs.com/svg.latex?\large&space;Sensitivity=TPR=\frac{TP}{TP+FN}=\frac{147}{147+15}=\boxed{0.91})

![\Large \kappa=\frac{P_o-P_e}{1-P_e}](https://latex.codecogs.com/svg.latex?\large&space;Specificity=TNR=\frac{TN}{TN+FP}=\frac{50}{50+42}=0.54)

![\Large \kappa=\frac{P_o-P_e}{1-P_e}](https://latex.codecogs.com/svg.latex?\large&space;FPR=1-Specificity=1-0.54=\boxed{0.46})

Taking both the TPR and FPR for Y and X axis we get:

![img](res/3.png)

This given point (FPR, TPR) is **on** the ROC Curve, but how do we get the remaining points on it? For example if our data is a):

![img](res/4.png)

And then, in the ordered table b) we put a **decision threshold** that divides the 0's from the 1's in the real data vector, we would get what we got as TPR and FPR. If we **move** the threshold, say to rows up like c), then **change the real 0's to 1's**, then calculate again the **TPR and FPR**  with a new confusion matrix ([[5, 1], [1, 1]]) and put another **point** in (FPR, TPR), and so on until the threshold has visited all rows, we will get the ROC Curve plotted.

It's the same idea when we plot the NO and YES and have the ideal threshold:

![img](res/5.png)

We say ideal threshold because we have 50% and 50% on both sides of the threshold, that is, we have balanced entries for class 0 and class 1. The closer our NO and YES outcomes are from each other, the harder the prediction will be, and the closer the ROC curve will be from the AUC = 0.5 or less.

The following images show how the TPR and FPR change as the threshold moves.

![img](res/6.png)

![img](res/7.png)

Thus, by looking at our first point in (0.46, 0.91), where the real threshold starts, we can say that it looks like the second picture where there are More Positives' Entries, meaning that the database must have more positive class entries than negative ones: this positioning of the starting threshold lets us know which class our classifier is able to predict better. Ideally, the point should be more towards the center of the corner: it can differentiate the two classes.