<u>**HOUSE PRICE MODELLING FOR AMES, IOWA**</u>

<u>Introduction</u>:

We have been presented the data of houses from Ames, Iowa, with the target of developing the most accurate model to predict the sales price for a house, based on the sales information collected from Ames Assessor's Office for the year 2006 to 2010. 

Two sets of data are supplied, one for model training (train.csv) and the other  to test (test.csv) the trained model. The training data contains 2051 different house sales which has 81 variables, including the sales price of the house. The test data contains 879 house sales, which has all the variables EXCEPT the sales price, which will be predicted using the model.

The judgement factor for the accuracy of the prediction will be to minimise the Root mean Squared Error (RMSE) of the Sales Price, which will be done upon submission of the predicted price for a particular house (identified by its ID) to Kaggle.

<u>EDA and Cleaning</u>:

First order of the day is to prepare and to clean the dataset for modelling. The first step taken is to remove the outliers and mentioned in the ReadMe file from the data source and the ID and PID columns, which are unique values for each house. The ReadMe file indicates that there are 2 sales that are clearly undervalued based on the price per square foot (which is clearly seen when plotting the scatter plot of Sale Price against the Above Ground Living Area).

The second step is to classify the types of variables into different category in order to assign the correct preparation for the model. The four different categories are;

- Continuous
- Discrete
- Nominal
- Ordinal

Once identified, the check for empty data points will be run and to identify whether there is missing data or if it has deliberately left out. For those that have been left out as it is a category/class, a zero/minimum value will be filled. For the missing data, a deduction will be made from other similar type of variables.

<u>Preprocessing</u>:

Once all the data has been sorted and there are no null values, it will now be tested for any relationship with the target variable (Sales Price). For the continuous and ordinal data types, the correlation will be tested while for the nominal and discrete data types, dummy variables will be created from them in order to test for mutual information. As there are many variables in this dataset, the test for correlation and mutual information will be used to narrow the list of variables down to a manageable 25 variables (where correlation > 0.3, correlation < -0.2 or mutual information > 0.15). The test dataset will also be prepared in the same way as the training dataset in order for the model to work with the exact same variables for the prediction. This selected dataset will then be scaled just before sending it to the model.

<u>Modelling</u>:

Scaling the data using StandardScaler, the plain vanilla Linear Regression will be run on the 25 variables, which will be the baseline score to evaluate the performance of the Ridge and Lasso regressions which are shown below.

| Type of Regression | R-Squared  | RMSE       | Kaggle (Public) | Kaggle (Private) |
| ------------------ | ---------- | ---------- | --------------- | ---------------- |
| Linear             | **0.8857** | 26,687     | **28,550**      | 32,767           |
| Ridge              | 0.886      | **26,660** | 28,954          | **32,667**       |
| Lasso              | 0.8858     | 26,684     | 28,626          | 32,715           |

Based on the results, although the Ridge regression has the most favorable results (smallest RMSE and Kaggle score), the difference between all the three different regressions is negligible. The ridge and lasso regression did not remove any coefficients or reduce one to near zero, and the scores are very close as shown by the R-Squared score, RMSE and the Kaggle scores.



<u>Findings and conclusions</u>

From the modelling, we can conclude that neither regression outperforms the other two. The differences are marginal so we are able to use either of the regressions to perform as the variance between the all three were similar as well. This would suggest that there is little overfitting that needed correcting, as the first round of filtering (using correlation and mutual information) helped to improve the fit of the model. Instead, the feature selections before running the model are more crucial and important to the accuracy of the model.



<u>Recommendations</u>

In order to obtain the optimal model for predicting the house prices, the feature selections stage of the process would be more crucial to the accuracy of the model, rather than the type of regression. Choosing the right tests to score and evaluate the variables and their abilities should be focused on when beginning.

For further studies, further prediction models could be used to predict prices of each neighbourhood or property type, as there seems to be major differences between each which could minimise the prediction error (RMSE) even further, which would be most beneficial to the users of the model.

