# Week-4📈 Shopify Stock Visualization, Time-Series Analysis & Financial Insights

## 📌 Project Overview

This project performs **visualization and time-series analysis of Shopify stock data** using Python.

The analysis focuses on understanding Shopify's historical stock-price behavior, daily returns, trading activity, moving averages, and volatility patterns. The project uses **Pandas** for data processing, **NumPy** for numerical calculations, **Matplotlib** and **Seaborn** for visualization.

The project provides a visual and statistical view of:

* Open, High, Low, and Close (OHLC) prices
* Trading volume trends
* Daily closing-price movements
* 20-day and 50-day moving averages
* Daily return distributions
* Histogram and KDE analysis
* Rolling volatility
* High-volatility periods
* Overall stock stability

---

# 🎯 Project Objectives

The main objectives of this project are:

1. Load and understand Shopify historical stock data.
2. Convert the date column into a proper datetime format.
3. Sort the data chronologically for time-series analysis.
4. Visualize OHLC stock prices over time.
5. Analyze Shopify's closing-price trend.
6. Visualize trading volume over time.
7. Calculate 20-day and 50-day moving averages.
8. Compare moving averages with daily closing prices.
9. Calculate daily stock returns.
10. Visualize daily returns using histograms.
11. Generate KDE plots to study the return distribution.
12. Analyze whether returns show approximately normal or fat-tailed behavior.
13. Calculate rolling volatility.
14. Identify periods of relatively high and low volatility.
15. Generate a financial summary describing price stability and volatility patterns.

---

# 📂 Dataset

The project uses the following dataset:

```text
shopify_stock.csv
```

The dataset contains historical Shopify stock market information.

### Expected Columns

| Column   | Description                          |
| -------- | ------------------------------------ |
| `date`   | Date of stock trading                |
| `open`   | Opening stock price                  |
| `high`   | Highest price during the trading day |
| `low`    | Lowest price during the trading day  |
| `close`  | Closing stock price                  |
| `volume` | Number of shares traded              |

---

# 🛠️ Technologies Used

### Programming Language

* Python

### Libraries

* **Pandas** – Data loading, manipulation, and time-series processing
* **NumPy** – Numerical calculations
* **Matplotlib** – Line plots and financial visualizations
* **Seaborn** – Statistical plots, histogram, and KDE visualization

### Development Environment

* Google Colab
* Google Drive

---

# 📁 Project Structure

```text
Shopify-Stock-Analysis/
│
├── shopify_stock.csv
├── shopify_stock_analysis.ipynb
├── README.md
│
└── images/
    ├── ohlc_prices.png
    ├── closing_price.png
    ├── trading_volume.png
    ├── moving_averages.png
    ├── daily_returns_histogram.png
    ├── daily_returns_kde.png
    └── rolling_volatility.png
```

---

# 🔄 Analysis Workflow

The project follows the workflow below:

```text
Shopify Stock Dataset
        │
        ▼
Load CSV Data
        │
        ▼
Inspect Dataset
        │
        ▼
Convert Date Column
        │
        ▼
Sort Chronologically
        │
        ├───────────────┐
        ▼               ▼
  OHLC Analysis    Volume Analysis
        │               │
        ▼               ▼
Closing Price      Volume Trend
        │
        ▼
Moving Averages
20-Day + 50-Day
        │
        ▼
Daily Returns
        │
        ├───────────────┐
        ▼               ▼
   Histogram           KDE
        │               │
        └───────┬───────┘
                ▼
       Return Distribution
                │
                ▼
       Rolling Volatility
                │
                ▼
      Financial Insights
```

---

# 1️⃣ Import Required Libraries

The project begins by importing the required Python libraries.

```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import seaborn as sns
```

### Purpose

| Library    | Purpose                   |
| ---------- | ------------------------- |
| Pandas     | Data manipulation         |
| NumPy      | Numerical operations      |
| Matplotlib | Data visualization        |
| Seaborn    | Statistical visualization |

---

# 2️⃣ Load the Dataset

The Shopify stock dataset is loaded using Pandas.

```python
df = pd.read_csv(
    '/content/drive/MyDrive/Colab Notebooks/shopify_stock.csv'
)
```

The first five records are displayed:

```python
df.head(5)
```

This provides an initial understanding of the dataset structure.

---

# 3️⃣ Inspect Dataset Columns

The column names are checked using:

```python
df.columns
```

This helps confirm that the dataset contains the expected financial attributes.

The data types are inspected using:

```python
df.dtypes
```

This identifies whether each column has the appropriate datatype.

---

# 4️⃣ Convert Date Column

The `date` column is converted into a datetime format:

```python
df["date"] = pd.to_datetime(
    df["date"],
    utc=True
)
```

The datatype is then checked:

```python
df['date'].dtype
```

### Why Date Conversion Is Important

Time-series analysis requires dates to be stored in a proper datetime format.

This allows the project to:

* Sort records by date
* Plot data chronologically
* Calculate rolling statistics
* Analyze trends over time

---

# 5️⃣ Sort Data Chronologically

The dataset is sorted according to the date:

```python
df = df.sort_values("date")
```

Chronological ordering is important because stock-market data represents a sequence of observations over time.

---

# 📊 6️⃣ OHLC Price Visualization

OHLC stands for:

```text
O → Open
H → High
L → Low
C → Close
```
<img width="1315" height="722" alt="image" src="https://github.com/user-attachments/assets/66161bdc-bb1e-40b3-8fda-341d3767e223" />


The project visualizes all four price attributes using line plots.

```python
plt.figure(figsize=(16, 8))

plt.plot(df.index, df["open"], label="Open")
plt.plot(df.index, df["high"], label="High")
plt.plot(df.index, df["low"], label="Low")
plt.plot(df.index, df["close"], label="Close")

plt.title("Shopify Stock OHLC Prices")
plt.xlabel("Date")
plt.ylabel("Price")
plt.legend()
plt.xticks(rotation=45)

plt.show()
```
<img width="1005" height="547" alt="image" src="https://github.com/user-attachments/assets/7005e42a-c2ff-4f0f-9c8e-5147d0b533af" />

### Purpose

The OHLC plot helps visualize:

* Overall price movement
* Daily price ranges
* Differences between opening and closing prices
* High and low price behavior
* Long-term trends

---

# 📈 7️⃣ Shopify Closing Price Trend

A separate line plot is used to focus specifically on the closing price.

```python
plt.figure(figsize=(12, 6))

sns.lineplot(
    x='date',
    y='close',
    data=df
)

plt.title("Shopify's Closing Price Over Time")
plt.xlabel("Date")
plt.ylabel("Closing Price")

plt.show()
```

### Why Closing Price Is Important

The closing price is commonly used for:

* Trend analysis
* Moving averages
* Return calculations
* Volatility analysis
* Technical analysis

This visualization makes it easier to observe major upward and downward movements in Shopify's stock price.

---

# 📊 8️⃣ Trading Volume Analysis

Trading volume represents the number of shares traded during each trading session.

A volume line plot can be created using:

```python
plt.figure(figsize=(14, 6))

plt.plot(
    df["date"],
    df["volume"],
    label="Trading Volume"
)

plt.title("Shopify Trading Volume Over Time")
plt.xlabel("Date")
plt.ylabel("Volume")

plt.xticks(rotation=45)
plt.legend()
plt.grid()

plt.show()
```

### Interpretation

Large spikes in trading volume can indicate periods when trading activity was considerably higher than usual.

These periods can be investigated alongside:

* Large price movements
* Major return changes
* High volatility

However, high volume alone does not establish the cause of a price movement.

---

# 📉 9️⃣ Moving Average Analysis

Moving averages are used to smooth short-term price fluctuations and highlight broader trends.

This project uses:

* 20-day moving average
* 50-day moving average

---

## 20-Day Moving Average

```python
df["MA_20"] = df["close"].rolling(window=20).mean()
```

The 20-day moving average represents the average closing price over the previous 20 observations.

---

## 50-Day Moving Average

```python
df["MA_50"] = df["close"].rolling(window=50).mean()
```

The 50-day moving average provides a smoother representation of the medium-term price trend.

---

# 📈 10️⃣ Closing Price with Moving Averages

The closing price can be plotted alongside both moving averages.

```python
plt.figure(figsize=(15, 7))

plt.plot(
    df["date"],
    df["close"],
    label="Closing Price"
)

plt.plot(
    df["date"],
    df["MA_20"],
    label="20-Day Moving Average"
)

plt.plot(
    df["date"],
    df["MA_50"],
    label="50-Day Moving Average"
)

plt.title("Shopify Closing Price with Moving Averages")
plt.xlabel("Date")
plt.ylabel("Price")

plt.legend()
plt.xticks(rotation=45)
plt.grid()

plt.show()
```

### Purpose

This visualization helps identify:

* Short-term price trends
* Medium-term price trends
* Smoother price movements
* Periods where the stock price moves significantly away from its moving averages

The moving averages should be interpreted as descriptive indicators rather than standalone trading signals.

---

# 📈 11️⃣ Calculate Daily Returns

Daily returns measure the percentage change between consecutive closing prices.

```python
df['daily_returns'] = df['close'].pct_change()
```

### Formula

```text
Daily Return =
(Current Close - Previous Close)
-------------------------------- × 100
       Previous Close
```

The `pct_change()` function calculates the decimal return.

For example:

```text
0.05 = 5%
```

If percentage values are desired:

```python
df["daily_returns_pct"] = (
    df["daily_returns"] * 100
)
```

---

# 📊 12️⃣ Histogram of Daily Returns

A histogram is used to understand the distribution of daily returns.

```python
plt.figure(figsize=(10, 6))

sns.histplot(
    df['daily_returns'].dropna(),
    bins=50,
    kde=True
)

plt.title("Histogram of Daily Returns")
plt.xlabel("Daily Return")
plt.ylabel("Frequency")

plt.show()
```
<img width="604" height="547" alt="image" src="https://github.com/user-attachments/assets/27be48f5-66ba-42ea-b853-47b29fb74c5c" />

### What the Histogram Shows

The histogram helps identify:

* Central tendency
* Spread of returns
* Positive and negative movements
* Extreme observations
* Shape of the return distribution

---

# 📈 13️⃣ KDE Plot of Daily Returns

A Kernel Density Estimate (KDE) provides a smoothed representation of the return distribution.

```python
plt.figure(figsize=(10, 6))

sns.kdeplot(
    df['daily_returns'].dropna(),
    fill=True
)

plt.title("KDE Plot of Daily Returns")
plt.xlabel("Daily Return")
plt.ylabel("Density")

plt.show()
```
<img width="562" height="455" alt="image" src="https://github.com/user-attachments/assets/84a5fcdd-def0-41e6-ae29-7956ec4bb82a" />

### Purpose

The KDE plot helps visualize the overall shape of the distribution without relying only on histogram bins.

---

# 📊 14️⃣ Normal vs Fat-Tailed Distribution

The histogram and KDE plot can be used to examine whether daily returns appear approximately normal or show heavier tails.

### Approximately Normal Distribution

A distribution that is approximately normal often appears:

* Symmetric
* Bell-shaped
* Concentrated around the mean
* With relatively thin tails

### Fat-Tailed Distribution

A fat-tailed distribution tends to show:

* More extreme observations
* Greater probability of unusually large positive or negative returns
* Heavier tails than a normal distribution

### Important Interpretation

The visual shape alone should not be treated as a definitive statistical test for normality.

Additional tests such as the **Shapiro-Wilk test, Jarque-Bera test, or Q-Q plot** can be used for a more formal assessment.

---

# 📉 15️⃣ 20-Day Rolling Volatility

Rolling volatility measures how much daily returns vary over a moving 20-day window.

The project calculates:

```python
df["Rolling_Volatility_20"] = (
    df["daily_returns"]
    .rolling(window=20)
    .std()
)
```
<img width="1010" height="568" alt="image" src="https://github.com/user-attachments/assets/b24196f2-a63a-48ae-8b5f-b42a93433f1d" />

### Explanation

For each trading day, the standard deviation of the previous 20 daily returns is calculated.

A higher value indicates greater return variability during that rolling period.

---

# 📊 16️⃣ Rolling Volatility Visualization

The calculated volatility is plotted using:

```python
plt.figure(figsize=(12, 6))

plt.plot(
    df.index,
    df["Rolling_Volatility_20"]
)

plt.title("Shopify 20-Day Rolling Volatility")
plt.xlabel("Date")
plt.ylabel("Volatility")

plt.xticks(rotation=45)

plt.show()
```

### Interpretation

Periods where the rolling-volatility line rises indicate greater variation in recent daily returns.

Periods with relatively lower values indicate comparatively lower return variability.

---

# 📌 17️⃣ High-Volatility Period Identification

A simple way to identify relatively high-volatility periods is to compare rolling volatility with a chosen threshold.

For example, the 75th percentile can be used:

```python
volatility_threshold = (
    df["Rolling_Volatility_20"]
    .quantile(0.75)
)

high_volatility_periods = df[
    df["Rolling_Volatility_20"] >
    volatility_threshold
]

print(high_volatility_periods[
    [
        "date",
        "close",
        "daily_returns",
        "Rolling_Volatility_20"
    ]
])
```

This identifies observations whose 20-day rolling volatility is above the dataset's 75th percentile.

---

# 📊 18️⃣ Financial Stability Analysis

Stock stability can be studied using:

* Daily return dispersion
* Rolling volatility
* Price fluctuations
* Moving averages
* Frequency of extreme returns
* Trading volume

### Lower Return Variability

If daily returns remain relatively close to their average and rolling volatility is comparatively low, the analyzed period shows lower return variability.

### Higher Return Variability

If daily returns contain larger positive and negative movements and rolling volatility rises substantially, the analyzed period shows higher return variability.

These are descriptive observations about the historical dataset and do not by themselves indicate future performance.

---

# 📋 19️⃣ Financial Summary Report

## Shopify Stock Financial Summary

### Price Trend

The OHLC visualization provides an overview of Shopify's historical price movement. Comparing the opening, high, low, and closing prices helps identify periods of significant price fluctuations.

### Closing Price

The closing-price time series provides a direct view of how Shopify's stock price changed across the analyzed period.

### Moving Averages

The 20-day and 50-day moving averages smooth short-term fluctuations and provide different time horizons for observing price trends.

The 20-day average reacts more quickly to recent price changes, while the 50-day average provides a smoother medium-term representation.

### Daily Returns

Daily returns quantify percentage changes between consecutive closing prices. Large positive or negative observations represent days with relatively large price movements.

### Return Distribution

The histogram and KDE plot provide a visual representation of the distribution of daily returns. The shape, concentration, and tails can be examined to determine whether the observed distribution appears approximately normal or exhibits heavier tails.

### Volatility

The 20-day rolling standard deviation provides a time-varying measure of return variability. Peaks in rolling volatility represent periods where recent daily returns were more dispersed.

### Trading Volume

Trading volume shows how actively the stock was traded over time. Spikes in volume can be compared with price and volatility movements to identify periods of increased market activity.

---

# 🔬 20️⃣ Key Analysis Questions

This project attempts to answer the following questions:

### Price Analysis

* How did Shopify's stock price change over time?
* What were the major upward and downward price movements?
* How did Open, High, Low, and Close prices behave?

### Moving Average Analysis

* How does the 20-day moving average compare with the 50-day moving average?
* How closely does the closing price follow the moving averages?
* During which periods did prices move substantially away from their moving averages?

### Return Analysis

* What is the distribution of daily returns?
* Are extreme positive or negative returns present?
* Does the distribution appear approximately normal?
* Are the tails heavier than a typical normal distribution?

### Volatility Analysis

* Which periods show relatively high return variability?
* Which periods show comparatively lower volatility?
* How does volatility change through time?

### Volume Analysis

* How does trading volume change over time?
* Are there noticeable volume spikes?
* Do periods of high volume coincide with large price or return movements?

---

# 💻 Complete Enhanced Analysis Code

The following version combines the main requirements into one workflow:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv(
    '/content/drive/MyDrive/Colab Notebooks/shopify_stock.csv'
)

# Convert date
df["date"] = pd.to_datetime(
    df["date"],
    utc=True
)

# Sort by date
df = df.sort_values("date")

# Calculate daily returns
df["daily_returns"] = df["close"].pct_change()

# Calculate moving averages
df["MA_20"] = df["close"].rolling(20).mean()
df["MA_50"] = df["close"].rolling(50).mean()

# Calculate rolling volatility
df["Rolling_Volatility_20"] = (
    df["daily_returns"]
    .rolling(20)
    .std()
)

# ------------------------------------------------
# OHLC PRICE PLOT
# ------------------------------------------------

plt.figure(figsize=(16, 8))

plt.plot(df["date"], df["open"], label="Open")
plt.plot(df["date"], df["high"], label="High")
plt.plot(df["date"], df["low"], label="Low")
plt.plot(df["date"], df["close"], label="Close")

plt.title("Shopify Stock OHLC Prices")
plt.xlabel("Date")
plt.ylabel("Price")
plt.legend()
plt.xticks(rotation=45)
plt.grid()

plt.show()

# ------------------------------------------------
# TRADING VOLUME
# ------------------------------------------------

plt.figure(figsize=(14, 6))

plt.plot(
    df["date"],
    df["volume"]
)

plt.title("Shopify Trading Volume Over Time")
plt.xlabel("Date")
plt.ylabel("Volume")
plt.xticks(rotation=45)
plt.grid()

plt.show()

# ------------------------------------------------
# MOVING AVERAGES
# ------------------------------------------------

plt.figure(figsize=(15, 7))

plt.plot(
    df["date"],
    df["close"],
    label="Closing Price"
)

plt.plot(
    df["date"],
    df["MA_20"],
    label="20-Day MA"
)

plt.plot(
    df["date"],
    df["MA_50"],
    label="50-Day MA"
)

plt.title(
    "Shopify Closing Price with 20-Day and 50-Day Moving Averages"
)

plt.xlabel("Date")
plt.ylabel("Price")
plt.legend()
plt.xticks(rotation=45)
plt.grid()

plt.show()

# ------------------------------------------------
# DAILY RETURN HISTOGRAM
# ------------------------------------------------

plt.figure(figsize=(10, 6))

sns.histplot(
    df["daily_returns"].dropna(),
    bins=50,
    kde=True
)

plt.title("Distribution of Shopify Daily Returns")
plt.xlabel("Daily Return")
plt.ylabel("Frequency")

plt.show()

# ------------------------------------------------
# KDE PLOT
# ------------------------------------------------

plt.figure(figsize=(10, 6))

sns.kdeplot(
    df["daily_returns"].dropna(),
    fill=True
)

plt.title("KDE Plot of Shopify Daily Returns")
plt.xlabel("Daily Return")
plt.ylabel("Density")

plt.show()

# ------------------------------------------------
# ROLLING VOLATILITY
# ------------------------------------------------

plt.figure(figsize=(12, 6))

plt.plot(
    df["date"],
    df["Rolling_Volatility_20"]
)

plt.title(
    "Shopify 20-Day Rolling Volatility"
)

plt.xlabel("Date")
plt.ylabel("Volatility")

plt.xticks(rotation=45)
plt.grid()

plt.show()

# ------------------------------------------------
# FINANCIAL SUMMARY
# ------------------------------------------------

mean_return = df["daily_returns"].mean()
std_return = df["daily_returns"].std()
variance_return = df["daily_returns"].var()

print("----- Shopify Financial Summary -----")

print("Mean Daily Return:", mean_return)
print("Return Variance:", variance_return)
print("Return Standard Deviation:", std_return)

print(
    "Maximum Daily Return:",
    df["daily_returns"].max()
)

print(
    "Minimum Daily Return:",
    df["daily_returns"].min()
)

print(
    "Maximum Rolling Volatility:",
    df["Rolling_Volatility_20"].max()
)
```

---

# 📈 Expected Visualizations

The project produces the following major visualizations:

| Visualization           | Purpose                                               |
| ----------------------- | ----------------------------------------------------- |
| OHLC Line Plot          | Compare Open, High, Low, and Close prices             |
| Closing Price Plot      | Examine overall closing-price trend                   |
| Trading Volume Plot     | Analyze trading activity                              |
| Moving Average Plot     | Compare closing price with 20-day and 50-day averages |
| Return Histogram        | Examine return distribution                           |
| KDE Plot                | View smoothed return distribution                     |
| Rolling Volatility Plot | Identify periods of changing return variability       |

---

# 🧠 Learning Outcomes

By completing this project, the following concepts are demonstrated:

* Python programming
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Time-series analysis
* Financial data visualization
* OHLC analysis
* Moving averages
* Daily returns
* Statistical distributions
* Histogram analysis
* KDE analysis
* Rolling statistics
* Volatility analysis
* Exploratory Data Analysis

---

# 🚀 Future Enhancements

The project can be extended with:

### 1. Candlestick Charts

Use Plotly or other financial-charting libraries to create interactive candlestick charts.

### 2. Additional Moving Averages

Add:

* 100-day moving average
* 200-day moving average

### 3. Bollinger Bands

Calculate:

* Moving average
* Upper band
* Lower band

to visualize price dispersion around a rolling average.

### 4. Advanced Volatility Measures

Additional measures could include:

* 30-day volatility
* Annualized volatility
* Exponentially weighted volatility

### 5. Statistical Normality Tests

The return distribution can be formally tested using:

* Shapiro-Wilk
* Jarque-Bera
* Q-Q plot

### 6. Interactive Dashboard

The analysis could be converted into a dashboard using:

* Streamlit
* Plotly
* Dash

Users could select date ranges and interact with price, return, volume, and volatility charts.

---

# 📌 Conclusion

This project demonstrates how historical Shopify stock data can be transformed into meaningful visual and statistical insights using Python.

The combination of **OHLC visualization, trading-volume analysis, moving averages, daily-return distributions, KDE plots, and rolling volatility** provides a comprehensive view of historical price behavior and return variability.

The project is primarily an **exploratory and descriptive financial-data analysis**. The identified trends and volatility periods describe the historical dataset and should not be interpreted as predictions of future stock performance.

---

# 👩‍💻 Author

**C. Keerthana**
---

# ⭐ Project Highlights

```text
✔ Shopify Stock Data Analysis
✔ OHLC Price Visualization
✔ Trading Volume Analysis
✔ 20-Day Moving Average
✔ 50-Day Moving Average
✔ Daily Return Analysis
✔ Histogram & KDE
✔ Return Distribution Analysis
✔ Rolling Volatility
✔ High-Volatility Period Analysis
✔ Financial Summary
✔ Python-Based EDA
✔ Google Colab
```

---

# 📜 License

This project is created for **educational and learning purposes**.
