
# Week 10: House Price Visualization, Spatial Analytics & Real-Estate Insights

## 1. Project Overview

This project analyses the preprocessed King County House Sales Dataset using Python. It explores the relationship between house prices, living area, property grade, condition, waterfront access, age, renovation status, and geographical location.

Data visualization techniques are used to identify price patterns, compare property characteristics, and generate evidence-based real-estate insights.

## 2. Objectives

- Analyse living area and house price relationships.
- Compare prices across property grades and conditions.
- Evaluate waterfront and non-waterfront property prices.
- Visualize geographical house-price distributions.
- Study property age and renovation status.
- Compare prices by bedrooms and bathrooms.
- Analyse price per square foot.
- Generate summary statistics and investment insights.

## 3. Dataset Description

**Dataset:** King County House Sales Dataset (Preprocessed)

**Source:** Kaggle

The dataset should be preprocessed using the Week 9 workflow.

Important columns include:

- price
- sqft_living
- sqft_lot
- bedrooms
- bathrooms
- grade
- condition
- waterfront
- lat
- long
- sale_year
- property_age
- is_renovated
- price_per_sqft_living
- price_per_sqft_lot

The program requires `price` and `sqft_living`. Other analyses are performed when their required columns are available.

## 4. Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn

## 5. Project Structure

```text
week10_house_price_visualization/
│
├── house_price_analysis.py
├── README.md
├── requirements.txt
├── data/
│   └── KingCounty_Preprocessed.csv
└── outputs/
```

The output folder is populated automatically when the program runs.

## 6. Installation

Install Python 3.9 or later.

Open the terminal in the project directory and execute:

```bash
pip install -r requirements.txt
```

## 7. Dataset Setup

Place the preprocessed Week 9 CSV file inside the `data` folder.

Use this filename:

```text
Kc_house_data_Preprocessed.csv
```

If your file has another name, the script searches for a CSV file in the data folder. You can also change `DATA_PATH` in the Python script.

## 8. Execution

Run the following command:

```bash
python house_price_analysis.py
```

The program loads the dataset, prepares the data, generates visualizations, and creates reports in the `outputs` folder.

## 9. Visualizations Generated

1. Living Area vs House Price - Linear Trend
<img width="569" height="455" alt="image" src="https://github.com/user-attachments/assets/0622505c-73d7-463a-9d3b-865cb824b4d6" />

2. Living Area vs House Price - Nonlinear Trend
<img width="569" height="455" alt="image" src="https://github.com/user-attachments/assets/72938672-7f86-458c-9f3f-80b13eabee18" />

3. House Price Distribution by Grade
<img width="586" height="455" alt="image" src="https://github.com/user-attachments/assets/dc767293-f7b8-40f9-88f4-370d5dd07318" />

4. House Price Distribution by Condition
<img width="988" height="547" alt="image" src="https://github.com/user-attachments/assets/f57d2424-ebd1-4723-bd58-619143819569" />

5. Waterfront vs Non-waterfront Prices
<img width="755" height="547" alt="image" src="https://github.com/user-attachments/assets/c746dba2-f7e3-4e92-bc05-95f131352611" />

6. Geographic Distribution of House Prices
<img width="558" height="455" alt="image" src="https://github.com/user-attachments/assets/3c3ed26e-22ff-4592-a3b9-e44240cab1ad" />

7. Property Age vs House Price
<img width="564" height="455" alt="image" src="https://github.com/user-attachments/assets/87207043-b65d-4c2d-aa7c-8f2f27ac50ae" />

8. Average Price by Renovation Status
<img width="721" height="470" alt="image" src="https://github.com/user-attachments/assets/d5a0aa51-e413-44ed-89ef-69288185566e" />

9. Average Unit Price by Property Grade
<img width="850" height="547" alt="image" src="https://github.com/user-attachments/assets/c27e2082-98e6-4514-ad59-87146b19608d" />

10. Living Area vs Price per Square Foot
<img width="586" height="455" alt="image" src="https://github.com/user-attachments/assets/d25f6db5-2747-45f9-a82f-69b5a66caaae" />

11. Average House Price by Bedroom Count
<img width="876" height="547" alt="image" src="https://github.com/user-attachments/assets/c96a2a9d-17b2-4788-9313-7a13a6d7554e" />

12. Average House Price by Bathroom Count
<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/9f519ed2-1646-4db5-982a-3379adc2cf09" />


## 10. Generated Reports

- `summary_statistics.csv` - Descriptive statistics for numeric columns.
- `price_summary_by_grade.csv` - Price statistics by property grade.
- `price_summary_by_condition.csv` - Price statistics by condition.
- `price_summary_by_waterfront.csv` - Price statistics by waterfront status.
- `average_price_by_renovation.csv` - Average price by renovation status.
- `unit_price_by_grade.csv` - Average price per square foot by grade.
- `high_value_properties.csv` - Properties in the top 10% of sale prices with available coordinates.
- `real_estate_insights.txt` - Automatically generated statistical findings and limitations.

## 11. Expected Insights

The analysis helps investigate whether:

- Larger living areas tend to be associated with higher sale prices.
- Higher property grades are associated with higher median prices.
- House prices differ across condition categories.
- Waterfront properties have higher observed prices.
- High-priced properties form geographical concentrations.
- Renovation status and property age are associated with valuation.
- Price per square foot varies across property grades and property sizes.

Actual conclusions must be based on the generated results.

## 12. Limitations

- Correlation does not prove causation.
- Extreme values may influence average prices and trend lines.
- Waterfront comparisons do not control for property size, grade, or location.
- Geographic scatter plots identify visible patterns but do not constitute formal spatial clustering.
- The analysis depends on the quality and completeness of the input dataset.

## 13. Conclusion

This project applies Python-based visual analytics to explore house-price variation in King County. It compares property characteristics, visualizes geographical price patterns, and produces statistical summaries to support real-estate market evaluation.

The results can help identify factors associated with property valuation and areas that warrant further investigation. Additional market research and due diligence are necessary before making investment decisions.
