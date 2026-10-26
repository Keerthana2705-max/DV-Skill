# Week-9 Housing Price Data Cleaning and Feature Engineering

## Project Overview
This project focuses on cleaning and transforming housing sales data to prepare it for effective data analysis and machine learning models. The dataset contains information about property prices, bedrooms, bathrooms, living area, lot size, construction year, renovation year, and sale dates.

## Objectives
- Inspect property features such as bedrooms, bathrooms, living area, grade, and year built.
- Extract temporal attributes from sale dates.
- Calculate property age and years since renovation.
- Compute price per square foot for living area and lot size.
- Identify extreme house-price values using box plots and statistical methods.

## Tasks Performed

### 1. Data Cleaning
- Checked for missing values.
- Handled invalid zero values in bedroom and bathroom counts.
- Filled missing room-count values using median values.
- Checked the dataset after cleaning.

### 2. Date Processing and Feature Engineering
- Converted sale dates into datetime format.
- Extracted the sale year.
- Calculated property age at the time of sale.
- Calculated years since renovation.
- Created an `is_renovated` feature to identify renovated properties.

### 3. Price per Square Foot Calculation
Calculated the following metrics:

- **Price per Square Foot (Living Area):** House price divided by living area.
- **Price per Square Foot (Lot Size):** House price divided by total lot size.
<img width="644" height="470" alt="image" src="https://github.com/user-attachments/assets/d4da42ef-b1e7-421e-a30f-61b427163dab" />

Zero area values were handled to avoid division-by-zero errors.

### 4. Outlier Detection
- Created box plots to visualize outliers in house prices.
- Visualized outliers in price per square foot.
- Used the Interquartile Range (IQR) method to calculate lower and upper bounds.
- Identified extreme house-price observations.
<img width="644" height="470" alt="image" src="https://github.com/user-attachments/assets/9ca0edb8-3ca1-49a6-b17c-07a12715d03b" />

### 5. Exploratory Data Inspection
- Examined dataset structure and column data types.
- Generated descriptive statistics.
- Displayed sample records to verify the transformed dataset.

## Technologies Used
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab

## Project Workflow
1. Load the housing dataset.
2. Inspect the dataset and identify missing values.
3. Clean invalid room-count values.
4. Process sale dates and create derived features.
5. Calculate price per square foot.
6. Visualize and identify outliers.
7. Review the cleaned and transformed dataset.

## How to Run the Project
1. Open Google Colab.
2. Upload the housing dataset or connect Google Drive.
3. Import the required Python libraries.
4. Load the dataset into a Pandas DataFrame named `df`.
5. Execute the data-cleaning and feature-engineering cells in sequence.
6. Review the outputs, statistics, and visualizations.

## Expected Outcomes
- A cleaner and more consistent dataset.
- Additional features related to property age and renovation.
- Price-per-square-foot metrics for property valuation.
- Visual identification of extreme house prices.
- A dataset better prepared for further analysis and predictive modeling.

## Conclusion
This project demonstrates essential data preprocessing, feature engineering, and outlier detection techniques using Python. These steps help improve data quality and prepare housing sales data for further exploratory analysis and house-price prediction.

**Note:** Outliers are identified but not automatically removed. Their treatment should depend on the analysis objective and whether the observations represent genuine property sales or data errors.
