# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

df = pd.read_excel("Coffe_sales.xlsx")

print(df.head())

df['date'] = pd.to_datetime(df['date'])
df.set_index('date', inplace=True)

df['money'] = df['money'].fillna(method='ffill')

plt.figure(figsize=(14, 6))
plt.plot(df['money'], label="Original")
plt.legend()
plt.title("Original Sales Data (Entire Dataset)")
plt.show()

log_sales = np.log(df['money'])

plt.figure(figsize=(14, 6))
plt.plot(log_sales, label="Log Transformed")
plt.legend()
plt.title("Log Transformation of Sales Data (Entire Dataset)")
plt.show()

diff_sales = df['money'].diff().dropna()

plt.figure(figsize=(14, 6))
plt.plot(diff_sales, label="1st Order Differencing (Entire Dataset)")
plt.legend()
plt.title("Regular Differencing (Entire Dataset)")
plt.show()

log_diff_sales = log_sales.diff().dropna()

plt.figure(figsize=(14, 6))
plt.plot(log_diff_sales, label="Log + Differencing (Entire Dataset)")
plt.legend()
plt.title("Log + Differencing (Entire Dataset)")
plt.show()

decomposition = seasonal_decompose(df['money'], model='additive', period=12)

decomposition.plot()
plt.show()

seasonal_adjusted = df['money'] - decomposition.seasonal

plt.figure(figsize=(14, 6))
plt.plot(seasonal_adjusted, label="Seasonally Adjusted (Entire Dataset)")
plt.legend()
plt.title("Seasonally Adjusted Sales Data (Entire Dataset)")
plt.show()

```

### OUTPUT:

REGULAR DIFFERENCING:
<img width="1143" height="528" alt="REGULAR DIFFERENCING" src="https://github.com/user-attachments/assets/cab9afcf-eb26-4d17-b983-9fb118bdf36e" />
SEASONAL ADJUSTMENT:
<img width="1132" height="528" alt="SEASONAL ADJUSTMENT" src="https://github.com/user-attachments/assets/dd54b545-0f1a-44fc-81d5-2fc7fb7371a5" />
LOG TRANSFORMATION:
<img width="1136" height="528" alt="LOG TRANSFORMATION" src="https://github.com/user-attachments/assets/f143c9af-bfed-4888-bc95-27c0aaa296db" />
Original Sales Data:
<img width="1132" height="528" alt="Original Sales Data" src="https://github.com/user-attachments/assets/d04da0f2-bd71-4b46-9980-169fb2c60ef3" />
Log + Differencing:
<img width="1148" height="528" alt="Log + Differencing" src="https://github.com/user-attachments/assets/49331132-0442-4ed4-be06-b3d9bf1b1649" />
<img width="629" height="470" alt="money" src="https://github.com/user-attachments/assets/d065bb94-068b-4ff3-bbf5-bb1c85a4e8ab" />




### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
