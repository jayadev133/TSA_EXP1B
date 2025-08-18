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

file_path = "/content/Coffe_sales.xlsx"   
df = pd.ExcelFile(file_path)
data = df.parse('index_1')


data['date'] = pd.to_datetime(data['date'])

daily_sales = data.groupby("date")["money"].sum()


log_sales = np.log(daily_sales + 1) 

diff_sales = daily_sales.diff().dropna()

seasonal_diff_sales = daily_sales.diff(7).dropna()


plt.figure(figsize=(14, 10))

plt.subplot(4, 1, 1)
plt.plot(daily_sales, label="Original Data")
plt.title("Daily Coffee Sales (Original)")
plt.legend()

plt.subplot(4, 1, 2)
plt.plot(log_sales, label="Log Transformed", color="orange")
plt.title("Log Transformation")
plt.legend()

plt.subplot(4, 1, 3)
plt.plot(diff_sales, label="Regular Differencing", color="green")
plt.title("Regular Differencing")
plt.legend()

plt.subplot(4, 1, 4)
plt.plot(seasonal_diff_sales, label="Seasonal Differencing (7-day)", color="red")
plt.title("Seasonal Differencing (7-day)")
plt.legend()

plt.tight_layout()
plt.show()

print("Original Data Shape:", daily_sales.shape)
print("After Log Transformation Shape:", log_sales.shape)
print("After Regular Differencing Shape:", diff_sales.shape)
print("After Seasonal Differencing Shape:", seasonal_diff_sales.shape)
```

### OUTPUT:



<img width="1389" height="989" alt="TS-EXP1B" src="https://github.com/user-attachments/assets/c5bbbe57-7502-4ee3-91b4-c1a3d792df27" />



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
