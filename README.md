### DEVELOPED BY: M.JAYACHANDRAN
### REGISTER NO: 212222240038
### DATE:

# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

### AIM:
To Compute the Auto Correlation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:

```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd


file_path = 'future_gold_price.csv'
data = pd.read_csv(file_path)


data['Close'] = pd.to_numeric(data['Close'], errors='coerce')
data_values = data['Close'].dropna().values  # Drop NaN values


mean_data = np.mean(data_values)
var_data = np.var(data_values)


normalized_data = (data_values - mean_data) / np.sqrt(var_data)


lags = range(35)
acf_values = [np.corrcoef(normalized_data[:-lag], normalized_data[lag:])[0, 1] if lag != 0 else 1 for lag in lags]


plt.figure(figsize=(10, 6))
plt.stem(lags, acf_values)
plt.title('Autocorrelation Function (ACF) for Close Prices')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.grid(True)
plt.show()


```

### OUTPUT:

![Screenshot 2024-09-22 105427](https://github.com/user-attachments/assets/fbfd666b-63cb-47fd-89bf-a38b7e4481e7)



### RESULT:
 Thus, the python code for implementing the auto correlation function is executed successfully.  
