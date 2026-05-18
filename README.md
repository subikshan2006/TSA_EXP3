# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
## Date: 02/05/2026 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.

### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.

### PROGRAM:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load your dataset
df = pd.read_csv('/content/drive/MyDrive/COLAB PROJECTS/Time Series/Batsmen.csv')

# Display columns (to help you confirm column name)
print("Columns in dataset:", df.columns)

data = df['Runs'].dropna().values 

# Parameters
N = len(data)
lags = range(35)

autocorr_values = []

# Mean and Variance
mean_data = np.mean(data)
variance_data = np.var(data)

# ACF Calculation
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# Plot ACF
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)

plt.title('Autocorrelation Function (ACF)')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')

plt.grid(True)
plt.show()

```
### OUTPUT:
<img width="1081" height="696" alt="image" src="https://github.com/user-attachments/assets/d5f61085-1be9-4199-a042-a4a840950071" />



### RESULT:
Thus we have successfully implemented the auto correlation function in python.
