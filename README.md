# Project Title:
Machine Learning Time Series Forecasting on Web Traffic dataset
#
---
# Project Description:
Task is Time Series Forecasting on Web Traffic dataset with ARIMA, SARIMA and PROPHET models. Forecast was made for each device type (separately) and forecast the total cumulaive traffic.  
#
---
# Table of Contents:

  1. Data Cleaning
  2. Exploratory data analysis
  3. Data Preprocessing 
  4. Data Engineering
  5. Model Training
  6. Model Hyperparameter Optimization
  7. Model Evaluation
  8. Conclusion and Results
---
#

--
# CONCLUSION from EDA, Data preprocessing and Data engineering for ALL DEVICES:

---
## Handling outliers 
The most extreme 4 outliers shown as peak in the plot were deleted and then imputed with mean value of the dataset.    

## Decomposition of the endogenous variable

**Trend Component**: Does not show persistent increasing or decreasing direction in the data.

**Seasonal Component**: This component captures regular patterns that occur over a period of 7 days.

**Residual Component**: This component represents the remaining random fluctuations in the data after removing the trend and seasonal components. Nothing particular can be seen at this point.      

## Stationarity test: 
Stationary test faied, so I appled logarithm function and I did all the additional steps to make it stationary. 
    
Stationarity test after these transformations failed again. Here I assumed that the reason for this is the values in the last year - 2019, which are dropping sharply and they seemed as they were not real data. Since I have a large dataset, I decided to remove those values in order to obtain a better forecast. 

After this step the dataset passed the stationarity test and it is ready for Time Series Forecasting with ARIMA, SARIMA and PROPHET models.  

I'm saving the files in order to train the models on clean dataset in additional notebooks.

---

# CONCLUSION from EDA, Data preprocessing and Data engineering PER DEVICE:

## Handling outliers 
ONLY the most extreme outliers, shown as peak in the plots, were deleted and then imputed with mean value of the dataset.    

## Decomposition of the endogenous variable

**Trend Component**: Does not show persistent increasing or decreasing direction in the data.

**Seasonal Component**: This component captures regular patterns that occur over a period of 7 days.

**Residual Component**: This component represents the remaining random fluctuations in the data after removing the trend and seasonal components. Nothing particular can be seen at this point.      

## Stationarity test: 
All features failed the stationary test, so I appled logarithm function and I did all the additional steps to make it stationary. 
Before log function was applied, I've replaced two 0 values from the dataset with mean value, firstly because I don't want to get infinity when applying log function, and second if I only add some epsilon value to these zeros, I'll receive outlies once again.
    
Stationarity test after these transformations failed again. Here I assumed that the reason for this are the values in the last year - 2019, which are dropping sharply and they seemed as they were not real data. Since I have a large dataset, I decided to remove those values in order to obtain a better forecast. 

After this the dataset passed the stationarity test and it is ready for Time Series Forecasting with ARIMA, SARIMA and PROPHET models.  

I'm saving the files in order to train the models on clean dataset in additional notebooks.

---

# RESULTS:

## device: DESKTOP
![image](https://github.com/VesnaPop-Dimitrijoska/ML-Time-Series-Forecasting-WebTraffic/assets/144008804/2dafb76b-7851-4fb8-83ab-e05a420d4940)

All of the models demonstrated **EXCELLENT** forecasting performance on the test dataset, as evidenced by both visual representation of the predictions and the comprehensive evaluation metrics used.

---
## device: MOBILE
![image](https://github.com/VesnaPop-Dimitrijoska/ML-Time-Series-Forecasting-WebTraffic/assets/144008804/e3878a24-4bf9-4e69-bc15-0eb73532a3a3)

All of the models demonstrated GOOD forecasting performance on the test dataset, as evidenced by both visual representation of the predictions and the comprehensive evaluation metrics used.

Note: 
1. SARIMA model gave same result with seasonal_order component s = 0 and of s = 7
2. These metrics are calculated on the test split of the dataset. In a real forecasting model, such tests can only be done after the forecast period.

---
## device: TABLET
![image](https://github.com/VesnaPop-Dimitrijoska/ML-Time-Series-Forecasting-WebTraffic/assets/144008804/2787a4d7-22c4-45b0-b0e6-e61e10ab2ecb)

All of the models demonstrated NOT SO GOOD forecasting performance on the test dataset, as evidenced by both visual representation of the predictions and the comprehensive evaluation metrics used.
However PROPHET model is preforming best of all models.

---
## ALL DEVICES
![image](https://github.com/VesnaPop-Dimitrijoska/ML-Time-Series-Forecasting-WebTraffic/assets/144008804/e19990fb-253c-4319-8c3f-6a953924caae)

All of the models demonstrated **EXCELLENT** forecasting performance on the test dataset, as evidenced by both visual representation of the predictions and the comprehensive evaluation metrics used.

Note: These metrics are calculated on the test split of the dataset. In a real forecasting model, such tests can only be done after the forecast period.

---
#
# License
MIT License
#
