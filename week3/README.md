# Notes

## Box Plots

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/box-plot-parts.png?raw=true)

- A boxplot is a standardized way of displaying the distribution of data, or the variability of data (when spread out in order).

- It can also tell you if your data is symmetrical, how tightly your data is grouped, and if and how your data is skewed.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/02.png?raw=true)

- Use a box plot when you need to have information on the variability or dispersion of the data. A boxplot is a graph that gives you a good indication of how the values in the data are spread out.

    - **median (Q2/50th Percentile)**: the middle value of the dataset.

    - **first quartile (Q1/25th Percentile)**: the middle number between the smallest number (not the “minimum”) and the median of the dataset. The middle of the lower half of data.

    - **third quartile (Q3/75th Percentile)**: the middle value between the median and the highest value (not the “maximum”) of the dataset. The middle of the top half of data.

    - **interquartile range (IQR)**: 25th to the 75th percentile

    - **whiskers** (shown in blue)

- As mentioned earlier, outliers are the remaining .7% percent of the data.

- It is important to note that for any PDF, the area under the curve must be 1

## Box Plot Explained vs. PDF

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/03.png?raw=true)

- **Probability Density Function**: A PDF is used to specify the probability of the random variable falling within a particular range of values, as opposed to taking on any one value. This probability is given by the integral of this variable’s PDF over that range.

- The graph of a PDF does not show you the probability of events but their probability density.

## Example

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/04.png?raw=true)

- Using the graph, we can compare the range and distribution of the area_mean for malignant and benign diagnosis. We observe that there is a greater variability for malignant tumor area_mean as well as larger outliers.

- Also, since the notches in the boxplots do not overlap (the medians), you can conclude that with 95% confidence, that the true medians do differ.

## Interpretation

The five-number summary divides the data into sections that each contain approximately 25% percent of the data in that set.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/05.png?raw=true)

### About what percent of the boxes of raisins weighed more than 29 grams?

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/06.PNG?raw=true)

- Since Q_1 = 29, about 25% of the data is lower than 29 and about 75% is above 29. About 75% percent of the boxes of raisins weighed more than 29 grams.

- (About 50% of boxes have more than 32 grams)

## Histograms vs Density Plots

### Histograms

A histogram divides the variable into bins, counts the data points in each bin, and shows the bins on the x-axis and the counts on the y-axis. The binwidth is the most important parameter for a histogram, and the way to decide it is to choose the width that best describes the distribution.

- Smaller binwidths can make the plot cluttered, but larger binwidths may obscure nuances in the data.

### Histogram Failure

It fails in readability issues when we want to compare the distributions of one variable across multiple categories. (if we want to compare arrival delay distributions between airlines)

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/07.png?raw=true)

### Density Plot

A density plot is a smoothed, continuous version of a histogram estimated from the data.

- The most common form of estimation is known as kernel density estimation: a continuous curve (the kernel) is drawn at every individual data point and all of these curves are then added together to make a single smooth density estimation. The kernel most often used is a Gaussian (which produces a Gaussian bell curve at each data point).

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/08.png?raw=true)

- The y-axis in a density plot is the probability density function. However, we need to be careful to specify this is a *probability density* and not a *probability*. The difference is the **probability density is the probability per unit on the x-axis.**

- A Density Plot visualises the distribution of data over a continuous interval or time period. The peaks of a Density Plot help display where values are concentrated over the interval.

- An advantage Density Plots have over Histograms is that they're better at determining the distribution shape because they're not affected by the number of bins used (each bar used in a typical histogram).

- Any curve that is always on or above the horizontal axis and has total are underneath equal to one is a density curve.

    - Area under the curve in a range of values indicates the proportion of values in that range.

    - **Median**: The equal-areas point with 50% of the “mass” on either side.

    - **Mean**: The balancing point of the curve, if it were a solid mass.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/09.PNG?raw=true)

*Note*

- The mean and median of a symmetric density curve are equal.

- The mean of a skewed curve is pulled away from the median in the direction of the long tail.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/11.PNG?raw=true)

A density curve is a graph that shows probability. The area under the curve is equal to 100 percent of all probabilities.

## A Rule

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/10.png?raw=true)

## Scatter Matrix

A scatter plot matrix is ​​a grid (or matrix) of scatter plots that is used to visualize bivariate relationships between combinations of variables. Each scatter plot in the matrix shows the relationship between a pair of variables.

- It is common among data science tasks to understand the relation between two variables.We mostly use the correlation to understand the relation between two variables. But often we also hear about scatter matrix (also scatter plot) and covariance too.

- A scatter matrix is a estimation of covariance matrix when covariance cannot be calculated or costly to calculate.

    - The **covariance** is defined as the measure of the joint variability of two random variables.

- A scatter matrix consists of several pair-wise scatter plots of variables presented in a matrix format. It can be used to determine whether the variables are correlated and whether the correlation is positive or negative.

-  In other words, scatter plot matrix represents bi-variate or pairwise relationship between different combinations of variables while laying them in grid form.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/scatter-matrix.png?raw=true)

- The diagonal shows the distribution of the three numeric variables of our example data.

- In the other cells of the plot matrix, we have the scatterplots (i.e. correlation plot) of each variable combination of our dataframe.

If we were to draw one by hand, we decide which pair of variables to do: then, we also need to specify which of the paired variables will be our independent (x axis) and dependent (y axis) variables. Then, we plot for each x axis value (x variable value) its corresponding y axis value (y variable value on the same row). At the end, maybe you can spot a tendency: positive/negative, linear/non-linear.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week3/res/scatter-plot.png?raw=true)

### Correlation

The correlation matrix gives us the information about how the two variables interact, both the direction and magnitude. The commonly used covariance is based on the Pearson correlation coefficient.

    - The way we compute the correlation matrix is by dividing the covariance values of two variables by product of the standard deviation of two variables.

### Usage

- Use scatter plot matrix or pairplot for assessing pairwise or bi-variate relationship between different predictor variables

- Use scatter plot matrix or pairplot for analyzing the multicollinearity between predictor variables

- Use scatter plot matrix or pairplot for assessing whether the data is linearly separable or otherwise.

## Handy Links

- https://towardsdatascience.com/understanding-boxplots-5e2df7bcbd51

- https://www.khanacademy.org/math/statistics-probability/summarizing-quantitative-data/box-whisker-plots/a/box-plot-review

- https://towardsdatascience.com/histograms-and-density-plots-in-python-f6bda88f5ac0

- http://galton.uchicago.edu/~eichler/stat22000/Handouts/l03.pdf

- https://www.statisticshowto.com/density-curve-examples/
