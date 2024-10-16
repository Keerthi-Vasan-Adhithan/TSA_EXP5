### Developed by: KEERTHI VASAN A
### Register Number:212222240048
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on Apple stock price dataset.

### ALGORITHM:
1. Import the required packages like pandas.
2. Load the dataset using pandas.
3. Use the seasonal_decompose function to break down the time series data into trend, seasonal, and residual components.
4. Plot the seasonal decomposition, trend, and residuals.
5. Summarize and show the decomposition results.

### PROGRAM:
```PY
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the data
data = pd.read_csv('/content/apple_stock.csv')

# Ensure the 'Date' column is in datetime format and set it as the index
data['Date'] = pd.to_datetime(data['Date'], errors='coerce')
data = data.dropna(subset=['Date'])  # Drop any rows with invalid dates
data.set_index('Date', inplace=True)

# Convert 'Close' to numeric (if not already), and handle missing values
data['Close'] = pd.to_numeric(data['Close'], errors='coerce')
data = data.dropna(subset=['Close'])  # Drop rows with missing 'Close' values

# Plot the original time series data (stock prices)
plt.figure(figsize=(12, 6))
plt.plot(data['Close'], label='Stock Price')
plt.title('Apple Stock Prices Over Time')
plt.legend()
plt.show()

# Perform time series decomposition
# Use a period appropriate for stock data (e.g., 252 trading days per year)
period = 252  # Adjust this value if necessary
result = seasonal_decompose(data['Close'], model='multiplicative', period=period)

# Plot the decomposition results: Trend, Seasonal, and Residual components

# Plot original data
plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)
plt.plot(data['Close'], label='Original Data', color='blue')
plt.title('Original Time Series')
plt.legend()

# Plot the trend component
plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='orange')
plt.title('Trend Component')
plt.legend()

# Plot the seasonal component
plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()

# Plot the residual (remainder) component
plt.subplot(4, 1, 4)
plt.plot(result.resid, label='Residuals', color='red')
plt.title('Residuals Component')
plt.legend()

plt.tight_layout()
plt.show()

```
### OUTPUT:
#### FIRST FIVE ROWS:
![{5E3BA59F-9EA2-4B6F-B12B-338D643C203A}](https://github.com/user-attachments/assets/306ca6be-404e-4b20-9b90-3988e2f879e8)

#### PLOTTING THE DATA:
![{C41AF471-74C2-43B2-AB12-89745AC37BF9}](https://github.com/user-attachments/assets/b4d3d453-7fa3-409c-9d5f-85a75e04be8a)

#### SEASONAL PLOT REPRESENTATION :
![{51CE8C93-5769-4662-9BC0-71BF74ED9B4F}](https://github.com/user-attachments/assets/461c2ccd-05d2-47cc-a995-b88c82818a56)

#### TREND PLOT REPRESENTATION :
![{AAD2A82A-AF03-4711-9EF6-0A58B7DA3162}](https://github.com/user-attachments/assets/8cf91db3-ba69-405a-89e1-dfe116792780)

#### OVERAL REPRESENTATION:
![{0357B944-A563-493D-BC7D-0B4F976FEDE3}](https://github.com/user-attachments/assets/2d86ef63-bcf5-4805-9944-a4241dbdb6b9)

### RESULT:
Thus, we have successfully illustrated a Python program to perform time series analysis and decomposition on the Apple stock price dataset.
