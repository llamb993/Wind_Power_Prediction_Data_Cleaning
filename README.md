### Wind_Power_Prediction_Data_Cleaning
The aim of the project was to clean a data set which can then go on to be used to build a machine learning model that could predict the active power of a wind turbine.

The dataset used was the ‘Wind Power Forecasting’ dataset from kaggle see link: https://www.kaggle.com/datasets/theforcecoder/wind-power-forecasting. There were 21 dependent variables and the independent variable was ‘Active Power’.
While the format of the data was time series for the purposes of the wind power prediction project the data was treated as independent data points.

**Nulls**
Initial analysis showed there were a lot of missing values. There are 22734 rows with all nulls, they were dropped. The variables were chosen to be dropped as this was less than 20% of overall values and there was a significant amount of data left.

**Negative Values**
ActivePower has a minimum of -38 - power can be a negative value, so values below 0 were removed. Ideally don’t want to edit the target variable but I believe these values are incorrect and so needed to be transformed. 
An assumption was also made that blade pitching angle can’t be negative so negatives were removed. 

**Non Unique Values**
There are 22734 rows which all the vales are nan and WTG is G01.
WTG and ControlBoxTemperature will be removed as it contains no unique values so will not be help full in model building.

**Test Train Split**
Data was split into test and training data sets prior to scaling. 

**Scaling** 
Data was scaled using MinMax Scaler. It scales the features to a specific range, typically between 0 and 1. 

**Future Data Cleaning**
Further data cleaning could be done. The Reactive Power variable may have outliers - the mean is 88, the max is 403 and the quartiles are in the 88 range. This could indicate high values are outliers. Box plots should be plotted to check. 
This is the same for the BladePitchAngle variables. The means are 9-10, the max is 90 and the quartiles are in the range of 9. 
It is interesting that the blade pitching angles contain roughly the same number of missing rows. As well as the widening temperature and gear box variables. Without having more information on these variables within the wind turbine context it is hard to make assumptions about what null values may indicate, i.e they could give more information about when the turbine is static or even when equipment has broken. It is a shame to loose this information however all other nulls will be removed so I can continue with the data assessment - this is not ideal as we are loosing a significant amount of data. Future data cleaning. Could forward or backward fill these values and retain more information. 
Another area of data investigation and cleaning is multicollinearity where two or more independent variables are highly correlated with each other. This can cause problems with feature interpretation, overfitting, and model instability. 
