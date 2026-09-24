# 📈 Shopify Stock Data Understanding, Cleaning & Exploratory Analysis

## 📌 Project Overview

This project focuses on understanding, cleaning, and performing exploratory data analysis (EDA) on historical stock market data.

The analysis uses daily stock trading data containing important price attributes such as **Open, High, Low, Close, and Volume**. The dataset is loaded using Python and processed using **Pandas and NumPy**. Various statistical calculations and exploratory techniques are applied to understand stock price movements, daily returns, trading volume patterns, and unusual trading days.

The project also calculates the **daily price delta** and **daily percentage return**, identifies days with unusually high closing prices, analyzes trading volume trends, and summarizes the distribution of stock returns using statistical measures.

---

## 🎯 Objectives

The main objectives of this project are:

1. Load and inspect historical stock market data.
2. Clean the dataset by handling missing and duplicate records.
3. Convert the `Date` column into an appropriate datetime format.
4. Sort the stock records chronologically.
5. Analyze important stock attributes:

   * Open
   * High
   * Low
   * Close
   * Volume
6. Calculate the daily price delta.
7. Calculate daily percentage returns.
8. Identify the days with the highest and lowest returns.
9. Analyze trading volume and identify high-volume trading days.
10. Detect anomalous trading days using a threshold-based approach.
11. Calculate descriptive statistics for the stock data.
12. Understand the distribution and behavior of stock returns.

---

# 📂 Dataset

The project uses a CSV file named:

```text
AAPL.csv
```

The dataset contains historical stock market information.

### Main Attributes

| Column   | Description                            |
| -------- | -------------------------------------- |
| `Date`   | Date of stock trading                  |
| `Open`   | Opening price of the stock             |
| `High`   | Highest price during the trading day   |
| `Low`    | Lowest price during the trading day    |
| `Close`  | Closing price of the stock             |
| `Volume` | Number of shares traded during the day |

> **Note:** Although the project title mentions Shopify, the current code loads `AAPL.csv`, which represents Apple stock data. If the intended dataset is Shopify, replace the CSV with the appropriate Shopify dataset.

---

# 🛠️ Technologies Used

The project is implemented using Python.

### Programming Language

* Python

### Libraries

* **Pandas** – Data loading, cleaning, manipulation, and statistical analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization

### Development Environment

* Google Colab
* Google Drive

---

# 📥 1. Import Required Libraries

The project begins by importing the required Python libraries.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

### Purpose

* `pandas` is used for handling tabular stock market data.
* `numpy` is used for numerical calculations.
* `matplotlib` is imported for visualization.

---

# 📊 2. Load the Dataset

The CSV file is loaded using Pandas.

```python
df = pd.read_csv("/content/drive/MyDrive/Colab Notebooks/AAPL.csv")
```

The complete dataset is then displayed:

```python
print(df)
```

This helps understand the structure and contents of the dataset.

---

# 🔍 3. Initial Data Inspection

The first and last records are inspected using:

```python
print(df.head())
print(df.tail())
```

### `head()`

Displays the first five rows of the dataset.

### `tail()`

Displays the last five rows of the dataset.

The shape of the dataset is checked using:

```python
print(df.shape)
```

This returns:

```text
(number of rows, number of columns)
```

The dataset information is examined using:

```python
print(df.info())
```

This provides information about:

* Number of records
* Column names
* Data types
* Non-null values
* Memory usage

---

# 📅 4. Date Conversion

The `Date` column is converted into a datetime format:

```python
df["Date"] = pd.to_datetime(df["Date"], utc=True)
```

The datatype is verified using:

```python
df['Date'].dtype
```

### Why Date Conversion is Important

Converting the date into a proper datetime format makes it easier to:

* Sort records chronologically
* Perform time-series analysis
* Extract year/month/day information
* Analyze stock behavior over time

---

# 🧹 5. Data Cleaning

The dataset is cleaned using the following operations.

## Remove Missing Values

```python
df = df.dropna()
```

This removes rows containing missing values.

Missing values can cause problems during:

* Statistical calculations
* Return calculations
* Comparisons
* Visualization

---

## Remove Duplicate Records

```python
df = df.drop_duplicates()
```

Duplicate records are removed to ensure that each trading record is unique.

---

# 📅 6. Sort Data Chronologically

The cleaned dataset is sorted according to the trading date.

```python
df = df.sort_values("Date")
```

Chronological ordering is important for stock market time-series analysis because it allows price movements to be studied in the correct sequence.

---

# 📈 7. Descriptive Statistics

The project uses:

```python
print(df.describe())
```

The `describe()` function provides statistical information such as:

* Count
* Mean
* Standard deviation
* Minimum
* 25th percentile
* Median
* 75th percentile
* Maximum

This provides an initial understanding of the numerical stock attributes.

---

# 📋 8. Missing Value Verification

After cleaning, missing values are checked again:

```python
print(df.isnull().sum())
```

This verifies whether any missing values remain in the dataset.

---

# 💰 9. Open and Close Price Analysis

The project calculates the average, maximum, and minimum values of the `Open` and `Close` prices.

```python
avg = df[["Close", "Open"]].mean()
max = df[["Close", "Open"]].max()
min = df[["Close", "Open"]].min()

print(avg, max, min)
```

This provides a basic understanding of the stock's opening and closing price ranges.

---

# 📌 10. Price Threshold and Anomaly Detection

A threshold is calculated using:

```python
threshold = 2 * avg
```

This creates a threshold equal to twice the average price.

Anomalous trading days are then identified using:

```python
anolomous_days = df[df["Close"] > threshold["Close"]]
```

The selected records represent trading days where the closing price exceeded twice the average closing price.

### Important Note

This is a **simple threshold-based anomaly detection method**. It does not necessarily mean that these days are statistically anomalous.

More advanced approaches could use:

* Z-score
* IQR
* Rolling averages
* Standard deviation bands
* Isolation Forest

---

# 💵 11. Daily Price Delta

Daily price delta measures the difference between the closing price and opening price.

### Formula

```text
Daily Delta = Close - Open
```

The calculation is performed using:

```python
df["Daily_delta"] = df["Close"] - df["Open"]
```

### Interpretation

* Positive value → Closing price is higher than opening price.
* Negative value → Closing price is lower than opening price.
* Zero → Opening and closing prices are equal.

---

# 📈 12. Identify Top Positive Price Changes

The project identifies the top 10 positive daily price changes.

```python
top_10_positive = (
    df[df["Daily_delta"] > 0]
    .nlargest(10, "Daily_delta")
)

print(top_10_positive)
```

This helps identify trading days with the largest absolute increase between opening and closing prices.

---

# 📊 13. Daily Percentage Return

Daily percentage return measures the percentage change between the opening and closing prices.

### Formula

```text
Daily Return (%) =
((Close - Open) / Open) × 100
```

The calculation is implemented as:

```python
df["daily_return"] = df["Close"] - df["Open"]

df["daily_return"] = (
    df["daily_return"] / df["Open"]
) * 100
```

### Interpretation

For example:

```text
Open  = $100
Close = $105
```

Then:

```text
Daily Return = ((105 - 100) / 100) × 100
             = 5%
```

A positive return indicates an increase, while a negative return indicates a decrease.

---

# 🟢 14. Highest Daily Returns

The top 10 daily returns are identified using:

```python
highest_10_returns = (
    df[df["daily_return"].notna()]
    .nlargest(10, "daily_return")
)

print(highest_10_returns)
```

This identifies the trading days with the largest positive percentage movements from Open to Close.

---

# 🔴 15. Lowest Daily Returns

The bottom 10 daily returns are identified using:

```python
lowest_10_returns = (
    df[df["daily_return"].notna()]
    .nsmallest(10, "daily_return")
)

print(lowest_10_returns)
```

These records represent the days with the largest negative percentage movements from Open to Close.

---

# 📦 16. Trading Volume Analysis

Trading volume indicates the number of shares traded during a particular day.

The project summarizes volume using:

```python
print(df['Volume'].describe())
```

This provides:

* Count
* Mean
* Standard deviation
* Minimum
* Maximum
* Quartiles

---

# 📊 17. Mean and Median Trading Volume

The average trading volume is calculated using:

```python
mean_volume = df['Volume'].mean()
```

The median trading volume is calculated using:

```python
median_volume = df['Volume'].median()
```

The results are displayed using:

```python
print("\nMean Volume:", mean_volume)
print("Median Volume:", median_volume)
```

### Why Mean and Median?

Comparing mean and median can provide an indication of whether trading volume contains unusually large values.

For example:

```text
Mean > Median
```

may indicate that some high-volume trading days are pulling the average upward.

---

# 🔝 18. Highest Trading Volume Days

The 10 days with the highest trading volume are identified using:

```python
highest_volume_days = df.nlargest(10, 'Volume')
```

The relevant columns are displayed:

```python
print(
    highest_volume_days[
        ['Date', 'Open', 'Close', 'Volume']
    ]
)
```

This allows high-volume trading days to be compared with their opening and closing prices.

---

# 📋 19. Anomalous Trading Days Summary

The project displays important information for identified anomalous days:

```python
print(
    anolomous_days[
        [
            "Date",
            "Open",
            "Close",
            "Daily_delta",
            "daily_return",
            "Volume"
        ]
    ]
)
```

The output contains:

| Attribute    | Purpose                           |
| ------------ | --------------------------------- |
| Date         | Trading date                      |
| Open         | Opening stock price               |
| Close        | Closing stock price               |
| Daily Delta  | Difference between Close and Open |
| Daily Return | Percentage return                 |
| Volume       | Number of shares traded           |

---

# 📉 20. Stock Return Distribution Statistics

The project can be extended to summarize the distribution of daily returns using three important statistical measures.

## Mean

Mean represents the average daily return.

```python
mean_return = df["daily_return"].mean()
```

Formula:

```text
Mean = Σx / n
```

A positive mean indicates that the average Open-to-Close movement was positive over the analyzed period, while a negative mean indicates an average negative movement.

---

## Variance

Variance measures how widely daily returns are distributed around their mean.

```python
variance_return = df["daily_return"].var()
```

A higher variance indicates greater dispersion in daily returns.

---

## Standard Deviation

Standard deviation measures the typical spread of returns around the mean.

```python
std_return = df["daily_return"].std()
```

A higher standard deviation indicates greater variability in daily returns.

---

# 📊 Return Statistics Code

The following code can be added to the project to generate the complete return distribution summary:

```python
mean_return = df["daily_return"].mean()
variance_return = df["daily_return"].var()
std_return = df["daily_return"].std()

print("Mean Return:", mean_return)
print("Variance of Return:", variance_return)
print("Standard Deviation of Return:", std_return)
```

---

# 🔬 Complete Analysis Workflow

The overall project follows this workflow:

```text
                Stock CSV Dataset
                       │
                       ▼
              Load Dataset
                       │
                       ▼
             Inspect the Data
                       │
                       ▼
              Data Cleaning
          ┌────────────┴────────────┐
          ▼                         ▼
     Missing Values             Duplicates
          │                         │
          └────────────┬────────────┘
                       ▼
               Date Conversion
                       │
                       ▼
             Sort by Date
                       │
                       ▼
          Descriptive Statistics
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
      Price Delta   Daily Return   Volume
          │            │            │
          ▼            ▼            ▼
      Top Positive  Highest/Lowest  High Volume
       Changes        Returns          Days
          │            │            │
          └────────────┼────────────┘
                       ▼
             Anomaly Detection
                       │
                       ▼
             Return Statistics
       Mean | Variance | Std. Deviation
                       │
                       ▼
                 EDA Insights
```

---

# 📌 Key Metrics Analyzed

The project focuses on the following metrics:

### Price Metrics

* Average Open Price
* Average Close Price
* Minimum Open Price
* Maximum Open Price
* Minimum Close Price
* Maximum Close Price

### Return Metrics

* Daily Price Delta
* Daily Percentage Return
* Highest Daily Returns
* Lowest Daily Returns
* Mean Return
* Return Variance
* Return Standard Deviation

### Volume Metrics

* Mean Trading Volume
* Median Trading Volume
* Minimum Volume
* Maximum Volume
* Highest Volume Trading Days

### Anomaly Metrics

* Price threshold
* Trading days exceeding the threshold
* Daily delta on anomalous days
* Daily return on anomalous days
* Trading volume on anomalous days

---

# 💡 Insights That Can Be Derived

The analysis can be used to understand:

1. General stock price behavior over the selected period.
2. The average opening and closing price.
3. The magnitude of daily price movements.
4. Trading days with unusually high positive or negative returns.
5. Trading volume concentration on particular days.
6. The variability of stock returns.
7. Potential unusual observations based on the selected threshold.
8. The relationship between large price movements and trading volume.

The actual conclusions depend on the values obtained from the dataset and the time period represented by `AAPL.csv`.

---

# ⚠️ Important Note About Daily Return

The current implementation calculates return from **Open to Close**:

```text
(Close - Open) / Open × 100
```

This is different from the commonly used **close-to-close daily return**, which is:

```text
(Current Close - Previous Close) / Previous Close × 100
```

For example, a close-to-close return can be calculated with:

```python
df["daily_return_close"] = (
    df["Close"].pct_change() * 100
)
```

Both measures are useful, but they represent different concepts.

---

# 🚀 Future Enhancements

The project can be further improved by adding:

### 1. Data Visualization

Create charts for:

* Open vs Close prices
* Stock price trend
* Daily returns
* Trading volume
* Moving averages
* Return distribution

Example:

```python
plt.figure(figsize=(12, 6))

plt.plot(df["Date"], df["Close"])

plt.title("Stock Closing Price Trend")
plt.xlabel("Date")
plt.ylabel("Closing Price")

plt.xticks(rotation=45)
plt.grid()

plt.show()
```

---

### 2. Moving Average Analysis

Calculate:

* 20-day moving average
* 50-day moving average
* 200-day moving average

Example:

```python
df["MA_20"] = df["Close"].rolling(20).mean()
df["MA_50"] = df["Close"].rolling(50).mean()
```

---

### 3. Advanced Anomaly Detection

Instead of only using:

```python
Close > 2 × Average Close
```

the project can use:

* Z-score
* IQR
* Rolling standard deviation
* Isolation Forest

---

### 4. Correlation Analysis

Analyze relationships between:

* Open and Close
* High and Close
* Low and Close
* Volume and Return

Example:

```python
correlation = df[
    ["Open", "High", "Low", "Close", "Volume"]
].corr()

print(correlation)
```

---

### 5. Interactive Dashboard

The project can be converted into an interactive dashboard using:

* Streamlit
* Plotly
* Dash

Users could select a date range and interactively explore stock prices, returns, and trading volume.

---

# 📁 Suggested Project Structure

```text
Stock-Data-EDA/
│
├── AAPL.csv
├── stock_analysis.ipynb
├── README.md
└── images/
    ├── stock_price.png
    ├── daily_returns.png
    └── trading_volume.png
```

---

# 🧪 How to Run the Project

## Step 1: Open Google Colab

Open a new Google Colab notebook.

## Step 2: Upload Dataset

Upload:

```text
AAPL.csv
```

or place it in Google Drive.

## Step 3: Update the File Path

Modify:

```python
df = pd.read_csv(
    "/content/drive/MyDrive/Colab Notebooks/AAPL.csv"
)
```

according to the location of your dataset.

## Step 4: Install Required Libraries

Most of the required libraries are already available in Google Colab.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

## Step 5: Run the Notebook

Execute the cells sequentially to:

1. Load the data
2. Inspect the dataset
3. Clean the data
4. Calculate price delta
5. Calculate returns
6. Analyze trading volume
7. Identify unusual days
8. Calculate return statistics

---

# 🎓 Learning Outcomes

Through this project, the following concepts are demonstrated:

* Python programming
* Pandas DataFrame operations
* NumPy numerical operations
* CSV data loading
* Data cleaning
* Missing-value handling
* Duplicate removal
* Datetime conversion
* Data sorting
* Descriptive statistics
* Financial data analysis
* Percentage calculations
* Return analysis
* Trading volume analysis
* Basic anomaly detection
* Exploratory Data Analysis

---

# 📌 Conclusion

This project provides a structured exploratory analysis of historical stock market data. It demonstrates how raw stock data can be loaded, cleaned, transformed, and analyzed using Python.

By calculating **daily price delta, daily percentage returns, trading volume statistics, anomaly indicators, mean, variance, and standard deviation**, the project provides a foundation for understanding stock price movements and return variability.

The analysis can be further extended with advanced visualization, technical indicators, statistical anomaly detection, correlation analysis, and interactive dashboards.

---

## 👩‍💻 Author

**C. Keerthana**
---

## ⭐ Project Highlights

```text
✔ Stock Market Data Analysis
✔ Data Cleaning
✔ Exploratory Data Analysis
✔ Daily Price Delta Calculation
✔ Daily Return Calculation
✔ Trading Volume Analysis
✔ Anomaly Detection
✔ Statistical Analysis
✔ Python & Pandas
✔ Google Colab
```

---

## 📜 License

This project is intended for educational and learning purposes.
