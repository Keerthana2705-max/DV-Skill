# Week-7  Student Performance Data Analysis

## 📌 Project Overview

This project focuses on analyzing student performance data using **Python, Pandas, and NumPy**. The dataset contains information about students' demographic and educational backgrounds along with their scores in **Math, Reading, and Writing**.

The project performs data cleaning, statistical analysis, feature engineering, and outlier detection to understand student performance patterns.

---

## 🎯 Objectives

* Clean and standardize categorical features.
* Calculate statistical measures for subject scores.
* Create **Total Marks** and **Percentage** features.
* Detect extreme performance outliers using the **IQR method**.
* Generate a cleaned dataset for further analysis.

---

## 📂 Dataset

The project uses the **StudentsPerformance.csv** dataset.

### Dataset Features

| Feature                     | Description                                    |
| --------------------------- | ---------------------------------------------- |
| Gender                      | Student's gender                               |
| Race/Ethnicity              | Student's race/ethnicity group                 |
| Parental Level of Education | Parent's highest education level               |
| Lunch                       | Type of lunch received                         |
| Test Preparation Course     | Whether the student completed test preparation |
| Math Score                  | Mathematics score                              |
| Reading Score               | Reading score                                  |
| Writing Score               | Writing score                                  |

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Jupyter Notebook / Google Colab**

---

## 🔄 Project Workflow

```text
Load Dataset
     ↓
Clean Categorical Features
     ↓
Analyze Subject Scores
     ↓
Calculate Statistical Measures
     ↓
Create Total Marks
     ↓
Calculate Percentage
     ↓
Detect Performance Outliers
     ↓
Save Cleaned Dataset
```

---

## 🧹 1. Categorical Data Cleaning

The following categorical features are cleaned:

* Gender
* Race/Ethnicity
* Parental Level of Education
* Lunch
* Test Preparation Course

Extra spaces are removed and categorical values are standardized into lowercase format.

Example:

```text
"Male " → "male"
" Female" → "female"
```

---

## 📊 2. Statistical Analysis

Statistical measures are calculated for:

* Math Score
* Reading Score
* Writing Score

The following measures are included:

### Mean

Represents the average score.

### Median

Represents the middle value of the scores.

### Standard Deviation

Measures how much the scores vary from the average.

### Quartiles

The following quartiles are calculated:

* Q1 – 25th percentile
* Q2 – 50th percentile / Median
* Q3 – 75th percentile

---

## 🧮 3. Feature Engineering

Two new features are created.

### Total Marks

The three subject scores are added together.

```text
Total Marks = Math + Reading + Writing
```

The maximum possible total is **300**.

### Percentage

Student percentage is calculated as:

```text
Percentage = (Total Marks / 300) × 100
```

Example:

```text
Math = 80
Reading = 85
Writing = 90

Total Marks = 255

Percentage = 85%
```

---

## 🚨 4. Outlier Detection

Extreme performance values are detected using the **Interquartile Range (IQR)** method.

### Formula

```text
IQR = Q3 - Q1
```

Lower boundary:

```text
Q1 - 1.5 × IQR
```

Upper boundary:

```text
Q3 + 1.5 × IQR
```

Values outside these boundaries are considered potential outliers.

Outliers are analyzed separately for:

* Math Score
* Reading Score
* Writing Score

---

## 📁 Project Structure

```text
Student-Performance-Analysis/
│
├── StudentsPerformance.csv
├── StudentsPerformance_Cleaned.csv
├── student_performance_analysis.py
└── README.md
```

---

## ▶️ How to Run

### 1. Install required libraries

```bash
pip install pandas numpy
```

### 2. Place the dataset in the project folder

Make sure the following file is available:

```text
StudentsPerformance.csv
```

### 3. Run the Python program

```bash
python student_performance_analysis.py
```

If using **Google Colab**, upload the CSV file and update the file path accordingly.

---

## 📈 Output

The program generates:

* Cleaned categorical data
* Mean scores
* Median scores
* Standard deviation
* Q1, Q2, and Q3
* Total marks
* Percentage performance
* Outlier details
* Cleaned CSV dataset

The final cleaned dataset is saved as:

```text
StudentsPerformance_Cleaned.csv
```

---

## 🔍 Key Insights

The analysis can be used to identify:

* Overall student performance levels.
* Differences in performance across subjects.
* Variation in student scores.
* Students with unusually high or low subject scores.
* Overall percentage performance.
* Potential areas requiring further academic analysis.

---

## 🚀 Future Enhancements

The project can be extended by adding:

* Data visualization using Matplotlib and Seaborn.
* Subject-wise performance comparison.
* Gender-based performance analysis.
* Test-preparation impact analysis.
* Correlation analysis between subjects.
* Performance prediction using Machine Learning.
* Interactive dashboards using Power BI or Plotly.

---

## 👩‍💻 Author

**C. Keerthana**

---

## ⭐ Conclusion

This project demonstrates a basic **Exploratory Data Analysis (EDA)** workflow using student performance data. It combines data cleaning, descriptive statistics, feature engineering, and outlier detection to transform raw student data into useful analytical information.
