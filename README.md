# Energy-Model-Project

![IST 652](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/d8f14f20-f7e6-40df-93f8-9be92d7ee0df)

****
# Introduction:

Our project aims to develop an Energy Consumption Model that leverages a data pipeline for aggregating relevant weather and household energy data and applies predictive analytics to assess how energy is consumed.

# Project Overview:

The project will involve two main components: building a data pipeline and creating a predictive model for energy used in households. The pipeline will gather data from various sources such as weather forecasting data and US/EU household energy data. The predictive model will use machine learning techniques to analyze this data and generate insights into energy usage.


# Data Sources:

The data pipeline will integrate data from several sources:

1.	Weather forecasting and historical data: https://open-meteo.com/en/docs
2.	US energy consumption by household: [eia.gov](https://eia.gov)


# Methodology:

Data Collection (Extraction) - Establish APIs and data retrieval methods to collect data from the identified sources.

Data Processing (Transform) - Clean and preprocess the data using Python libraries like Pandas.

Database (Loading) - Store data into a database such as MongoDB, MySQL, Postgres.

Model Development - Implement machine learning algorithms for energy consumption prediction, likely employing techniques such as gradient boosting (XgBoost).

Validation - Test the model's accuracy and reliability against a subset of the data.

# Questions:

1. Can the sales of energy be predicted using a machine learning model? If so, what model works best? Starting with the most popular, Regression analysis, we will try to predict sales.
2. A popular machline learning algorithm used right now is the XGBoost model which stands for extreme gradient boosting. Although popular, it does tend to overfit data but will this still work for our needs?
3. Lastly, a random forest model will be attempted to be used to predict sales.

# Step 1: Data Collection

Our team created two data pipelines included in the jupyter notebook. One is for EIA data and th e other one is for weather data.

## Energy Data API
![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/7f5972bb-9788-4139-b1c5-cecffbef8a1f)

## Weather Data API
![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/a4eea411-52b8-498a-b363-bec68937df3e)

Once the data was collected and cleaned (the mundane act of cleaning the data was left in the jupyter notebook) the data was added to our MongoDB database:

![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/6438208e-6656-464c-a546-0b9a4e28815a)

## Step 2: Exploratory Data Analysis and Visualization (EDA)

Our team conducted a detailed EDA analysis of descriptive statistics as well as visuals for weather data to under the seasonality of it and where weather tends to have the biggest swings.

### heavy tailed distributions for energy prices

![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/72194ab1-49bf-4255-af4e-f79694e59f18)

Down below are also the histograms of each numerical variable (datetime can be ignored) which show really heavy heavy-tailed distrubtions - we are speculating that the cause of this is due to regulations around price as well as the inelastic demand that can come from energy needs.

### Weather data

![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/da572f26-25e6-402a-9aa7-cfaced5138b6)


![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/b954200b-3f83-4c9a-a362-262cfa27e9a0)


In addition to various maps in our jupyter notebook, we also included visuals of weather averages in the major states:

![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/1bac822d-81d4-418f-a17f-8fc47f0852ca)


# Step 3: Merging DataFrames and Conducting Machine Learning

Once the data was visualized and further cleaned for null values, duplicate rows, the data sets were merged.

Once merged, our team conducted feature extraction to choose the best features for our machine learning models. In regards to price, revenue and sales, the goal is that sales is the independent variable and what we are predicting. Revenue would most likely give our model too much look ahead bias and perhaps mathematically calculate what the sales should be. Given that, the 'revenue' variable will also be removed. 

Then, there was the problem of temperatures. The a pricing model obviosuly cannot make a prediction of the sales by waiting until the end of the day to know what the max and min temp is going to be. It would be too late at that point and the sales can already be concluded. That is why we will only leave the 'mean' price in for our model. 

For all categorical variables, we used the hot encoding to change them all to 0's and 1's with dummy variables - machine learning algorithms dont work well with categorical information.

Final data set that training was done on:

![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/c834ff0a-4246-44a0-a015-92b2f06421eb)

A collection of 31 features in total.

# Step 4: Machine Learning Models

## Linear Regression:

![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/0219a058-f3e1-4666-9672-9363b1895c9f)

Summary: The 'mean squared error' (MSE) is really high suggesting that our sales predictions would be way off. The Mean Absolute Error (MAE) tells us that our sales predictions would be off by 1,059 units.

R² of 0.680: An R² of 0.680 means that about 68% of the variability in sales is explained by the model. While not low, this leaves room for improvement, as approximately 32% of the variance in sales is not captured by the model.

The cross validation MSE: further indicates how much our estimate is off by on average.

## Extreme Gradient Boosting (XGBoost)

![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/be93bc00-8b5f-4954-a12a-437b92963f9b)

The results from your XGBoost model indicate a Mean Squared Error (MSE) of approximately 366972 and an R-squared value of about 0.945.

We see a big improvement in our MSE compared to linear regression and a much better r-squared value.

## Random Forest

![image](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/fde552fe-0097-4339-8f16-646e290180c8)

Surpisingly, the random forest algorithm performed the best. It has the lowest MSE and the best R-squared. It is suprising because this algorithm tends to underfit.

# Conclusions

From our analysis, it emerged that the Random Forest algorithm demonstrated superior performance compared to both Regression and XGBoost models. It's noteworthy, however, that our data preprocessing and cleaning efforts resulted in a significantly reduced dataset size—from initially hundreds of thousands of entries to approximately 26,000. While complex machine learning algorithms typically benefit from larger datasets to enhance their predictive accuracy and generalizability, our analysis was constrained to this reduced dataset size due to the nature and quality of the available data.

Despite these limitations, the Random Forest model's relative success underscores its robustness and effectiveness even with smaller datasets. However, to further unlock the potential of our predictive modeling efforts, collecting a more extensive dataset in the future will be crucial. A larger dataset will likely improve model performance by providing a more comprehensive representation of the underlying patterns and relationships.

Additionally, we advocate for continued refinement and optimization of the Random Forest model. Fine-tuning the model's hyperparameters, exploring more sophisticated feature engineering techniques, and employing advanced methods for model evaluation could substantially enhance its predictive capabilities. These steps will not only improve the accuracy of our current predictions but also bolster the model's ability to generalize to new, unseen data, thereby making it a more powerful tool for our analytical objectives.

