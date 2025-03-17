# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

### Date:


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
~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Load the data
# Adjust the path and column name as needed
data = pd.read_csv('electric_production.csv')


production = data['Production']
~~~


# Calculate mean and variance
~~~
mean_production = np.mean(production)
variance_production = np.var(production)
~~~~

# Normalize the data by subtracting the mean
~~~
normalized_production = production - mean_production
~~~
# Pre-allocate the autocorrelation table
~~~
acf_values = np.zeros(36)
~~~
# Compute autocorrelation for each lag from 0 to 35
~~~
n = len(normalized_production)
for lag in range(36):
    # Calculate the autocorrelation for the current lag
    autocovariance = np.sum(normalized_production[:n-lag] * normalized_production[lag:]) / n
    acf_values[lag] = autocovariance / variance_production
~~~
# Display the ACF graph
~~~
plt.figure(figsize=(10, 6))
plt.stem(range(36), acf_values, use_line_collection=True)
plt.title('Autocorrelation Function (ACF) of Electric Production')
plt.xlabel('Lags')
plt.ylabel('ACF')
plt.grid(True)
plt.show()


~~~

### OUTPUT:
<img width="840" alt="image" src="https://github.com/user-attachments/assets/3c50f6f3-93d8-409a-a2ae-2d759b19fb55">


### RESULT:

Thus the python code is successfully implemented the auto correlation function in python.
