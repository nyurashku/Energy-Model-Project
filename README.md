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

![image.png](attachment:image.png)




















