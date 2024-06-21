We combine these dataframes into a single dataframe:

python
Copy code
tickers = ['BAC', 'C', 'GS', 'JPM', 'MS', 'WFC']
bank_stocks = pd.concat([BAC, C, GS, JPM, MS, WFC], axis=1, keys=tickers)
bank_stocks.columns.names = ['Bank Tickers', 'Stock info']
Exploratory Data Analysis (EDA)
Maximum Closing Stock Price
We find the maximum closing stock price for each bank:

python
Copy code
bank_stocks.xs(key='Close', axis=1, level='Stock info').max()
Calculating Stock Returns
We calculate daily returns for each stock:

python
Copy code
returns = pd.DataFrame()
for tick in tickers:
    returns[tick + ' Return'] = bank_stocks[tick]['Close'].pct_change()
Visualizing Stock Returns
We create a pairplot of the returns dataframe:

python
Copy code
sns.pairplot(returns[1:])
Best and Worst Single Day Returns
We find the best and worst single day returns for each stock:

python
Copy code
returns.idxmin()
returns.idxmax()
Standard Deviation of Returns
We calculate the standard deviation of returns to classify the stock based on risk:

python
Copy code
returns.std()
returns.loc['2015-01-01':'2015-12-31'].std()
Distribution Plots
We create distribution plots for specific time periods:

python
Copy code
sns.displot(returns.loc['2015-01-01':'2015-12-31']['MSReturn'], color='green', bins=100)
sns.displot(returns.loc['2008-01-01':'2008-12-31']['CReturn'], color='red', bins=50)
Visualization
Line Plot of Closing Prices
We create a line plot showing the closing price for each bank:

python
Copy code
for tick in tickers:
    bank_stocks[tick]['Close'].plot(figsize=(12, 4), label=tick)
plt.legend()
Interactive Plot using Plotly and Cufflinks
We create an interactive plot of the closing prices:

python
Copy code
bank_stocks.xs(key='Close', axis=1, level='Stock info').iplot()
Conclusion
This project demonstrates the use of web scraping and data visualization techniques in Python to analyze stock data. By leveraging Pandas, Seaborn, Matplotlib, and interactive visualization libraries like Plotly and Cufflinks, we can effectively explore and present stock performance insights.
