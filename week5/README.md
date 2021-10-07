# Notes

## Standardization

Standardization of datasets is a requirement for many ML algorithms in `sklearn` package. Its purpose is to make the dataset look like a standard normally distributed dataset: Gaussian with **mean = 0 and unit variance**.

We transform in such way to center it by removing the mean value **to each feature**, then **scale it by dividing the feature by their standard deviation (S)**.

![\Large z=\frac{x-\overline{X}}{S}](https://latex.codecogs.com/svg.latex?\Large&space;z=\frac{x-\overline{X}}{S})

We perform this to each feature by computing the relevant statistics on the **samples** in the training dataset.

The preprocessing module of `sklearn` package provides the **StandardScaler** utility class, which is a quick and easy way to perform such transformations. 

*Note: many l2 regularizers assume that all features are standard normally distributed datasets.*

## Normalization With L2 Method

Normalization is the process of scaling individual samples to have **unit norm**. This might be useful if you want to use any dot-product or quadratic form to quantify the similarity of any pair of samples. Each sample (each row of the dataset) with at least one non zero component is rescaled independently of other samples so that its norm (l1, **l2** or inf) equals one.

The function `normalize` provides a quick and easy way to perform this operation on a single array-like dataset, either using the l1, l2, or max norms.

The parameter `norm` determines the norm to use to normalize each non zero sample. If `norm=’max’` is used, values will be rescaled by the maximum of the absolute values.

**L2 normalization** is also known as *spatial sign preprocessing*. L2 is using the l2 norm (or euclidean norm/distance/length), in other words the sum of the squares of the elements gives one.

![\Large d(p,q)=\sqrt{(q_x-p_x)^2+(q_y-p_y)^2}](https://latex.codecogs.com/svg.latex?\Large&space;d(p,q)=\sqrt{(q_x-p_x)^2+(q_y-p_y)^2})

Say if we got a normalized dataset (matrix) with L2 method called `X` we can achieve a vector of 1's by applying:

```python
np.sqrt(np.sum(X**2, axis=1))
# array([ 1.,  1.,  1.])
```

## Handy Links

- https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html

- https://scikit-learn.org/stable/modules/preprocessing.html

- https://stackoverflow.com/questions/48232331/norm-parameters-in-sklearn-preprocessing-normalize/48233156