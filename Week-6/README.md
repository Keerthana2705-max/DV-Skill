# Week-6  Healthcare Data Visualization, Cost Relationship & Policy Insights

## 📌 Project Overview

This project focuses on **healthcare data visualization, patient admission trends, billing analysis, and correlation analysis** using Python.

The analysis explores how healthcare costs vary across **medical conditions and insurance providers**, examines the distribution of billing amounts, identifies **monthly admission patterns**, and studies relationships among **patient age, hospital stay duration, and billing amount**.

The visualizations provide healthcare management insights that can support **resource planning, cost monitoring, patient-flow management, and data-driven decision-making**.

---

## 🎯 Objectives

The main objectives of this project are:

* 📊 Build stacked bar charts comparing billing amounts across medical conditions and insurance providers.
* 💰 Analyze billing amount distributions using violin plots.
* 🏥 Compare healthcare costs across different medical conditions.
* 📅 Identify monthly patient admission patterns.
* 📈 Detect periods with relatively higher or lower patient admissions.
* 🔗 Generate a correlation matrix for age, hospital stay duration, and billing amount.
* 🧠 Identify relationships among important healthcare variables.
* 📋 Develop an executive summary with healthcare management recommendations.

---

## 📂 Dataset

The project uses a healthcare dataset containing patient admission, discharge, demographic, medical, insurance, and billing information.

### Dataset File

```text
healthcare_dataset (1).csv
```

### File Path

```text
/content/drive/MyDrive/healthcare_dataset (1).csv
```

### Important Columns

| Column             | Description                            |
| ------------------ | -------------------------------------- |
| Patient ID         | Unique identifier for each patient     |
| Age                | Age of the patient                     |
| Gender             | Patient gender                         |
| Medical Condition  | Patient's medical condition            |
| Date of Admission  | Patient admission date                 |
| Discharge Date     | Patient discharge date                 |
| Insurance Provider | Patient's insurance provider           |
| Billing Amount     | Total billing amount                   |
| Admission Type     | Type of hospital admission             |
| Medication         | Medication associated with the patient |
| Test Results       | Medical test results                   |

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Google Colab**

---

# 🔄 Project Workflow

```text
Healthcare Dataset
       ↓
Data Loading & Inspection
       ↓
Date Conversion
       ↓
Hospital Stay Calculation
       ↓
Billing Analysis
       ↓
Medical Condition & Insurance Analysis
       ↓
Admission Trend Analysis
       ↓
Correlation Analysis
       ↓
Visualization
       ↓
Executive Summary & Management Insights
```

---

# 1️⃣ Data Loading and Inspection

The healthcare dataset is loaded using Pandas.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("/content/drive/MyDrive/healthcare_dataset (1).csv")

df.head()
df.shape
df.info()
df.columns
df.describe()
df.isnull().sum()
```

The dataset is inspected to understand:

* Number of records
* Number of attributes
* Data types
* Statistical characteristics
* Missing values
* Available healthcare variables

---

# 2️⃣ Date Standardization

The admission and discharge date columns are converted into proper datetime format.

```python
df["Date of Admission"] = pd.to_datetime(df["Date of Admission"])
df["Discharge Date"] = pd.to_datetime(df["Discharge Date"])
```

This conversion makes it possible to perform:

* Monthly analysis
* Time-series analysis
* Hospital stay calculations
* Date-based grouping

---

# 3️⃣ Hospital Stay Duration

The number of days each patient stayed in the hospital is calculated using admission and discharge dates.

```python
stay_days = df["Discharge Date"] - df["Date of Admission"]

df["Stay Days"] = stay_days.dt.days
```

The resulting `Stay Days` variable is used for correlation analysis.

---

# 4️⃣ Stacked Bar Chart – Billing by Medical Condition and Insurance Provider

A grouped summary is created using medical condition and insurance provider.

```python
billing = df.groupby(
    ["Medical Condition", "Insurance Provider"]
)["Billing Amount"].sum().unstack()

billing
```

A stacked bar chart is then generated:

```python
billing.plot(
    kind="bar",
    stacked=True,
    figsize=(10,6)
)

plt.title("Billing Amount by Medical Condition and Insurance Provider")
plt.xlabel("Medical Condition")
plt.ylabel("Total Billing Amount")
plt.xticks(rotation=45)
plt.show()
```

### 📊 Purpose

The stacked bar chart helps compare:

* Total billing by medical condition
* Contribution of different insurance providers
* Conditions associated with higher healthcare expenditure
* Differences in billing patterns between insurance providers

### 💡 Management Use

Healthcare administrators can use this information to identify **high-cost medical conditions** and understand how insurance providers contribute to overall billing.

---

# 5️⃣ Violin Plot – Billing Distribution

A violin plot is created to examine the distribution of billing amounts across medical conditions.

```python
plt.figure(figsize=(10,6))

sns.violinplot(
    x="Medical Condition",
    y="Billing Amount",
    data=df
)

plt.title("Distribution of Billing Amount by Medical Condition")
plt.xlabel("Medical Condition")
plt.ylabel("Billing Amount")
plt.xticks(rotation=45)
plt.show()
```

### 📊 What the Violin Plot Shows

The violin plot provides information about:

* Distribution of billing amounts
* Central tendency
* Spread of costs
* Variation between patients
* Potential concentration of high or low billing values

### 💡 Management Use

This visualization can help healthcare managers identify conditions where patient costs show **large variation**, which may warrant further investigation into treatment pathways, length of stay, or patient characteristics.

---

# 6️⃣ Monthly Patient Admissions

The admission month is extracted from the admission date.

```python
df["Admission Month"] = df["Date of Admission"].dt.month
```

Monthly admissions are then calculated:

```python
monthly_admission = df.groupby("Admission Month").size()

monthly_admission
```

A line chart is created:

```python
plt.figure(figsize=(12,6))

monthly_admission.plot(
    kind="line",
    marker="o"
)

plt.title("Monthly Patient Admissions")
plt.xlabel("Month")
plt.ylabel("Number of Admissions")
plt.xticks(rotation=45)
plt.grid()
plt.show()
```

### 📈 Purpose

The temporal line chart helps identify:

* Months with higher patient admissions
* Months with lower admissions
* Fluctuations in patient volume
* Potential seasonal patterns

### 🏥 Management Use

Admission trends can support:

* Staff scheduling
* Bed allocation
* Resource planning
* Inventory management
* Emergency department preparation

**Note:** A seasonal pattern should only be considered established if the dataset covers enough years. If the dataset contains only one year, the chart shows monthly variation rather than a confirmed recurring seasonal trend.

---

# 7️⃣ Correlation Matrix

The following variables are selected:

```python
correlation_matrix = df[
    ["Age", "Stay Days", "Billing Amount"]
].corr()

correlation_matrix
```

A heatmap is generated:

```python
sns.heatmap(
    correlation_matrix,
    annot=True,
    cmap="coolwarm"
)

plt.title("Correlation Matrix")
plt.show()
```

### 🔗 Variables Analyzed

| Variable       | Description               |
| -------------- | ------------------------- |
| Age            | Patient age               |
| Stay Days      | Duration of hospital stay |
| Billing Amount | Patient billing amount    |

### 📊 Purpose

The correlation matrix helps examine the **strength and direction of linear relationships** between:

* Age and hospital stay
* Age and billing amount
* Hospital stay and billing amount

### ⚠️ Important Interpretation

Correlation does **not** prove causation.

For example, if billing amount and stay duration show a positive correlation, this indicates that higher billing amounts tend to occur alongside longer stays in this dataset. It does not by itself establish that longer stays directly cause higher costs.

---

# 📋 Key Analytical Areas

The project provides insights into four major healthcare areas:

### 1. Cost Analysis

Billing amounts are compared across:

* Medical conditions
* Insurance providers
* Individual patients

### 2. Patient Flow Analysis

Monthly admission counts are used to understand changes in patient volume over time.

### 3. Hospital Stay Analysis

Admission and discharge dates are used to calculate patient stay duration.

### 4. Relationship Analysis

Age, stay duration, and billing amount are compared using correlation analysis.

---

# 🏥 Executive Summary

The analysis provides a visual overview of healthcare utilization, patient admissions, and financial relationships within the dataset. The stacked bar chart compares total billing across medical conditions and insurance providers, helping identify areas with relatively higher healthcare expenditure. The violin plot provides additional detail by showing how billing amounts are distributed within each medical condition.

The monthly admission line chart highlights fluctuations in patient volume over time. These patterns can help healthcare administrators plan staffing, beds, medical supplies, and operational capacity. However, a single-year dataset should be interpreted as monthly variation rather than definitive recurring seasonality.

The correlation matrix examines relationships among **patient age, hospital stay duration, and billing amount**. These relationships can help identify variables that may be useful for further cost and resource-utilization analysis, while recognizing that correlation alone does not establish causation.

---

# 💡 Healthcare Management Recommendations

### 1. Monitor High-Cost Conditions

Healthcare managers can regularly monitor medical conditions associated with higher total billing and investigate the factors contributing to those costs.

### 2. Improve Resource Planning

Monthly admission patterns can be used as one input for planning:

* Hospital beds
* Nursing staff
* Doctors
* Medical equipment
* Medicines and supplies

### 3. Analyze Long-Stay Patients

Patients with longer hospital stays can be examined to understand whether extended stays are associated with higher billing and resource utilization.

### 4. Monitor Billing Variation

Large differences in billing amounts within the same medical condition may justify additional analysis of:

* Treatment procedures
* Length of stay
* Patient characteristics
* Insurance coverage
* Resource utilization

### 5. Strengthen Insurance Cost Monitoring

Comparing insurance-provider contributions to total billing can help management understand the financial distribution of healthcare services.

### 6. Use Data for Capacity Planning

Admission trends can support data-driven operational planning rather than relying only on historical assumptions.

### 7. Extend the Analysis

Future analysis could incorporate multiple years of data to distinguish **true seasonal patterns** from short-term monthly fluctuations.

---

# 📊 Key Visualizations

The project generates the following visualizations:

### Stacked Bar Chart

**Billing Amount by Medical Condition and Insurance Provider**

Shows the contribution of different insurance providers to total billing for each medical condition.

### Violin Plot

**Distribution of Billing Amount by Medical Condition**

Shows the spread and distribution of patient billing amounts across conditions.

### Line Chart

**Monthly Patient Admissions**

Shows changes in the number of patient admissions by month.

### Correlation Heatmap

**Correlation Matrix**

Shows relationships among:

* Age
* Stay Days
* Billing Amount

---

# 📁 Suggested Project Structure

```text
Healthcare-Data-Visualization/
│
├── healthcare_dataset.csv
├── healthcare_analysis.ipynb
├── README.md
│
└── visualizations/
    ├── billing_by_condition.png
    ├── billing_violin_plot.png
    ├── monthly_admissions.png
    └── correlation_matrix.png
```

---

# 🚀 Future Enhancements

The project can be extended by adding:

* Interactive dashboards using **Plotly or Power BI**
* Year-wise admission analysis
* Medical-condition-wise average billing
* Insurance-provider comparison
* Average hospital stay by condition
* Outlier detection for unusually high billing
* Patient demographic dashboards
* Admission forecasting
* Cost prediction using machine learning
* Interactive filtering by medical condition and insurance provider

---

# 🎓 Learning Outcomes

Through this project, the following skills were practiced:

* Healthcare data analysis
* Pandas data manipulation
* Date and time processing
* GroupBy operations
* Data aggregation
* Hospital stay calculation
* Matplotlib visualization
* Seaborn visualization
* Stacked bar charts
* Violin plots
* Time-series line charts
* Correlation analysis
* Heatmap visualization
* Healthcare management interpretation
* Data-driven decision-making

---

# ✅ Conclusion

This project demonstrates how healthcare datasets can be transformed into meaningful visual and analytical insights. By combining **billing analysis, patient admission trends, hospital stay calculations, and correlation analysis**, the project provides a foundation for understanding healthcare utilization and financial patterns.

The resulting insights can support healthcare organizations in **resource planning, cost monitoring, patient-flow management, and operational decision-making**.
