### Developed by: Anbuselvan.S
### Register No: 212223240008
### Date:

# Ex.No: 1B-CONVERSION OF NON STATIONARY TO STATIONARY DATA 

## AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
## ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.stattools import adfuller
%matplotlib inline

data = pd.read_csv("AirPassengers.csv")

data['timestamp'] = pd.to_datetime(data['Month'], format='%Y-%m')
data.drop('Month', axis=1, inplace=True)

data['#Passengers'].plot(title='Original Data')
plt.show()

data['Passengers_diff'] = data['#Passengers'] - data['#Passengers'].shift(1)
data['Passengers_diff'].dropna().plot(title='After Regular Differencing')
plt.show()

seasonal_period = 7
data['Passengers_seasonal_diff'] = data['#Passengers'] - data['#Passengers'].shift(seasonal_period)
data['Passengers_seasonal_diff'].dropna().plot(title='After Seasonal Adjustment')
plt.show()

data['Passengers_log'] = np.log(data['#Passengers'])
data['Passengers_log_diff'] = data['Passengers_log'] - data['Passengers_log'].shift(1)
data['Passengers_log_diff'].dropna().plot(title='After Log Transformation')
plt.show()

result = adfuller(data['#Passengers'])
print('Dickey-Fuller Test Results:')
print('Test Statistic:', result[0])
print('p-value:', result[1])
print('Critical Values:', result[4])
```
## OUTPUT:

### ORIGINAL DATA:
![image](https://github.com/user-attachments/assets/b35ab615-19ba-4561-bddb-a5d36623435a)

### REGULAR DIFFERENCING:
![image](https://github.com/user-attachments/assets/d84c047e-0fab-46a3-8fb0-36f78ff7e4f3)

### SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/9be567fc-4295-4a85-a70f-3dc7a090d086)

### LOG TRANSFORMATION:
![image](https://github.com/user-attachments/assets/d3a4c08f-2270-452f-bd85-af6d43d7fa34)

### OVERALL RESULT:
![image](https://github.com/user-attachments/assets/689d0628-8fd1-4d7f-9365-352df3c62fb1)

### RESULT:
Thus , This is the python code for the conversion of non stationary to stationary data on international airline passenger
data.
