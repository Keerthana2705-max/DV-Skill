# Superstore Sales Data Understanding, Cleaning & Exploratory Analysis(Task-1)– Sample Superstore Sales Analysis

## 📌 Project Overview
This project performs exploratory data analysis (EDA) on the **Sample Superstore** dataset using Python. The objective is to analyze sales data, clean the dataset, create new features, and visualize important business insights.

The project demonstrates the use of data analysis libraries such as **Pandas**, **NumPy**, **Matplotlib**, and **Seaborn**.

---

## 📂 Dataset
**Dataset Used:** `samplesuperstore.csv`

The dataset contains information about:
- Orders
- Customers
- Products
- Sales
- Shipping details
- Categories
- Profit
- Regions

---

## 🎯 Objectives
- Load and explore the Superstore dataset.
- Understand the dataset structure.
- Perform data preprocessing.
- Convert date columns into datetime format.
- Calculate delivery time for each order.
- Check for missing values.
- Analyze sales by product category.
- Visualize sales distribution.

---

## 🛠️ Technologies Used

- Python 3
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn

---

## 📚 Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 📊 Project Workflow

### 1. Import Libraries
Import the required Python libraries for data analysis and visualization.

### 2. Load Dataset
Read the Sample Superstore dataset using Pandas.

### 3. Data Exploration
- Display first five rows
- Check dataset information
- Generate statistical summary

### 4. Data Preprocessing
- Convert Order Date to datetime
- Convert Ship Date to datetime

### 5. Feature Engineering
Create a new column:

**Delivery Days**

```
Delivery Days = Ship Date - Order Date
```

This calculates the number of days taken to deliver each order.

### 6. Missing Value Analysis
Identify missing values in every column.

### 7. Sales Analysis
Group sales according to product categories.

Categories include:
- Furniture
- Office Supplies
- Technology

### 8. Data Visualization

#### Sales by Category
A bar chart is generated to compare total sales among product categories.

#### Sales Distribution
A histogram is created to understand the distribution of sales values.

---

## 📈 Output Visualizations

- Sales by Category (Bar Chart)
- <img width="721" height="560" alt="image" src="https://github.com/user-attachments/assets/8460430f-5efb-42fa-91af-2677056ba98c" />

- Sales Distribution (Histogram)
- <img width="704" height="470" alt="image" src="https://github.com/user-attachments/assets/cabe3fc1-4910-4ec2-8140-96cd76f173d9" />


---

## 📋 Key Insights

- Technology, Furniture, and Office Supplies contribute differently to overall sales.
- Delivery time can be analyzed using the newly created "Delivery Days" feature.
- Sales distribution helps identify high-value and low-value orders.
- Missing value analysis ensures better data quality before further analysis.

---

## 👩‍💻 Author

**C. Keerthana**

Bachelor of Computer Applications (BCA)

Kamaraj College, Thoothukudi

---
