# Dynamic Pricing Model For Flights
## Overview 
In this project, I implemented the dynamic model for price optimization of flight data. These were the two main steps:
1) Built the baseline model(Xgboost Regressor)to predict initial prices.
2) Built a price optimization logic based on the predicted prices of each customer to maximize revenue and optimize prices based on specific constraints like demand and no of seats left etc.

## Introduction  
I used the dataset from Kaggle which comprises details of flight bookings like booking dates, journey dates, airline class, departure and arrival timings, flight duration, total stops, and prices. I cleanead this dataset, preprocessed it, and used it for analysis and dynamic pricing problem.

The major business goal is to maximize revenue for an airline by optimizing prices according to certain constraints.

## Data Preprocessing 
The data preprocessing involved splitting the Airline- Class column to get the airline name, flight code, and class. I also used the Date of Journey and Date of Booking to get days before a flight. I stripped Departure_Time and Arrival Time to get the departure and arrival cities. The main feature engineering step was to create a feature called Route that appends Departure city with Departure time.

## Exploratory Data Analysis
Data visualization plays a critical role in dynamic pricing by providing visual insights into demand patterns, customer behavior, and the competitive landscape among various airlines. This visual representation aids in better understanding the data, allowing for more informed pricing decisions and strategic planning.
Some of the visuals are shown below:

![](/images/visual.png)

![](/images/visual2.png)

![](/images/visual3.png)

![](/images/visual4.png)

![](/images/visual5.png)

## Segmentation and Encoding 
It’s important to segment data and perhaps build different models for different segments and be able to make pricing strategies to the unique characteristics of each segment and optimize revenue. First-class and business-class customers often exhibit a high willingness to pay for tickets, as they prioritize luxury, comfort, and personalized services. Customers in economy are more likely to be price sensitive and prioritize affordability and value when choosing flights. So I proceeded to build a model for economy class and narrowed it down to a specific airline and route.

For converting categorical variables into numerical format, I used label and frequency encoding.

## Model Building 
The machine learning algorithm used was an Xboost Regressor. XGBoost, short for Extreme Gradient Boosting, is a supervised machine learning algorithm that uses ensemble learning method to combine predictions of multiple weaker models to create a stronger, more accurate model.
1) Initialization and Residual Calculation: Start with an initial prediction for all observations. Compute residuals, which are the differences between actual target values and these initial predictions.
2) Fit a Weak Learner: Fit a shallow decision tree to the residuals to model the errors made by the initial prediction.
3) Update Predictions: Adjust the initial predictions by adding the predictions from the decision tree, aiming to reduce residuals.
4) Combination of Trees: Combine predictions from all trees, each scaled by a learning rate, to improve accuracy.
5) Regularization: Apply regularization techniques to prevent overfitting and improve generalization.
6) Final Prediction: Sum the contributions of all weak learners, with an optional learning rate to control each tree's impact on the final prediction.

The regressor also includes hyperparameters after model tuning. I used the Optuna package for Hyperparameter tuning.Optuna uses Bayesian optimization to find the best hyperparameters for your model. It’s lightweight and very efficient for optimizing hyperparameters, and it’s much faster than other tools like GridSearchCV.

## Price Optimization Logic
From the Xgboost regressor, we now have the predicted prices for each customer. This will be used as the baseline price. In a production environment, the model can typically be updated periodically or in batches using aggregated data from multiple customers based on day, time etc.

We then finally print the revenue before and after optimization, allowing usto compare the effectiveness of the optimization process in maximizing revenue within the specified constraints.

![](/images/rev.png)

Based on the results presented above, it’s evident that the revenue achieved after optimization surpasses the initial revenue, all while adhering to our specified constraints. Our primary objective was to maximize revenue regardless of operational expenses. 

Unlike static pricing approaches, this dynamic method allows us to adapt to changes in customer behavior, demand fluctuations, and other market dynamics, ultimately leading to more responsive and effective pricing strategies.


