# Airbnb-New-York_ML-Project

The Goal of this analysis is to create an efficient price predictor using supervised learning algorithms models. I hope that through this analysis helps airbnb property owners to better adjust their rate based on their properties attributes.

Data Overview

The data set that I will be utilizing for this analysis is from Airbnb’s New York metropolitan area. The shape of our data is 86009 thousand rows and 46 columns. It comprises 46 different variables; I will only include 36 of these variables which have been chosen based on their ability to predict the price of an Airbnb property in New york. In our analysis I had 5 different price predictors to choose from: Published Nightly rate, Average daily rate, Published Monthly rate, Published Weekly rate and Annual Revenue. I decided that Average Daily Rate(ADR) and Published Nightly Rate (PNR), would be the best predictors for our models.

The ADR variable had 22617 missing values (26%), however instead of dropping these NAs I decided to feature engineer a value to replace them. First I identified the top recurring neighborhoods which accounted for 60% of the missing values in ADR: Williamsburg; Harlem; Brooklyn; Midtown; Bushwick; East Village; Upper West Side; Upper East Side; Crown Heights; Lower East Side; Astoria; Washington Heights.

Then I took the mode of these values and the respective mean. The result I got from these calculations was 87.5, each NA value within ADR was replaced with this value. After this process I decided to drop the rest of the null values resulting in a sample size of 10038, which gives an additional 2471 samples from just dropping all null values (see: data6 vs data5). From this process I created the night_data dataset (relevant columns excluding ADR) and the ADR_data dataset (relevant columns excluding Published Nightly Rate), for their respective prediction models.

Next I tested which dependent variable performed the best in a standard linear regression. The results were that Published Nightly Rate ( 𝑅2=0.723 ) out performed Average Daily Price ( 𝑅2=0.635 ). Our reasoning behind this is that perhaps I could have used a better method for feature engineering to get more similar results.

I ran the rest of the models using the Principal Nightky Rate as the main dependent variable.

Summary

For the analysis of this data set, I have chosen to utilize 6 different supervised machine learning models to predict the price of an Airbnb property in New York. For our first model I have chosen a principal component analysis as a dimension reduction technique. From the PCA model I have been able to reduce the amount of linear relationships needed to represent our model down to 3 principal components, however this greatly reduces the predictive power of our models. I theorized that this might be due to the fact that PCA does not take into account classes of information, it purely looks at the variance of each feature.

The second model I used was an OLS Regression technique to help understand the causal relationship between the features of a property on the published nightly rate. The R Squared from this model is 0.72 ~ 72.3%.

Our third model utilizes Ridge Regression to combat the issue of multicollinearity. The R squared from this model is .72 ~ 72.3%. In the fourth model I use a Lasso Regression to help shrink the possibility of overfitting. The R squared from this model is 0.723 ~ 72.3%.

The fourth model is a Random Forest regressor. This technique allows us to fit a number of classifying decisions on various sub-samples of the data set using averaging to improve the accuracy and control for overfitting. The R squared for this model is 0.732 ~ 73.2%.

In the fifth model I use a Gradient boosting model. This model allows for weaker signals to show throughout the model, this also shrinks the data set controlling for overfitting. The R squared for this model is 0.58~58%.

The sixth model I have chosen is Bagging in order to help with bias-variance-trade-off. The R squared for this model is 0.719 ~71%.

After utilizing the 6 different supervised machine learning models I can conclude that the Random Forest regressor is the most efficient model for price prediction of an airbnb property in New York. Its ability to combine ensemble learning with a decision tree framework to create multiple randomly drawn decision trees from the data allowed for the model to be flexible enough to accurately predict Nightly rate. Information that shed light on the price setting controls set by owners and the different types of discounts given by owners based on seasonality. This information would help us better understand price setting for airbnb owners leading to a more accurate price prediction model.
