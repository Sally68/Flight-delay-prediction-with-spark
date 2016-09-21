Flight-Delay-prediction

Objective

The objective of the project is to perform analysis of the historial flight data to gain valuable insights and build a predictive model to predict whether a flight will be delayed or not given a set of flight characteristics.

Questions to be answered post analysis: • Which Airports have the Most Delays? • Which Routes are typically the most delayed? • Airport Origin delay per month • Airport Origin delay per day/hour  • What are the primary causes for flight delays?

The objective of the predictive model is to build a model to predict whether a flight will be delayed or not based on certain characteristics of the flight. Such a model may help both passengers as well as airline companies to predict future delays and minimize them.

Dataset Description

The dataset for this problem was obtained from the Bureau of Transportation Statistics which consists of all commercial flight operations from the year 2001 to 2008. The dataset consists of the following flight features: • YEAR : Year Of Flight Departure/Arrival • CRS_DEP_TIME : Flight Departure time in Hours • MONTH : Month of Flight Departure/Arrival (5-May and 12- December) • DAY_OF_WEEK : Day of Week (1-7) • CARRIER : Code assigned by IATA and commonly used to identify a carrier. • ORIGIN_CITY_NAME: Origin City of flight • DEST_CITY_NAME: Destination City of flight • ARR_DELAY_NEW : Difference in minutes between scheduled and actual arrival time. Early arrivals set to 0. • ARR_DEL15: Arrival Delay Indicator, 15 Minutes or More (1=Yes) • DISTANCE : Distance between origin and destination in miles. • CARRIER_DELAY: Carrier Delay, in Minutes • WEATHER_DELAY: Weather Delay, in Minutes • NAS_DELAY: National Air System Delay, in Minutes • SECURITY_DELAY: Security Delay, in Minutes • LATE_AIRCRAFT_DELAY: Late Aircraft Delay, in Minutes

In order to build the predictive model, the following attributes have been considered: • Timeslot • Carrier • Distance • Month Since the above factors played the most important role in determining delays, other factors have not been considered to maintain model accuracy.

I evaluated two models before deciding which model to use:Linear SVMs and Logistic Regression.Logistic regression finds a classifier which maximizes the conditional likelihood of the training data. SVM maximizes the margin between points closest to the classification boundary.
SVMs only consider points near the margin (support vectors). Logistic regression considers all the points in the data set. I decided to use the logistic regression model.

First,I analyze and predict flight delays in airports based on flight records in 2007 (7 million flights) . I use Jupyter Notebook and Local Spark to read, explore, analyze and visualize results.

Initial discovery of relationships is usually done with a training set while a test set and validation set are used for evaluating whether the discovered relationships hold. More formally, a training set is a set of data used to discover potentially predictive relationships. A test set is a set of data used to assess the strength and utility of a predictive relationship. The accuracy of the model is 85.13%

To see if the larget dataset will improve the prediction accuracy, I use the the flight records from 2001 to 2008, 5 GB and containing 52 million flight records. I use in the Aparche Spark service on Bulemix and the 5 GB dataset is stored in the Swift (Bluemix Object Storage) file system. This clearly helped -- accuracy is higher at 85.96%. 
