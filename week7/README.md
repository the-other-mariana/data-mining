# Techniques To Evaluate ML Models

The most commonly used normalization method is the Standard Normalization. After we transform the data, we have our training data set fitted 'in the plane' and now they are in a way 'ready' to be sent as training for a ML algorithm. The ML algorithm will output a model, how can we validate how good is this model?

## Techniques To Evaluate ML Models

These are performed when we train a ML model with many subsets of the data set available and it is evaluated with the complementary subsets.

It is useful to detect over-adjustment of a model: those cases where the model does not achieve generalization.

But the idea of subsets is also used in the **training process**: there are some techniques to better use the training and test data set so that the model is accurate. Most of them involve the idea of dividing the whole 'training data set' available into different subsets and use a segment of these to train and others to validate (test), sometimes this is done iteratively and sometimes just once.

- **Over-adjustment**   

When the obtained mathematical model is adjusted tightly to the training data set. Consider the image:

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/1.png?raw=true)

When we say a model is over-adjusted, this means that our model is adjusted exactly to all our data points that we use as training, much like what interpolation methods do, such as Lagrange IM or Newton IM, that adjust **exactly** to the training data set. This in fact is the ideal model for our training set, but the problem arises when we have new input data: this model will no longer be useful for the new input data points (blue points in the image).

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/2.png?raw=true)

Then, what do we need to do? we need to apply models where there is just a **tendency** of the training data set, not an exact **fitting**. With these, we will have an error percentage with respect to the training data set, but the model will also somehow be more approachable to the new input data.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/3.png?raw=true)

Otherwise, we can train a model that gives us a 90% accuracy level, but **this 90% is calculated with respect to its training data**. Then, if we provide new data and we get a 60% of accuracy with this new data, then thid positive difference in percetange (30%) between the accuracy with training and with test data determines that my model is **over-adjusted** or **over-trained**. Thus, there are different techniques that can help us train our model without falling into this over-adjustment.

- Machine Learning (ML) Techniques

For a classification problem (pima database), what we get as a model is a line or a function that separates the two or the different classes that we want to predict for. Then, this model with output if the input point belongs to one class or another (**discrete output**).

For a regression problem, what we get as a model is also a liine or a function but this will output a **continuous value** for each input point we provide, following the tendency defined by the model/function.

For a clustering problem, we do not have a column that guides our training towards that output, we just group data according to its similarities.

Coming back, if we have a regression problem, and the model gives us an accuracy of 80% with respect to the training data and a 75% accuracy with respect to the input test data, our model is correct and is not over-adjusted. It can also happen that the model gives us an accuracy level of 70% with respect to training data and accuracy of 90% with respect to new input data: this is also an incorrect model, but in this case is due to **under-adjustment**. In conclusion, we cannot have a big difference in percentage of accuracy, neither positive or negative, with respect to our training and validating data.

## Data Preprocessing: Resampling Methods (Métodos de Remuestreo)

In order to validate a model we use **Resampling Methods**. Their objective is to evaluate algorithms, and they consist in dividing the training data for this evaluation. Their purpose is to avoid the over-adjustment of a model by taking a diversity of samples to create a diversity of models with one db.

### Resampling Methods for Validating a Model

- **Division by Percentage**: divide the data base in two by a set percentage; the part that goes as training is usually the bigger remaining of the percentage, and the smaller one goes to validation. The most common is 67% for training and 33% for validation. We then compute the percentage of **accuracy** after validating/evaluating.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/4.png?raw=true)

- **Division by Percentage with Repetitions**: take a 33% percent subset but many times, and randomly taken. If this and sthe simple one have similar results, then repetition methods are not needed. Or if the repetitions are 10 and 100 and the change is not that big, then the computation time / high repetitions are not necessary.

- **Cross Validation (K-Fold)**: divide the data base into k parts, and then perform k iterations: on each you take a different part as validation and the remaining k - 1 parts as training, and so on. This is the most commly used method.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/5.png?raw=true)

Until you achieve something like this:

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/8.png?raw=true)

At the end of the 5 iterations, you will have 5 percentages of accuracy (comparison between what you predicted using training data and what you calculated from the test data) for the 5 models you got, and those will be averaged to get the final accuracy level (`results.mean()`, which will be the one compared to the accuracy with the new input data and decide if it is really balanced) and also a stdev (`results.std()`) to see how much an iteration differ from another. What is accuracy here? For example, if you train and test with same subset, the accuracy result is 100%. This method can be visualized more easily with the following image:

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/9.png?raw=true)

There are several types of crossed validation techniques as well.

- **Cross Validation with Repetitions**: make many iterations of the same process in Crossed validation in order to find more diversity of the model we are validating. Due to the fact that in cross validation the samples are always random (`shuffle` parameter in sklearn), crossed validation with repetition will further have more different samples. `results` variable will have now more accuracy results than simple cross validation.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/6.png?raw=true)

- **Leave One Out Cross Validation**: in iteration 1, what it does is take just one column as test data and the remaining columns as training data, and so on. Depending on the number of columns (N), the number of iterations there will be. We basically take all data values as training except one (one area and one house price, for example) instead of a percentage, which goes to test. The stdev will be higher, because we will be comparing one data value against its perdicted value for an error estimation. This method takes more time to process.

![img](https://github.com/the-other-mariana/data-mining/blob/master/week7/res/7.png?raw=true)

In the code, we applied these to raw data, but these method can be applied to transformed data to see what changes.