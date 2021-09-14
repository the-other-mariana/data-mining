# Notes

## Data Redundancy

An attribute (column or feature) of a data set is called **redundant** if it can be **derived** from any other attribute or set of attributes.

- Example

> On analysing the fact that if a person is not male (i.e is_male is 0 corresponding the person_name) then, the person is surely a female or is_female is 1 (since there are only two value in output class- male and female).

It implies that the two attributes are **highly correlated** and one attribute can **determine** the other, and therefore, one of the two is **redundant**. Hence, one of these attributes became redundant. So one of these two attributes can be dropped without any information loss.

## Detection of Redundancy: Correlation Coefficient

- In this test, the relation between the A attribute and B attribute is computed by Pearson's product-moment coefficient, also called the correlation coefficient. A correlation coefficient measures **the extent to which the value of one variable changes with another**. 

- The most common is the Pearson r, used for continuous variables.

    - A +1 correlation means that as one variable rises, the other rises proportionally.

    - A -1 correlation means that as one rises, the other falls proportionally.

    - A 0 correlation means that there is no relationship between the movements of the two variables.

- we can say that the greater the correlation coefficient, the more strongly the attributes are correlated to each other, and we can ignore any one of them (either a or b).

Let's say A and B are highly correlated, but how to know which one to delete? Well, a simple approach is to look at the main attribute of the dataset' correlation with A and B, and whichever is **lower**, is the column we can eliminate.

## Handy Links

- https://www.geeksforgeeks.org/redundancy-and-correlation-in-data-mining/

- https://www.javatpoint.com/redundancy-and-correlation-in-data-mining