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


