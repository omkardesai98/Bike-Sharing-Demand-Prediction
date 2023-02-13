# Bike-Sharing-Demand-Prediction




![Logo](https://images.unsplash.com/photo-1455641374154-422f32e234cd?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1632&q=80)

**Rental bikes are a multi-billion dollar industry whose
popularity is increasing among the masses for short
travelling within the cities.
To keep up with demand, it is important to predict
the demand for rented bikes on an hourly basis to increase
customer satisfaction by reducing the waiting time and thus
giving it an edge over other competitors.
The main aim of the project is to make predictions about
rented bikes required at each hour for the stable supply
of rented bikes.**![--](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
# **Index**

|  SI.No.            |   Content                                                              |
| ----------------- | ------------------------------------------------------------------ |
| 1 | <a href = "https://github.com/omkardesai98/Bike-Sharing-Demand-Prediction#1-Introduction"> Introduction </a> |
| 2| <a href = "https://github.com/omkardesai98/Bike-Sharing-Demand-Prediction#1-Data Collection and Understanding"> Data Collection and Understanding </a> |
| 3 | <a href = "https://github.com/omkardesai98/Bike-Sharing-Demand-Prediction#1-Data Cleaning and Manipulation"> Data Cleaning and Manipulation </a> |
| 4 | <a href = "https://github.com/omkardesai98/Bike-Sharing-Demand-Prediction#1-Exploratory Data Analysis (EDA)"> Exploratory Data Analysis (EDA) </a>  |
| 5 | <a href = "https://github.com/omkardesai98/Bike-Sharing-Demand-Prediction#1-Model Selection And Evaluation"> Model Selection And Evaluation </a>  |
| 6 | <a href = "https://github.com/omkardesai98/Bike-Sharing-Demand-Prediction#1-Conclusion">Conclusion </a>  |

![--](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

# **1. Introduction**:
**Recently there has been a popular movement towards bike sharing systems in big cities around the world. A BikeShare system is a service that provides a quick and convenient way for people to get from place to place for a cheap price. Cities that have implemented a BikeShare system have hubs or stations where there are bike available for rent. A customer would simply walk up to a station, pay a certain amount of money, and have use of the bike until he/she is done. The beauty of the service is that since there are multiple hubs around the city, the customer does not have to return the bike to the same location. If there is another station or hub nearby, the customer could simply return the bike there and not be charged with any other fee.**

![--](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

# **2. Data Collection and Understanding**
**We had Seoul Bike Data for our analysis and model building**
**The dataset contains weather information (Temperature, Humidity,
Wind speed, Visibility, Dew point, Solar radiation, Snowfall, Rainfall),
the number of bikes rented per hour and date information.**
**In this we had total 8760 observations and 14 features including target
variable.**
![--](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

# **3. Data wrangling and Feature Engineering**

**If we group by Functioning day against rented_bike_count,
we will observe that on non-functioning day zero bikes were
rented.**
**It is of no use to us as we already know that on non-functioning
days zero bikes will be rented**
**Dropping those 295 rows as we only want data for only
functioning days. Then dropping ‘Functioning day’ feature as it
has only one category which is of no use.**
* **Feature Engineering :**
 We have derived 3 extra features for analysis
* **➢ Month :** Extracted from ‘Date’ feature. Has month numbers from 1 to 12.
* **➢ Is weekend :** Extracted from ‘Date’ feature.**Tells whether it is weekend or
not.“0” means not a weekend, “1” means weekend.
* **➢ Binned visibility :** “Visibility” and “Snowfall” have a relationship that if
snowfall is heavy then visibility is low which leads to less rental bike count.
Similarly if the snowfall is less then visibility is high which increases rental
bike count. Hence visibility is binned into Heavy snowfall, Medium snowfall
and Low snowfall.Then we have dropped “Date", "Visibility” and “Snowfall”
feature.


![](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

# **4. Exploratory Data Analysis (EDA)** 
## Screenshots
![image](https://user-images.githubusercontent.com/106911079/218499655-34310692-5bcc-4b75-b05a-7aead90654cf.png)
![image](https://user-images.githubusercontent.com/106911079/218499725-2d5b17bb-5857-4349-8269-865c42bae6b9.png)
![image](https://user-images.githubusercontent.com/106911079/218499791-b3807dd7-c562-4257-91cc-4b1d68cd1bda.png)


# **5. Model Selection And Evaluation**
### Grid Search CV and Bayesian Optimization are the two hyper-parameter tuningmethods that were used ###
### The various models that were used were
* **➢ Linear Regression**
* **➢ Lasso Regularization(alpha=0.01)**
* **➢ Ridge Regularization(alpha=0.4)**
* **➢ Decision Tree(criterion=Friedman mse,max depth=10,min impurity decrease=41.99,min samples leaf=20, min samples split=43)**
* **➢ Random Forest(n estimators=50, max depth=10, min impurity decrease=41.99, min samples leaf=20, min samples split=20)**
* **➢ Gradient Boosting(n estimators=300, learning rate=0.0957, loss=squarederror, max depth=20, min impurity decrease=2, min samples leaf=50, min samples split=50)**
* **➢ XG Boosting(n estimators=284, eta=0.0387, gamma=2, max depth=8,subsample=0.9, col sample bytree=0.834)**
### Screenshots
![image](https://user-images.githubusercontent.com/106911079/218500142-ca5aecab-950a-451c-b69f-9ad330296401.png)
![image](https://user-images.githubusercontent.com/106911079/218500339-27dcf0ef-455c-4477-a598-c2026ad3d419.png)


# **6. Conclusion**
## **Linear Regreesion with Lasso and Ridge regularization**
1. Linear Regression gave underfitted model as the feature relation with the target variable was non-linear one.
2. Also the lasso and ridge were not helpfull as the model did not overfitted it underfitted due to non-linear relationship.

## **Decision Tree**
1. Decision Tree gave good increase in R2 score as compared to linear regression.
2. Train R2=0.847 and Test R2=0.812 were obtained.

## **Random Forest**
1. Gave little gain as compared to decision tree.
2. Train R2=0.856 and Test R2=0.831 were obtained.

## **Gradient Boosting and XGB Boosting**
1. Both boosting techniques gave very good R2 score,better than any of the model.
2. The reason for choosing Gradient Boosting over XGB Boosting is because very small difference between (train R2=0.948 and test R2=0.897) for Gradient Boosting as compared to XGB Boosting which is (train R2=0.992 and test R2=0.899)
3. Even though XGB and Gradient Boosting performed equally due to relatively large difference between Train and Test error XGB was not not selected.
4. Gradient Boosting seems to have generalized well on the given data.

