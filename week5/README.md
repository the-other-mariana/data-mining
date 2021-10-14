# Scaling Transformations for Numerical Values

For example, consider a data set containing two features, age, and income. Here age ranges from 0–100, while income ranges from 0 to a huge amount which is mostly higher than 100. Income is about 1,000 times larger than age. So, these **two features are in very different ranges**. When we do further analysis, like multivariate linear regression, the attributed income will intrinsically influence the result more due to its larger value. But this doesn’t necessarily mean it is more important as a predictor. **Therefore, the range of all features should be scaled so that each feature contributes approximately proportionately to the final distance.**

The concept of **feature scaling**, which is a crucial part of the data preprocessing stage in order to be able to handle many ML algorithms that are very sensible to these variations.

- **Standardization** and **Normalization** can be described as either two types of standardization or two types of normalizations.

## 1. MinMax Scaling (MinMax Normalization)

By using this transformation, all features (column) will be transformed into the range [0,1] meaning that the minimum and maximum value of a feature/variable is going to be 0 and 1, respectively.

![\Large x_{scaled}=\frac{x-min(x)}{max(x)-min(x)}](https://latex.codecogs.com/svg.latex?\Large&space;x_{scaled}=\frac{x-min(x)}{max(x)-min(x)})

## 2. Standardization

Standardization of datasets is a requirement for many ML algorithms in `sklearn` package. Its purpose is to make the dataset look like a standard normally distributed dataset: Gaussian with **mean = 0 and unit variance**.

We transform in such way to center it by removing the mean value **to each feature**, then **scale it by dividing the feature by their standard deviation (S)**.

![\Large z=\frac{x-\overline{X}}{S}](https://latex.codecogs.com/svg.latex?\Large&space;z=\frac{x-\overline{X}}{S})

We perform this to each feature by computing the relevant statistics on the **samples** in the training dataset, which means that the mean is the average of the column and the std dev is also from each column.

The preprocessing module of `sklearn` package provides the **StandardScaler** utility class, which is a quick and easy way to perform such transformations. 

*Note: many l2 regularizers assume that all features are standard normally distributed datasets.*

## 3. Normalization With L2 Method

Normalization is the process of scaling individual samples to have **unit norm**: either morm method you choose (max, l1, l2), will scale the row to have values in range [0,1]. This might be useful if you want to use any dot-product or quadratic form to quantify the similarity of any pair of samples. Each sample (each **row** of the dataset) with at least one non zero component is rescaled independently of other samples so that its norm (l1, **l2** or inf) equals one.

The function `normalize` provides a quick and easy way to perform this operation on a single array-like dataset, either using the l1, l2, or max norms.

The parameter `norm` determines the norm to use to normalize each non zero sample. If `norm=’max’` is used, values will be rescaled by the maximum of the absolute values.

**L2 normalization** is also known as *spatial sign preprocessing*. L2 is using the l2 norm (or euclidean norm/distance/length), in other words the sum of the squares of the elements gives one.

![\Large d(p,q)=\sqrt{(q_x-p_x)^2+(q_y-p_y)^2}](https://latex.codecogs.com/svg.latex?\Large&space;d(p,q)=\sqrt{(q_x-p_x)^2+(q_y-p_y)^2})

Say if we got a normalized dataset (matrix) with L2 method called `X` we can achieve a vector of 1's by applying:

```python
np.sqrt(np.sum(X**2, axis=1))
# array([ 1.,  1.,  1.])
```

Or simply:

![img](https://github.com/the-other-mariana/data-mining/blob/master/week5/res/norml1l2.png?raw=true)

Thus, L2 norm applies the following:

![\Large x_{i}^{norm}=\frac{x_i}{\sqrt{\sum_{i=1}^{n}{x_{i}}}}](https://latex.codecogs.com/svg.latex?\Large&space;x_{i}^{norm}=\frac{x_i}{\sqrt{\sum_{i=1}^{n}{x_{i}}}})

where i is each of the row values and n is the row's amount of values. You raise to the power of 2 each row value and at the end you take the square root of that sum. This value will divide each of said row's values.

| x_1 | x_2 | x_3 | x_4 |
| ---- | ---- | ---- | ---- |
| 2.5 | 3.4 | 1.3 | 2.0 |

![\Large x_{i}^{norm}=\frac{x_i}{\sqrt{\sum_{i=1}^{n}{x_{i}}}}](https://latex.codecogs.com/svg.latex?\Large&space;x_{1}^{norm}=\frac{2.5}{\sqrt{(2.5)^2+(3.4)^2+(1.3)^2+(2.0)^2}})

Due to the nature of this formula (squared terms), the atypical values affect significantly the normalized value. If we have a lot of atypical values, this transformation is not suggested.

### Standardization vs Normalization

Standardization, aka z-score normalization, is another scaling technique where the values are **centered around the mean** with a **unit standard deviation**. When it is applied the features will be rescaled so that they’ll have the properties of a standard normal distribution with mean = 0 and std deviation = 1 (standard deviation from the mean/average), also known as unit variation, and thus, the same scale. This formula (above) scales the features in a way that they range between [-1,1].

![img](https://github.com/the-other-mariana/data-mining/blob/master/week5/res/03.png?raw=true)

Normalization is a scaling technique in which values are shifted and rescaled so that they end up ranging between 0 and 1. It is also known as Min-Max scaling. 

### Applying Them

In the case of MinMax scaling (sometimes known as MinMax Normalization), all the features now have a minimum value of 0 and a maximum value of 1. 

If you have categorical or binary features, do not use Standardization. Normalization would just transform their values into a range of 0's and 1's.

Now if we apply a Standardization, the numerical features are now centered on the mean with a unit standard deviation. 

![img](https://github.com/the-other-mariana/data-mining/blob/master/week5/res/02.png?raw=true)

Now let's compare both methods visually

![img](https://github.com/the-other-mariana/data-mining/blob/master/week5/res/norm-stand.png?raw=true)

### Quick Example

- In the raw data, feature alcohol lies in [11,15] and, feature malic lies in [0,6].

    - In the normalized data, feature alcohol lies in [0,1] and, feature malic lies in [0,1].

    - In the standardized data, feature alcohol and malic are centered at 0.

Standardization's context is based on those problems that require us to use a Gaussian representation. What is a Gaussian representation?

![img](https://github.com/the-other-mariana/data-mining/blob/master/week5/res/04.jpg?raw=true)

- Interpretations

The 34% percentages around both sides of the mean = 0, take about 70% of information (-1 * stdev and 1 * stdev) and this 70% of the data is the one taken on account most of the times (ignoring atypicals): these are the values inside a box plot **density** (box). As we said before, some systems need to have the data in this form in order to be processed (Linear Regression or Logistic Regression). We can have different transformation results, but the 70% of the data must be around the mean.

In **normalization L2** technique, we use the as sample the **row** of a dataset, and in Standardization a sample was a **column/attribute**.

## 4. Binarization

This transformation ends up filling all columns with 1's or 0's. We transform the attribute data into 1's and 0's by using a threshold, and values lower than the threshold will be set to 0 and those larger than the threshold will be set to 1. You can combine transformations: scale with MinMax and then apply a threshold binarizer, for example.

- Gaussian Skewness

We can expect the following skews when we have a gaussian distribution:

![img](https://github.com/the-other-mariana/data-mining/blob/master/week5/res/06.png?raw=true)

This is seen in the **pedi** and **age** density plots.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week5/res/07.png?raw=true)

## 5. Power Transformer

There are non-linear transformations that can make an attribute's distribution look more like a normal distribution.

Transformations that try to shape the data values as a normal distribution:

1. Box-cox: input data values must be positive (biggest difference with method 2).

2. Yeo Johnson: input data can be negatives.

These two have a coefficient called **lambda**, which normally receives values in the range [-1, 1], and this coefficient modifies the transformation (either of the two) in order to change and adjust the shape of the gaussian result. We are trying to change the distribution of attributes in order to reach a distribution similar to the normal distribution, so that these attributes can be a proper input for a ML algorithm (Linear Regression). After this transformation, the correlation coefficient can change, therefore it is advised to check the correlation in raw data.

## Handy Links

- https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html

- https://scikit-learn.org/stable/modules/preprocessing.html

- https://stackoverflow.com/questions/48232331/norm-parameters-in-sklearn-preprocessing-normalize/48233156