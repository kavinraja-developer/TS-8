# Ex.No: 08 MOVING AVERAGE MODEL USING PYTHON
### Date: 

### AIM:

To implement Moving Average Model using python programming.

### ALGORITHM:

**Step 1:** Import Packages by Loading required libraries.

**Step 2:** Read Dataset, Import data from a CSV file.

**Step 3:** Generate White Noise by Creating random noise with specified mean and standard deviation.

**Step 4:** Apply Moving Average by Calculating moving averages over the noise.

**Step 5:** Plot Moving Average Series and Visualize the moving average data.

**Step 6:** Simulate ARMA Process to Generate data using ARMA model with given coefficients.

**Step 7:** Plot Simulated Series and Display the simulated data.

### PROGRAM:
```
Developed By : G Venkata Pavan Kumar
Reg no. : 212221240013
```
```python
# Importing Packages
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
from statsmodels.tsa.arima_process import ArmaProcess

# Reading Dataset
data = pd.read_csv("/content/Turbine_Data.csv")

# Generating White Noise
mean = 0
std = 1
n = len(data)
white_noise = np.random.normal(mean, std, size=n)

data['WhiteNoise'] = white_noise
w_series = pd.Series(white_noise)

# Applying Moving Average
window_size = 3
windows = w_series.rolling(window_size)
moving_averages = windows.mean()

# Plotting Moving Average Series
plt.figure(figsize=(18, 6))
plt.plot(moving_averages)
plt.title("Moving Average Series", fontsize=14)
plt.xlabel("Time", fontsize=14)
plt.show()

# Simulating ARMA Process
ar1 = np.array([1])
ma1 = np.array([1, 0.6])
data_subset = data['ActivePower'].iloc[:100]
MA_object = ArmaProcess(ar1, ma1)
simulated_data = MA_object.generate_sample(nsample=100)
simulated_series = pd.Series(simulated_data, index=data_subset.index)

# Plotting Simulated MA(1) Series
plt.plot(simulated_series)
plt.title("MA(1), $\\theta$ = 0.6")
plt.show()

```
### OUTPUT:

<img width="707" alt="image" src="https://github.com/Pavan-Gv/TSA_EXP8/assets/94827772/25ee0af3-5069-4cba-ac19-58c213461b0a">
<img width="344" alt="image" src="https://github.com/Pavan-Gv/TSA_EXP8/assets/94827772/86f61375-03de-4cae-a54e-23ca67440bd3">



### RESULT:
Thus we have successfully implemented the Moving Average Model using python.
