# Stock Analysis with Web Scraping and Data Visualization in Python

## Project Overview
In this data project, we perform exploratory data analysis (EDA) on stock prices of major banks. The goal is to gather, analyze, and visualize stock information to gain insights into stock performance over time.

## Technology Stack
- **Pandas:** For data manipulation and cleaning.
- **Seaborn:** For data visualization.
- **Matplotlib:** For data visualization.
- **Pandas DataReader:** For fetching stock data.
- **Plotly & Cufflinks:** For interactive visualizations.

## Data Collection
We use `pandas_datareader` to fetch data from Stooq finance:

```python
import pandas_datareader.data as data
import pandas as pd
import datetime 

start = datetime.datetime(2006, 1, 1)
end = datetime.datetime(2016, 1, 1)

BAC = data.DataReader("BAC", 'stooq', start, end)
C = data.DataReader("C", 'stooq', start, end)
GS = data.DataReader("GS", 'stooq', start, end)
JPM = data.DataReader("JPM", 'stooq', start, end)
MS = data.DataReader("MS", 'stooq', start, end)
WFC = data.DataReader("WFC", 'stooq', start, end)
