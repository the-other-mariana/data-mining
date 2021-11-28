# Binary Encoding

![img](res/1.png)

When we have a categorical column that is not the target column for a classification problem, we can convert the string categories in said column into N binary columns: in this example, we have a column that tells us the Sex of an oyster can either be (M)ale, (F)emale or (I)nfant:

| 0 | 1 | ... |
| --- | --- | --- |
| M | ... | ... |
| M | ... | ... |
| F | ... | ... |
| M | ... | ... |
| I | ... | ... |

Since we have 3 categories in this column, we need to encode it into 3 binary columns:

| 0 | 1 | 2 |
| --- | --- | --- |
| 0 | 0 | 1 |
| 0 | 0 | 1 |
| 1 | 0 | 0 |
| 0 | 0 | 1 |
| 0 | 1 | 0 |

Python uses the alphabetical order of: F, I, M and thus the column 0 is 1 when the oyster is F, column 1 is 1 when the oyster is I and column 2 is 1 when the oyster is M. In this way, our model can take these three columns as part of the training set, instead of dropping all the categorical columns as we did before.

In this data set, the accuracy with a resampling validation technique if we ignore the categorical column is 24% and if we include it binarized in three columns, the accuracy improves to 25%, which means the categorical column bring information that improves the prediction model.