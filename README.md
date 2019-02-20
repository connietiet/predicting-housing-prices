# How to Increase Your House Value

## Problem Statement
-  What features affect my sale price the most?
-  Which of these features should resources be allocated to?


[Data Source - Kaggle](https://www.kaggle.com/c/dsi-us-6-project-2-regression-challenge/data)

[Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)
### Background: 

Homeowners in Ames, IA want to sell their house, and know that improvements can increase the house value and decrease the number of days its on the market. The issue is not knowing what type of improvements will be the most beneficial to property valuation. Ideally, the house is remodeled in its entirety. Realistically, however, homeowners have a budget they must abide to. Devoting a majority of the budget to renovating the kitchen can mean forgoing improvements on the basement. 

I analyzed individual residential properties sold in Ames, IA from 2006 – 2010 and chose the best predictive model in order to learn how strongly different features can affect the price.  The data contains 81 house features and the price at which they were sold for.

### Approach:

The analysis is divided into two parts:

**1\. Exploratory Data Analysis and Cleaning**
-  The dataset contains 81 features, not all of which can effectively help us predict the sale price. This first step explores the relationship between features and removes ones that will contribute little to our model. Values that are either missing or incorrectly documented are also accounted for. 

**2\. Preprocessing and Modeling**
-  Multiple models are used and the one with the least amount of prediction errors is further enhanced. 
-  Baseline Model (Mean)
    -  This serves as our baseline model. We assume a house’s sale price will be $180,697.31 without taking into account the features and how they contribute differently.
-  Linear Regression
    -  We apply the linear regression model assuming the data meets the MLR assumptions. 
    -  The model performs significantly worse than the baseline model.
-  Lasso
    -  This is one of the regularization applied after reviewing the Linear Regression model. It performs feature selection and removes features that provide little signal for our model.
-  Ridge
    -  This is similar to Lasso, but it does not remove any features. The magnitudes of coefficients are reduced and approaches zero, but is still present in our model. It’s a less aggressive approach and helps address multicollinearity. 

**3\. Kaggle Submission**
-  The kaggle submission is not part of the modeling. The final model was submitted to a kaggle competition to see how well it performs on unseen data. 

### Takeaways:

Ridge performed the best, with an RMSE of 25108.92 and an $R^{2}$ score of 91.06% on the testing set. 
-  The predicted sale price will typically be lower or higher than the true sales price by `$25108.92`. 
-  91.06% of the variance in our training set is explained by our ridge model, relative to the mean (`$180,697.31`). 
-  The model has 105 features.

The top 10 predictors of sale price are:

| feature | weight |
| --- | --- |
| gr_liv_area | 1.43e+04 |
| overall_qual | 1.06e+04 |
| 2nd_flr_sf | 1.06e+04 |
| total_bsmt_sf | 9.82e+03 |
| 1st_flr_sf | 9.39e+03 |
| year_built | 7.44e+03 |
| bsmtfin_sf_1 | 7.17e+03 |
| garage_area | 6.11e+03 |
| overall_cond | 5.80e+03 |
| exter_qual_Ex | 5.67e+03 |

-  All the above features have a positive relationship with sale price 
-  Most features relate to size (square feet)
-  `overall_qual`, `overall_cond` and `exter_qual_Ex` are exceptions

### Recommendations: 
-  From the top 10 predictors, it’ll be best to focus on improving:
    -  overall quality
    -  overall condition


-  These features contribute the most weight to increasing the sale price of a house, but does not require as much renovations and expenses as the others do. 
