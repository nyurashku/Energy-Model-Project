# Energy-Model-Project
IST 652 - Final Project

![nasa-Q1p7bh3SHj8-unsplash](https://github.com/nyurashku/Energy-Model-Project/assets/119478875/d9e44b4c-5109-46ec-9bca-18c68847b7b2)
****
# Introduction:

Our project aims to develop an Energy Consumption Model that leverages a data pipeline for aggregating relevant weather and household energy data and applies predictive analytics to assess how energy is consumed.

# Project Overview:

The project will involve two main components: building a data pipeline and creating a predictive model for energy used in households. The pipeline will gather data from various sources such as weather forecasting data and US/EU household energy data. The predictive model will use machine learning techniques to analyze this data and generate insights into energy usage.


# Data Sources:

The data pipeline will integrate data from several sources:

1.	Weather forecasting and historical data: https://open-meteo.com/en/docs
2.	US energy consumption by household: eia.gov


# Methodology:

Data Collection (Extraction) - Establish APIs and data retrieval methods to collect data from the identified sources.

Data Processing (Transform) - Clean and preprocess the data using Python libraries like Pandas.

Database (Loading) - Store data into a database such as MongoDB, MySQL, Postgres.

Model Development - Implement machine learning algorithms for energy consumption prediction, likely employing techniques such as gradient boosting (XgBoost).

Validation - Test the model's accuracy and reliability against a subset of the data.
