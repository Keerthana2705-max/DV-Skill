# 📊 Superstore Sales Data Analysis – Week 2
## 📌 Project Overview
This project is part of my **Week 2 Data Analysis learning journey**, where I continued working with the **Superstore Sales Dataset**.
In Week 1, I focused on **data loading, cleaning, basic exploration, and statistical analysis**. In Week 2, I extended the project by adding **data visualization and exploratory analysis** to understand sales, profit, discounts, delivery time, and relationships between numerical variables.

The main objective of this project is to transform raw sales data into meaningful insights using **Python, Pandas, Matplotlib, and Seaborn**.

---

## 🎯 Objectives

The key objectives of this project are:

* Load and explore the Superstore dataset
* Understand the structure and characteristics of the data
* Convert date columns into proper datetime format
* Calculate delivery duration
* Check for missing values
* Analyze sales and profit across different categories
* Visualize sales distributions
* Study profit variations
* Analyze the relationship between discount and profit
* Identify correlations between numerical variables
* Improve understanding of **Exploratory Data Analysis (EDA)** and data visualization

---

## 🛠️ Technologies & Libraries Used

* 🐍 **Python**
* 🐼 **Pandas** – Data manipulation and analysis
* 🔢 **NumPy** – Numerical operations
* 📊 **Matplotlib** – Data visualization
* 📈 **Seaborn** – Statistical data visualization
* ☁️ **Google Colab** – Development environment
* 📁 **CSV** – Dataset format

---

## 📂 Dataset

The project uses the **Superstore Sales Dataset**, which contains information about orders, customers, products, sales, discounts, and profits.

### Dataset Information

* **Rows:** 10,194
* **Columns:** 21
* **Categories:** Furniture, Office Supplies, Technology

### Important Columns

| Column          | Description                     |
| --------------- | ------------------------------- |
| `Order ID`      | Unique identifier for an order  |
| `Order Date`    | Date when the order was placed  |
| `Ship Date`     | Date when the order was shipped |
| `Ship Mode`     | Shipping method used            |
| `Customer Name` | Name of the customer            |
| `Segment`       | Customer segment                |
| `Region`        | Sales region                    |
| `Category`      | Product category                |
| `Sub-Category`  | Product sub-category            |
| `Product Name`  | Name of the product             |
| `Sales`         | Sales amount                    |
| `Quantity`      | Number of products purchased    |
| `Discount`      | Discount applied                |
| `Profit`        | Profit generated                |

---

# 🔎 Data Analysis Process

## 1️⃣ Importing Required Libraries

The project starts by importing the required Python libraries:

* Pandas
* NumPy
* Matplotlib
* Seaborn

These libraries are used for data manipulation, numerical analysis, and visualization.

---

## 2️⃣ Loading the Dataset

The Superstore dataset is loaded using Pandas:

```python
df = pd.read_csv("samplesuperstore.csv")
```

The first few records are displayed using:

```python
df.head()
```

This helps understand the structure and values present in the dataset.

---

## 3️⃣ Understanding the Dataset

The following functions were used for initial exploration:

```python
df.info()
df.describe()
```

### `df.info()`

Provides information about:

* Number of rows
* Column names
* Data types
* Non-null values

### `df.describe()`

Provides statistical information such as:

* Mean
* Standard deviation
* Minimum
* Maximum
* Quartiles

For example, the dataset contains numerical variables such as **Sales, Profit, Quantity, and Discount**.

---

## 4️⃣ Date Conversion

The `Order Date` and `Ship Date` columns were converted into datetime format:

```python
df['Order Date'] = pd.to_datetime(df['Order Date'])
df['Ship Date'] = pd.to_datetime(df['Ship Date'])
```

This allows date-based calculations and analysis.

---

## 5️⃣ Calculating Delivery Days

A new column called **Delivery Days** was created to calculate the number of days between order placement and shipment.

```python
df['Delivery Days'] = (
    df['Ship Date'] - df['Order Date']
).dt.days
```

This provides an additional metric that can be used to understand shipping performance.

---

## 6️⃣ Checking Product Categories

The unique product categories were identified using:

```python
df['Category'].unique()
```

The dataset contains three major categories:

* 🪑 Furniture
* 📎 Office Supplies
* 💻 Technology

---

## 7️⃣ Checking Missing Values

Missing values were checked using:

```python
df.isnull().sum()
```

This step is important because missing values can affect the accuracy of analysis and visualizations.

---

# 📊 Data Visualization

## 8️⃣ Sales by Category

Total sales were calculated for each category:

```python
category_sales = df.groupby('Category')['Sales'].sum()
```

A bar chart was then created to visualize category-wise sales.

### Purpose

This visualization helps compare the total sales generated by different product categories.
<img width="721" height="560" alt="image" src="https://github.com/user-attachments/assets/e8ab9620-cb7f-418b-ab9e-f36fa76616b5" />


---

## 9️⃣ Sales Distribution

A histogram was used to understand the distribution of sales values:

```python
sns.histplot(df['Sales'], bins=30)
```

### Purpose

The histogram helps identify:

* Distribution of sales values
* Frequently occurring sales ranges
* Presence of high-value transactions
* Possible skewness in the data
<img width="704" height="470" alt="image" src="https://github.com/user-attachments/assets/dbf0cf96-43e9-4bdc-bf09-e24f37a8e11c" />

---
One of the main improvements in **Week 2** was adding different types of visualizations to understand the dataset more effectively.

## 🔟 Profit by Category

A bar plot was created to compare profit across product categories.

```python
sns.barplot(
    data=df,
    x="Category",
    y="Profit"
)
```

### Purpose

This visualization helps determine which categories contribute more to profitability.
<img width="571" height="455" alt="image" src="https://github.com/user-attachments/assets/556d82c4-3e2f-470c-b58a-bb9f1e496f29" />

---

## 1️⃣1️⃣ Sales Distribution by Category

Another bar plot was created to compare sales across categories.

```python
sns.barplot(
    data=df,
    x="Category",
    y="Sales"
)
```

This makes it easier to compare category-level sales performance.
<img width="571" height="455" alt="image" src="https://github.com/user-attachments/assets/2a716273-f37d-437a-9ff0-81bccfc55798" />

---

## 1️⃣2️⃣ Profit Distribution

A box plot was used to analyze the overall distribution of profit:

```python
sns.boxplot(data=df, y="Profit")
```

### Purpose

The box plot helps identify:

* Median profit
* Spread of profit values
* Variability
* Potential outliers
<img width="592" height="416" alt="image" src="https://github.com/user-attachments/assets/902ea160-e7a6-483b-a91c-626f6f8d555e" />

---

## 1️⃣3️⃣ Profit Variation Across Categories

Profit variation between categories was analyzed using:

```python
sns.boxplot(
    data=df,
    x="Category",
    y="Profit"
)
```

This visualization provides a more detailed understanding of how profit varies within each category.
<img width="592" height="455" alt="image" src="https://github.com/user-attachments/assets/47984ab1-e8dc-47d8-b664-3cc983017370" />

---

## 1️⃣4️⃣ Discount vs Profit

A scatter plot was used to investigate the relationship between discount and profit:

```python
sns.scatterplot(
    data=df,
    x="Discount",
    y="Profit"
)
```

### Purpose

This visualization helps investigate whether changes in discount levels are associated with changes in profit.

It can also reveal:

* Negative-profit transactions
* High-discount orders
* Possible relationships between discount and profitability
* Outliers
<img width="592" height="455" alt="image" src="https://github.com/user-attachments/assets/a880f5cc-90e1-4c86-bbfa-934ff594df3d" />

---

## 1️⃣5️⃣ Correlation Heatmap

A correlation matrix was created using numerical columns:

```python
numeric_df = df.select_dtypes(include="number")
corr = numeric_df.corr()
```

The correlation matrix was visualized using a heatmap:

```python
sns.heatmap(corr, annot=True)
```

### Purpose

The correlation heatmap helps understand relationships between numerical variables such as:

* Sales
* Quantity
* Discount
* Profit
* Delivery Days
* Other numerical fields

A correlation value close to **+1** indicates a strong positive relationship, while a value close to **-1** indicates a strong negative relationship.
<img width="609" height="518" alt="image" src="https://github.com/user-attachments/assets/411afe4b-1229-4e14-8bcc-4cd8d42d17c2" />

---

# 💡 Key Insights

Through the analysis and visualizations, the following areas were explored:

### 📌 Category Performance

Sales and profit were compared across **Furniture, Office Supplies, and Technology** categories.

### 📌 Sales Distribution

The sales histogram shows that transaction values are not evenly distributed, with some orders having significantly higher sales values than typical transactions.

### 📌 Profit Variation

Profit values show considerable variation, including both profitable and loss-making transactions.

### 📌 Discount & Profit

The scatter plot provides a visual way to investigate how discount levels are associated with profit and identify transactions where high discounts may correspond with lower profitability.

### 📌 Outlier Detection

Box plots help identify unusual profit values that may require further investigation.

### 📌 Correlation Analysis

The correlation heatmap provides an overall view of relationships between numerical variables and helps identify potentially important variables for further analysis.

---

# 📈 Visualizations Included

The project includes the following visualizations:

| Visualization          | Purpose                              |
| ---------------------- | ------------------------------------ |
| 📊 Sales by Category   | Compare category-wise sales          |
| 📊 Sales Distribution  | Understand sales distribution        |
| 📊 Profit by Category  | Compare category profitability       |
| 📊 Sales by Category   | Compare sales performance            |
| 📦 Profit Distribution | Analyze profit spread and outliers   |
| 📦 Profit by Category  | Compare profit variation             |
| 🔵 Discount vs Profit  | Analyze discount-profit relationship |
| 🔥 Correlation Heatmap | Identify numerical relationships     |

---
# 📚 What I Learned

Through this Week 2 project, I strengthened my understanding of:

* 🐼 Pandas DataFrame operations
* 🔍 Exploratory Data Analysis
* 🧹 Basic data preprocessing
* 📅 Datetime manipulation
* ➕ Creating calculated columns
* 📊 Bar charts
* 📈 Histograms
* 📦 Box plots
* 🔵 Scatter plots
* 🔥 Correlation heatmaps
* 📌 Identifying patterns and outliers
* 💡 Converting data into meaningful visual insights

Most importantly, I learned how **visualization can make patterns and relationships in data much easier to understand than looking at raw numbers alone.**

---

# 🔄 Week 1 → Week 2 Progress

### Week 1

* Dataset loading
* Data exploration
* Data cleaning
* Statistical analysis
* Basic understanding of the dataset

### Week 2

* Continued the Week 1 analysis
* Added deeper exploratory analysis
* Created multiple visualizations
* Analyzed sales and profit by category
* Studied profit variation and outliers
* Analyzed discount vs profit
* Created a correlation heatmap

This project represents my progress from **basic data exploration to visual storytelling with data**.

---
# 👩‍💻 Author

**C. Keerthana**
---
