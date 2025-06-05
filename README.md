# 🕸️ Web-Scraping-Amazon-Stock-Price-Data-using-Python-and-yFinance
## 🧾 What Does This Script Do?
The script:

- Gets today’s date.

- Calculates the date one year ago from today.

- Scrapes/downloads Amazon's daily historical stock data from Yahoo Finance using yfinance.

- Saves this data as a CSV file named amazon.csv.

## 🛠️ Requirements
To run this script, you need the following Python libraries:

- **pandas**

- **yfinance**

- **datetime**

_After installing the given libraries, you can now import them_ 

```
import pandas as pd
import yfinance as yf
import datetime as dt
from datetime import date, timedelta
```

To get today’s date and the date one year ago.
```
today = date.today()
d1 = today.strftime("%Y-%m-%d")
d2 = (today - timedelta(days=365)).strftime("%Y-%m-%d")
```

Now lets define the time range for scraping stock data.
```
start_date = d2
end_date = d1
```

The stock ticker for **Amazon** is **_AMZN_** so we will get its data object

```
tickerSymbol = 'AMZN'
tickerData = yf.Ticker(tickerSymbol)
```

SO finally we will get 1 year data of Amazone stock using the code below.

```
tickerDf = tickerData.history(period='1d', start=start_date, end=end_date)
tickerDf.to_csv('amazon.csv')
```

 
