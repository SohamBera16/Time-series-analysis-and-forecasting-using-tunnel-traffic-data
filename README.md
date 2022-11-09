# Time-series-forecasting-for-tunnel-traffic

## Steps of the project:
 ### 1. Goal/Objective:
Tunnel Traffic is a time series describing the number of vehicles traveling through the Baregg Tunnel 


### 2. Data Understanding: 
In order to understand the dataset, describe() function has been used to get information about various descriptive statistical measures like number of records in the dataset, mean value and standard deviation of the target variable, minimum and maximum values, etc.  
![data description](https://github.com/SohamBera16/Time-series-analysis-and-forecasting-using-tunnel-traffic-data/blob/main/data%20description.png)

### 3. Data preprocessing and Feature Engineering: 
In order to facilitate time series analysis, Pandas package has been used to transform the dataset accordingly. By setting the index to a date column, the "Day" column has been parsed as a date type by using `parse_dates` when loading the data. Moreover, a time dummy/time step feature has been created for generating lag features from the same by counting out the length of the series. To engineer time dummy features, a function from the statsmodels library called DeterministicProcess has also been used which can help to avoid some tricky failure cases that can arise with time series and linear regression. The order argument refers to polynomial order: 1 for linear, 2 for quadratic, 3 for cubic, and so on.

Then, We create lag features for understanding the relationship between number of vehicles on a particular day and future days. The lag plot shows us how well we were able to fit the relationship between the number of vehicles one day and the number the previous day. When creating lag features, we need to decide what to do with the missing values produced. Filling them in is one option, maybe with 0.0 or "backfilling" with the first known value. Instead, we'll just drop the missing values, making sure to also drop values in the target from corresponding dates.

![lag plot](https://github.com/SohamBera16/Time-series-analysis-and-forecasting-using-tunnel-traffic-data/blob/main/lag%20plot%20of%20tunnel%20traffic.png)

### 4. Model Development: 
Linear regression has been used as the modeling algorithm for fitting the data and making predictions on "out of sample" data. "Out of sample" refers to times outside of the observation period of the training data. The model actually created is (approximately) is Vehicles = 22.5 * Time + 98176. Plotting the fitted values over time shows us how fitting linear regression to the time dummy creates the trend line defined by this equation.
![linear trend forecast](https://github.com/SohamBera16/Time-series-analysis-and-forecasting-using-tunnel-traffic-data/blob/main/linear%20trend%20forecast.png)

### 5. Analysis: 
A moving average plot has been generated to see what kind of trend this series has. Since this series has daily observations, a window of 365 days has been chosen to smooth over any short-term changes within the year. To create a moving average, the rolling method has been used first to begin a windowed computation. It was followed by the mean method to compute the average over the window. As we can see, the trend of Tunnel Traffic appears to be about linear.

For analysing the presence of seasonality in the dataset, the seasonal plots based on weeks and years have been created. 
The seasonal plots based on days of a certain week as well as based on yearly changes look as follows - 
![seasonal plot week](https://github.com/SohamBera16/Time-series-analysis-and-forecasting-using-tunnel-traffic-data/blob/main/seasonal%20plot%20daywise.png)

Also, plot periodogram has been used to identify the dominant periods or frequencies in the time series. 
![plot periodogram](https://github.com/SohamBera16/Time-series-analysis-and-forecasting-using-tunnel-traffic-data/blob/main/plot%20periodogram.png)

### 6. Results:
After incorporating the lag features into the dataset, the predictions of the linear regression model for data that are outside the available dataset can be shown as follows - 
![seasonal forecast](https://github.com/SohamBera16/Time-series-analysis-and-forecasting-using-tunnel-traffic-data/blob/main/tunnel%20traffic%20seasonal%20forecast.png)

### 7. Result Interpretation:
The trend discovered by our LinearRegression model is almost identical to the moving average plot, which suggests that a linear trend was the right decision in this case. Also, whereas the model does predict the trend with certain degree of correctness, the predictions start to deviate from the linear trend with the progression of time. (e.g. starting around the year 2006) Hence, testing more sophisticated models for forecasting would be the next step for the project. 
