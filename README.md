# Predicting Gratuities for Taxi Cab Rides in New York City
> Using multiple linear regression, random forest, and XGBoost models

![Photo of taxi by Fernanda Caetano on Unsplash](images/taxi_photo.JPG)

## Overview
The purpose of this educational project was to find ways to generate more revenue for taxi cabs drivers. To achieve this, a goal was set to predict whether a customer would be a generous tipper (≥20%) or not. The dataset consisted of Yellow Taxi trip data from 2017. A multiple linear regression model was used to predict the fare amount, and this predicted feature then became an independent variable in a random forest model (and XGBoost model for comparison) to predict generous gratuity or not. The final random forest model performed well with 70% accuracy and 68% precision.

## Business Understanding
Taxi ridership has declined since 2011 due to competition from companies such as Uber. This increase in rideshare companies also reduced the medallion prices, and medallion holders had trouble making payments on the loans they borrowed to purchase the medallions, some costing more than $\$1$ million dollars originally. New York is one of the most expensive cities in the US, yet, in 2015, medallion drivers drivers earned only about $30/hour on average according to [Wikipedia](https://en.wikipedia.org/wiki/Taxis_of_New_York_City). For these reasons and more, finding ways to generate more revenue for Yellow Cab drivers is a pressing issue. 

## Data Understanding
This NYC Taxi and Limousine Commission data come from [NYC.gov](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page). It consists of nearly 22,700 rows and 18 features, and was likely sampled from the full dataset consisting of about 113M rows that can be found on the [NYC OpenData website](https://data.cityofnewyork.us/Transportation/2017-Yellow-Taxi-Trip-Data/biws-g3hs/about_data). Each row represents a single trip in a yellow taxi, and the features include pick-up and drop-off dates/times, pick-up and drop-off taxi zone locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts. The classes are fairly well balanced: about 53% generous tippers and 47% non-generous as shown in the plot:

![Class Balance plot](images/class_balance.PNG)

## Modeling and Evaluation
A random forest model was chosen based on maximizing the F1 score via cross-validation. The chosen model consisted of 50 decision trees and a max depth of 10, and achieved an accuracy of 70% and an F1 score of 74%. This model determined that the vendor, passenger count, and duration were the three features most capable of separating generous from non-generous tippers. This plot shows the top 15:

![Feature Importance Plot](images/feature_importance.PNG)

## Conclusion
The chosen algorithm (Random Forest) is good enough at predicting generous tippers, with reasonably strong precision (0.678), recall (0.828), F1 (0.745), and accuracy (0.702) scores. This model is roughly twice as likely to predict a false positive (FP) than a false negative (FN), which means that, when the model is wrong, the driver will more often be disappointed by the lack of a generous tip than be pleasantly surprised by a generous tip. Nevertheless, the model could be deployed to help Yellow Cab drivers select customers who are likely to tip generously.

Significant improvement to the model is unlikely without additional data, such as past tipping behavior for customers. There is opportunity to derive further insight from the data by, for example, clustering with K-Means and analyzing the resulting clusters.