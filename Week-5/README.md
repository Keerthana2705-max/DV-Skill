# Week-5🏥  Healthcare Data Understanding, Cleaning & Exploratory Analysis


## 📌 Project Overview

This project focuses on **healthcare data cleaning, preprocessing, statistical analysis, and demographic segmentation** using Python and Pandas.

The dataset contains **500 patient records** with information about patient demographics, medical conditions, admission types, medical codes, billing amounts, admission dates, and discharge dates.

The project performs data-quality checks, handles missing values, standardizes date attributes, cleans medical-code information, categorizes hospital admissions according to urgency, calculates hospital stay duration, and summarizes patient billing and hospitalization statistics.

The analysis also supports demographic segmentation based on different medical conditions.

---

# 🎯 Objectives

The main objectives of this project are:

1. Load and understand the healthcare dataset.
2. Inspect the structure and data types of the dataset.
3. Identify and handle missing values.
4. Clean and standardize medical-code attributes.
5. Convert admission and discharge dates into datetime format.
6. Standardize admission-type values.
7. Categorize admissions by:

   * Emergency
   * Urgent
   * Elective/Routine
8. Calculate hospital stay duration in days.
9. Calculate summary statistics for billing amounts.
10. Calculate summary statistics for hospital stays.
11. Analyze admission-type distribution.
12. Segment patient demographics by medical condition.
13. Prepare the dataset for further healthcare analytics and visualization.

---

# 📂 Dataset

The project uses:

```text
healthcare_dataset.csv
```

The dataset contains **500 rows and 9 original columns**.

### Dataset Columns

| Column              | Description                        |
| ------------------- | ---------------------------------- |
| `Patient_ID`        | Unique identifier for each patient |
| `Gender`            | Patient gender                     |
| `Age`               | Patient age                        |
| `Medical_Condition` | Primary medical condition          |
| `Admission_Date`    | Date of hospital admission         |
| `Admission_Type`    | Type of admission                  |
| `Medical_Code`      | Medical/diagnostic code            |
| `Billing_Amount`    | Patient hospital billing amount    |
| `Discharge_Date`    | Date of hospital discharge         |

A derived column is also created:

| Column               | Description                                    |
| -------------------- | ---------------------------------------------- |
| `Hospital_Stay_Days` | Number of days between admission and discharge |

---

# 📊 Dataset Overview

The dataset contains:

```text
Rows    : 500
Columns : 9
```

The original columns have the following data types:

```text
Patient_ID          object
Gender              object
Age                  int64
Medical_Condition   object
Admission_Date      object
Admission_Type      object
Medical_Code        object
Billing_Amount     float64
Discharge_Date      object
```

After date conversion, the date attributes become:

```text
Admission_Date     datetime64[ns]
Discharge_Date     datetime64[ns]
```

---

# 🛠️ Technologies Used

## Programming Language

* Python

## Libraries

* **Pandas** – Data loading, cleaning, transformation, and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization

## Development Environment

* Google Colab
* Google Drive

---

# 📁 Suggested Project Structure

```text
Healthcare-Data-Analysis/
│
├── healthcare_dataset.csv
├── healthcare_analysis.ipynb
├── README.md
│
└── images/
    ├── admission_types.png
    ├── medical_conditions.png
    ├── billing_distribution.png
    └── hospital_stay_distribution.png
```

---

# 🔄 Project Workflow

```text
Healthcare Dataset
        │
        ▼
     Load Data
        │
        ▼
   Inspect Dataset
        │
        ├───────────────┐
        ▼               ▼
   Data Types      Missing Values
        │               │
        └───────┬───────┘
                ▼
          Data Cleaning
                │
        ┌───────┴────────┐
        ▼                ▼
 Medical Codes       Date Attributes
        │                │
        └────────┬───────┘
                 ▼
       Admission Standardization
                 │
                 ▼
       Hospital Stay Calculation
                 │
       ┌─────────┴─────────┐
       ▼                   ▼
 Billing Analysis     Demographic Analysis
       │                   │
       └─────────┬─────────┘
                 ▼
          Healthcare Insights
```

---

# 1️⃣ Import Required Libraries

The required Python libraries are imported first.

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

### Purpose

| Library    | Purpose                        |
| ---------- | ------------------------------ |
| Pandas     | Data manipulation and analysis |
| Matplotlib | Data visualization             |
| Seaborn    | Statistical visualization      |

---

# 2️⃣ Load the Dataset

The healthcare dataset is loaded using Pandas.

```python
df = pd.read_csv(
    "/content/drive/MyDrive/Colab Notebooks/healthcare_dataset.csv"
)
```

The complete DataFrame can be displayed using:

```python
df
```

---

# 3️⃣ Inspect the First Records

The first five records are displayed using:

```python
df.head()
```

This helps verify:

* Column names
* Data values
* Data structure
* Initial formatting

Example records include:

```text
P1001 → Male → 45 → Hypertension
P1002 → Female → 32 → Pneumonia
P1003 → Male → 68 → Diabetes Type 2
```

---

# 4️⃣ Inspect Dataset Information

The structure of the DataFrame is examined using:

```python
df.info()
```

The dataset contains:

```text
500 entries
9 columns
```

Before preprocessing, the date columns are stored as `object` values.

---

# 5️⃣ Descriptive Statistics

The numerical columns are summarized using:

```python
df.describe()
```

### Results

| Statistic          |    Age | Billing Amount |
| ------------------ | -----: | -------------: |
| Count              |    500 |            500 |
| Mean               | 50.106 |       7249.001 |
| Standard Deviation | 15.328 |       3198.969 |
| Minimum            |     22 |           2300 |
| 25%                |     37 |           4400 |
| Median             |     50 |           6950 |
| 75%                |     63 |           9400 |
| Maximum            |     78 |          14200 |

### Interpretation

The average patient age is approximately **50.1 years**.

The average billing amount is approximately **7,249.00**.

Billing amounts vary substantially across patients, with values ranging from **2,300 to 14,200** in the dataset.

---

# 🧹 6️⃣ Check Missing Values

Missing values are checked using:

```python
df.isnull().sum()
```

The current dataset contains:

```text
Patient_ID           0
Gender               0
Age                  0
Medical_Condition    0
Admission_Date       0
Admission_Type       0
Medical_Code        0
Billing_Amount       0
Discharge_Date       0
```

Therefore, **no missing values are present in the original dataset**.

---

# 7️⃣ Handle Missing Categorical Values

Even though the dataset currently contains no missing categorical values, the project includes a preprocessing step to safely handle them.

```python
for column in df.select_dtypes(include='object').columns:
    df[column] = df[column].fillna('Unknown')

print("Missing values after filling:")
print(df.isnull().sum())
```

### Purpose

If a future version of the dataset contains missing text values, they will be replaced with:

```text
Unknown
```

This prevents missing categorical values from causing problems during grouping and analysis.

---

# 🧾 8️⃣ Medical Code Cleaning

The `Medical_Code` column contains codes such as:

```text
ICD-10-I10
ICD-10-J18
ICD-10-E11
ICD-10-J45
ICD-10-S52
```

Missing values can be checked using:

```python
df['Medical_Code'].isnull()
```

The current dataset contains no missing medical codes.

### Standardization

For a robust preprocessing pipeline, medical codes can also be standardized using:

```python
df["Medical_Code"] = (
    df["Medical_Code"]
    .astype(str)
    .str.strip()
    .str.upper()
)
```

This ensures that codes are consistently represented.

For example:

```text
icd-10-i10
ICD-10-I10
 ICD-10-I10
```

can be standardized to:

```text
ICD-10-I10
```

---

# 📅 9️⃣ Standardize Date Attributes

The admission and discharge dates are initially stored as strings.

They are converted using:

```python
df['Admission_Date'] = pd.to_datetime(
    df['Admission_Date']
)

df['Discharge_Date'] = pd.to_datetime(
    df['Discharge_Date']
)
```

The resulting data types are:

```text
datetime64[ns]
datetime64[ns]
```

### Why Date Standardization Is Important

Proper datetime values allow us to:

* Calculate hospital stay duration
* Sort patients chronologically
* Group records by month/year
* Perform time-series analysis
* Analyze admission patterns

---

# 🚨 1️⃣0️⃣ Admission Type Analysis

The dataset contains three admission categories:

```python
print(df['Admission_Type'].value_counts())
```

### Original Distribution

```text
Routine      196
Emergency    188
Urgent       116
```

### Percentage Distribution

The percentages can be calculated using:

```python
df["Admission_Type"].value_counts(normalize=True) * 100
```

Based on 500 records:

| Admission Type | Patients | Approx. Percentage |
| -------------- | -------: | -----------------: |
| Routine        |      196 |              39.2% |
| Emergency      |      188 |              37.6% |
| Urgent         |      116 |              23.2% |
| **Total**      |  **500** |           **100%** |

---

# ⚠️ 1️⃣1️⃣ Standardize Admission Type

The project converts admission-type text to lowercase:

```python
df['Admission_Type'] = (
    df['Admission_Type']
    .str.lower()
)
```

This converts:

```text
Emergency
Urgent
Routine
```

into:

```text
emergency
urgent
routine
```

### Why Standardize?

Standardization prevents different capitalization from being treated as separate categories.

For example:

```text
Emergency
emergency
EMERGENCY
```

should represent the same category.

---

# 🏥 1️⃣2️⃣ Admission Urgency Categories

The dataset currently contains:

```text
Emergency
Urgent
Routine
```

The project objective describes the third category as **Elective**. Since the actual dataset uses **Routine**, the analysis should preserve the source value unless there is a documented definition that equates Routine with Elective.

For reporting purposes:

| Dataset Value | Meaning in Dataset  |
| ------------- | ------------------- |
| Emergency     | Emergency admission |
| Urgent        | Urgent admission    |
| Routine       | Routine admission   |

If the dataset documentation confirms that `Routine` means `Elective`, it can be renamed:

```python
df["Admission_Type"] = df["Admission_Type"].replace(
    {"routine": "elective"}
)
```

This should only be done when the terminology is supported by the dataset definition.

---

# 🛏️ 1️⃣3️⃣ Calculate Hospital Stay

Hospital stay is calculated from the admission and discharge dates.

### Formula

```text
Hospital Stay Days =
Discharge Date - Admission Date
```

Python implementation:

```python
df['Hospital_Stay_Days'] = (
    df['Discharge_Date']
    - df['Admission_Date']
).dt.days
```

This creates a new column:

```text
Hospital_Stay_Days
```

---

# 📊 1️⃣4️⃣ Hospital Stay Statistics

The descriptive statistics are calculated using:

```python
df['Hospital_Stay_Days'].describe()
```

### Results

| Statistic          | Hospital Stay |
| ------------------ | ------------: |
| Count              |           500 |
| Mean               |    2.744 days |
| Standard Deviation |    1.177 days |
| Minimum            |         1 day |
| 25%                |        2 days |
| Median             |        2 days |
| 75%                |        4 days |
| Maximum            |       10 days |

### Interpretation

The average hospital stay in the dataset is approximately:

```text
2.74 days
```

The median stay is:

```text
2 days
```

The longest recorded stay is:

```text
10 days
```

---

# 💰 1️⃣5️⃣ Billing Amount Analysis

The billing amount is analyzed using:

```python
print(df['Billing_Amount'].describe())
```

### Results

| Statistic          | Billing Amount |
| ------------------ | -------------: |
| Count              |            500 |
| Mean               |      7,249.001 |
| Standard Deviation |      3,198.969 |
| Minimum            |          2,300 |
| 25%                |          4,400 |
| Median             |          6,950 |
| 75%                |          9,400 |
| Maximum            |         14,200 |

### Interpretation

The average billing amount is approximately:

```text
7,249.00
```

The median billing amount is:

```text
6,950.00
```

The observed billing amounts range from:

```text
2,300 to 14,200
```

The standard deviation of approximately **3,198.97** indicates noticeable variation in billing amounts across the patient records.

---

# 👥 1️⃣6️⃣ Demographic Segmentation by Medical Condition

Patient demographics can be segmented according to medical condition.

For example:

```python
condition_summary = df.groupby(
    "Medical_Condition"
).agg(
    Patient_Count=("Patient_ID", "count"),
    Average_Age=("Age", "mean"),
    Average_Billing=("Billing_Amount", "mean"),
    Average_Stay=("Hospital_Stay_Days", "mean")
)

print(condition_summary)
```

This creates a summary containing:

* Number of patients
* Average patient age
* Average billing amount
* Average hospital stay

for each medical condition.

---

# 🩺 1️⃣7️⃣ Medical Condition Analysis

The number of patients in each medical condition can be calculated using:

```python
condition_counts = (
    df["Medical_Condition"]
    .value_counts()
)

print(condition_counts)
```

This helps identify how frequently each medical condition appears in the dataset.

---

# 👨‍⚕️ 1️⃣8️⃣ Gender Segmentation by Medical Condition

Gender distribution can be examined using:

```python
gender_condition = pd.crosstab(
    df["Medical_Condition"],
    df["Gender"]
)

print(gender_condition)
```

This produces a table showing the number of male and female patients within each medical condition.

Example structure:

```text
Gender             Female    Male
Medical Condition
Asthma
COPD
Diabetes Type 2
Fracture
Heart Attack
Hypertension
Pneumonia
Stroke
```

---

# 📊 1️⃣9️⃣ Age Segmentation by Medical Condition

Average age by condition can be calculated using:

```python
age_by_condition = (
    df.groupby("Medical_Condition")["Age"]
    .agg(["count", "mean", "min", "max"])
)

print(age_by_condition)
```

This helps compare the age distribution of patients across medical conditions.

---

# 💳 2️⃣0️⃣ Billing by Medical Condition

Average billing amount for each condition can be calculated using:

```python
billing_by_condition = (
    df.groupby("Medical_Condition")["Billing_Amount"]
    .agg(["count", "mean", "median", "min", "max"])
)

print(billing_by_condition)
```

This allows the project to examine how billing amounts vary between medical conditions.

---

# 🛏️ 2️⃣1️⃣ Hospital Stay by Medical Condition

Average hospital stay can be compared using:

```python
stay_by_condition = (
    df.groupby("Medical_Condition")["Hospital_Stay_Days"]
    .agg(["count", "mean", "median", "min", "max"])
)

print(stay_by_condition)
```

This provides a condition-level summary of hospitalization duration.

---

# 📊 2️⃣2️⃣ Admission Type Visualization

A bar chart can be used to visualize admission categories.

```python
plt.figure(figsize=(8, 5))

sns.countplot(
    data=df,
    x="Admission_Type"
)

plt.title("Distribution of Admission Types")
plt.xlabel("Admission Type")
plt.ylabel("Number of Patients")

plt.show()
```

This makes it easier to compare emergency, urgent, and routine admissions.

---

# 📊 2️⃣3️⃣ Medical Condition Visualization

The distribution of medical conditions can be visualized using:

```python
plt.figure(figsize=(10, 6))

sns.countplot(
    data=df,
    y="Medical_Condition"
)

plt.title("Patients by Medical Condition")
plt.xlabel("Number of Patients")
plt.ylabel("Medical Condition")

plt.show()
```

---

# 💰 2️⃣4️⃣ Billing Distribution

The distribution of billing amounts can be visualized using:

```python
plt.figure(figsize=(10, 6))

sns.histplot(
    data=df,
    x="Billing_Amount",
    bins=30,
    kde=True
)

plt.title("Distribution of Billing Amounts")
plt.xlabel("Billing Amount")
plt.ylabel("Number of Patients")

plt.show()
```

This provides a visual understanding of the spread of healthcare billing amounts.

---

# 🛏️ 2️⃣5️⃣ Hospital Stay Distribution

Hospital stay distribution can be visualized using:

```python
plt.figure(figsize=(8, 5))

sns.histplot(
    data=df,
    x="Hospital_Stay_Days",
    bins=10,
    kde=True
)

plt.title("Distribution of Hospital Stay Duration")
plt.xlabel("Hospital Stay (Days)")
plt.ylabel("Number of Patients")

plt.show()
```

---

# 📋 2️⃣6️⃣ Complete Summary Table

A consolidated summary can be generated using:

```python
summary = df.groupby(
    "Medical_Condition"
).agg(
    Patient_Count=("Patient_ID", "count"),
    Average_Age=("Age", "mean"),
    Average_Billing=("Billing_Amount", "mean"),
    Median_Billing=("Billing_Amount", "median"),
    Average_Stay=("Hospital_Stay_Days", "mean"),
    Median_Stay=("Hospital_Stay_Days", "median")
)

print(summary)
```

The resulting table provides a comprehensive view of patient demographics and healthcare utilization by medical condition.

---

# 🔬 2️⃣7️⃣ Key Statistical Findings

Based on the provided 500-record dataset:

### Patient Age

```text
Average Age       : 50.106 years
Median Age        : 50 years
Minimum Age       : 22 years
Maximum Age       : 78 years
```

### Billing

```text
Average Billing   : 7,249.001
Median Billing    : 6,950
Minimum Billing   : 2,300
Maximum Billing   : 14,200
```

### Hospital Stay

```text
Average Stay      : 2.744 days
Median Stay       : 2 days
Minimum Stay      : 1 day
Maximum Stay      : 10 days
```

### Admission Type

```text
Routine            : 196 patients
Emergency          : 188 patients
Urgent             : 116 patients
```

---

# 💡 2️⃣8️⃣ Healthcare Insights

The dataset provides several descriptive insights.

### 1. Patient Demographics

The dataset contains 500 patients with ages ranging from 22 to 78 years. The mean age is approximately 50 years.

### 2. Admission Patterns

Routine admissions account for 196 records, emergency admissions for 188 records, and urgent admissions for 116 records.

### 3. Billing Variation

Billing amounts vary considerably across patients, ranging from 2,300 to 14,200.

### 4. Hospitalization Duration

The average hospital stay is approximately 2.74 days, with a median of 2 days.

### 5. Condition-Level Analysis

Grouping patients by medical condition enables comparison of:

* Patient counts
* Age
* Billing amounts
* Hospital stay duration
* Gender distribution

These comparisons can help describe patterns in the dataset without assuming that the observed differences represent causal relationships.

---

# 🧹 2️⃣9️⃣ Data Quality Checks

The project performs several data-quality operations:

```text
✔ Missing-value detection
✔ Missing categorical-value handling
✔ Medical-code validation
✔ Medical-code standardization
✔ Date conversion
✔ Admission-type standardization
✔ Hospital-stay calculation
✔ Numerical summary statistics
```

---

# 🚀 3️⃣0️⃣ Future Enhancements

The project can be extended with:

### 1. Admission Trend Analysis

Analyze admissions by:

* Day
* Week
* Month
* Year

### 2. Condition-Based Billing Analysis

Compare average billing amounts across medical conditions.

### 3. Hospital Stay Analysis

Investigate which conditions are associated with longer recorded stays in this dataset.

### 4. Demographic Visualization

Create charts for:

* Age groups
* Gender distribution
* Condition distribution
* Admission type by gender
* Condition by gender

### 5. Correlation Analysis

Analyze relationships between:

* Age
* Billing amount
* Hospital stay

Example:

```python
correlation = df[
    [
        "Age",
        "Billing_Amount",
        "Hospital_Stay_Days"
    ]
].corr()

sns.heatmap(
    correlation,
    annot=True
)

plt.title(
    "Healthcare Numerical Features Correlation"
)

plt.show()
```

### 6. Interactive Dashboard

The project could be converted into an interactive dashboard using:

* Streamlit
* Plotly
* Dash

Possible dashboard components include:

```text
Total Patients
Average Age
Average Billing
Average Hospital Stay

Admission Type Distribution
Medical Condition Distribution
Billing by Condition
Hospital Stay by Condition
Gender Distribution
```

---

# 🧪 3️⃣1️⃣ How to Run the Project

### Step 1 – Open Google Colab

Create a new Google Colab notebook.

### Step 2 – Upload the Dataset

Place:

```text
healthcare_dataset.csv
```

inside Google Drive.

### Step 3 – Update the File Path

```python
df = pd.read_csv(
    "/content/drive/MyDrive/Colab Notebooks/healthcare_dataset.csv"
)
```

Change the path if the file is stored elsewhere.

### Step 4 – Run the Notebook

Execute the cells in sequence:

```text
Load Data
   ↓
Inspect Data
   ↓
Check Missing Values
   ↓
Clean Medical Codes
   ↓
Convert Dates
   ↓
Standardize Admission Types
   ↓
Calculate Hospital Stay
   ↓
Analyze Billing
   ↓
Analyze Admissions
   ↓
Segment Demographics
   ↓
Generate Visualizations
```

---

# 🎓 3️⃣2️⃣ Learning Outcomes

Through this project, the following concepts are demonstrated:

* Python programming
* Pandas DataFrames
* CSV data processing
* Healthcare data preprocessing
* Missing-value handling
* Data-type conversion
* Datetime processing
* String standardization
* Medical-code cleaning
* GroupBy operations
* Cross-tabulation
* Descriptive statistics
* Patient demographic analysis
* Billing analysis
* Hospital stay analysis
* Data visualization
* Exploratory Data Analysis

---

# 📌 3️⃣3️⃣ Conclusion

This project demonstrates a complete workflow for **cleaning and exploring healthcare data using Python**.

The 500-patient dataset is inspected for missing values and data-quality issues, medical codes are standardized, date attributes are converted into appropriate datetime formats, admission categories are analyzed, and hospital stay duration is calculated from admission and discharge dates.

The statistical analysis shows an average patient age of approximately **50.1 years**, an average billing amount of approximately **7,249**, and an average hospital stay of approximately **2.74 days**.

The dataset can also be segmented by medical condition to examine differences in patient counts, demographics, billing amounts, and hospital stay duration.

Overall, the project provides a foundation for further **healthcare analytics, visualization, dashboard development, and predictive modeling**.

---

# 👩‍💻 Author

**C. Keerthana**
---

# ⭐ Project Highlights

```text
🏥 Healthcare Dataset Analysis
🧹 Data Cleaning
🔍 Missing Value Handling
🧾 Medical Code Standardization
📅 Date Standardization
🚨 Admission Type Analysis
💰 Billing Analysis
🛏️ Hospital Stay Analysis
👥 Demographic Segmentation
📊 Statistical Analysis
📈 Data Visualization
🐍 Python & Pandas
☁️ Google Colab
```

---

# 📜 License

This project is intended for **educational and learning purposes**.
