# Time-series-forecasting-for-tunnel-traffic

## Steps of the project:
 ### 1. Goal/Objective and Business Understanding:
Tunnel Traffic is a time series describing the number of vehicles traveling through the Baregg Tunnel in Switzerland each day from November 2003 to November 2005. Here, I try to explore various components in the time series like trends and seasonality and predict on out of sample data using Linear Regression model.

2. Data Understanding: 
### 3. Feature Engineering: 
We create lag features for understanding the relationship between number of vehicles on a particular day and future days. The lag plot shows us how well we were able to fit the relationship between the number of vehicles one day and the number the previous day. When creating lag features, we need to decide what to do with the missing values produced. Filling them in is one option, maybe with 0.0 or "backfilling" with the first known value. Instead, we'll just drop the missing values, making sure to also drop values in the target from corresponding dates.

### 4. Data preprocessing: 
In order to facilitate time series analysis, Pandas package has been used to transform the dataset accordingly. By setting the index to a date column, the "Day" column has been parsed as a date type by using `parse_dates` when loading the data. Moreover, a time dummy/time step feature has been created for generating lag features from the same by counting out the length of the series.

### 5. Model Development: 
Linear regression has been used as the modeling algorithm for fitting the data and making predictions on out of sample data. The model actually created is (approximately) is Vehicles = 22.5 * Time + 98176. Plotting the fitted values over time shows us how fitting linear regression to the time dummy creates the trend line defined by this equation.

7. Model Evaluation: 
8. Results:
9. Result Interpretation:
