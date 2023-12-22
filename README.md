
```python
import numpy as np
import pandas as pd
import requests
import time

# Function to retrieve market data
def get_market_data(symbol, interval, limit):
    url = f'https://api.example.com/market-data/{symbol}/candles?interval={interval}&limit={limit}'
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        df = pd.DataFrame(data)
        df['timestamp'] = pd.to_datetime(df['timestamp'], unit='s')
        return df
    else:
        return None

# Function to implement a simple trading strategy
def simple_strategy(data):
    short_mavg = data['Close'].rolling(window=20).mean()
    long_mavg = data['Close'].rolling(window=50).mean()
    data['signal'] = np.where(short_mavg > long_mavg, 1, 0)  # Buy signal when short MA > long MA
    return data

# Order ex“ ```
No corrections.
