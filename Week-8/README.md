#Week-8 STUDENT PERFORMANCE ANALYSIS 

## 1. Introduction

Student Performance Analysis is a data analysis project that studies students’ examination scores and identifies factors associated with their academic performance.

The project uses a student performance dataset containing students’ Mathematics, Reading and Writing scores along with demographic and educational information. The analysis focuses on understanding how different factors such as parental level of education, lunch type and test preparation course are related to students’ academic performance.

Data visualization and statistical analysis are used to identify patterns and relationships in the dataset. The results are presented using charts such as bar charts, box plots, scatter plots and correlation heatmaps.

---

## 2. Objective

The main objective of this project is to analyze student examination performance and identify important patterns in the dataset.

The objectives are:

* To understand the structure of the student performance dataset.
* To study Mathematics, Reading and Writing scores.
* To analyze the relationship between parental education and student performance.
* To compare student performance based on lunch type.
* To compare students who completed the test preparation course with those who did not.
* To analyze the relationship between different subject scores.
* To represent the analysis using suitable visualizations.
* To identify important factors related to students’ academic performance.

---

## 3. Dataset Description

The dataset used for this project is **StudentsPerformance_preprocessed.csv**.

The dataset contains information about **1,000 students** and includes academic scores along with demographic and educational attributes.

### Important Attributes

**Gender:**
Represents the gender of the student.

**Race/Ethnicity:**
Represents the group or category of the student.

**Parental Level of Education:**
Represents the educational qualification of the student's parent or parents.

**Lunch:**
Represents the type of lunch received by the student.

**Test Preparation Course:**
Indicates whether the student completed the test preparation course.

**Math Score:**
Represents the student's score in Mathematics.

**Reading Score:**
Represents the student's score in Reading.

**Writing Score:**
Represents the student's score in Writing.

**Total Score:**
Represents the combined score obtained in the subjects.

**Percentage:**
Represents the overall percentage based on the examination scores.

---

## 4. Tools and Technologies Used

The following tools and technologies were used for the project:

### Python

Python is used as the main programming language for data analysis.

### Pandas

Pandas is used for loading, organizing, grouping and analyzing the dataset.

### NumPy

NumPy is used for numerical operations and calculations.

### Matplotlib

Matplotlib is used to create different types of charts and graphs.

### Seaborn

Seaborn is used for statistical visualization and creating attractive analytical graphs.

### Google Colab

Google Colab is used as the development environment for running the analysis.

---

## 5. Data Understanding

The dataset was first examined to understand its structure and characteristics.

The rows, columns, data types and basic statistical information were checked. The column names were also examined to identify the variables required for the analysis.

The three main academic score columns used in the project are:

* Mathematics Score
* Reading Score
* Writing Score

The categorical columns such as gender, parental level of education, lunch and test preparation course were also examined to understand the different categories available in the dataset.

This step helps ensure that the dataset is properly understood before performing further analysis.

---

## 6. Average Score Analysis

An average score was calculated for each student using the Mathematics, Reading and Writing scores.

The average score provides a single value representing the student's overall performance across the three subjects.

Using the average score makes it easier to compare different groups of students based on their overall academic performance.

---

## 7. Analysis Based on Parental Level of Education

The first major analysis studies the relationship between parental level of education and students’ examination performance.

The average Mathematics, Reading and Writing scores are calculated for each parental education category.

A grouped bar chart is used to compare the average scores of the three subjects across different parental education groups.

### Purpose of the Analysis

This analysis helps to understand whether students with different parental education backgrounds show differences in academic performance.

The comparison also helps identify which parental education groups have relatively higher or lower average scores.

---

## 8. Analysis Based on Parental Education and Lunch Type

The second analysis examines student performance based on two factors:

* Parental Level of Education
* Lunch Type

Students are grouped according to their parental education and lunch category. Their average scores are then compared.

A grouped bar chart is used to represent the results.
<img width="989" height="590" alt="image" src="https://github.com/user-attachments/assets/72615117-6967-436a-80db-664a2ae8591f" />


### Purpose of the Analysis

This analysis provides a combined view of parental education and lunch type.

It helps identify how the average performance of students differs across various combinations of these two factors.

---

## 9. Analysis of Test Preparation Course

The third analysis compares students based on whether they completed the test preparation course.

Two groups are considered:

* Students who completed the test preparation course
* Students who did not complete the test preparation course

A box plot is used to display the distribution and variation of students' average scores.

### Result

Students who completed the test preparation course have an average score of approximately **72.67**.

Students who did not complete the test preparation course have an average score of approximately **65.04**.

This shows that students who completed the test preparation course performed better on average than students who did not complete the course.
<img width="587" height="445" alt="image" src="https://github.com/user-attachments/assets/1cceef30-cbc0-4061-aa1a-9fd3b81ca08a" />


### Interpretation

The result suggests that test preparation is positively associated with students' academic performance in this dataset.

However, this result shows an association and does not by itself prove that the preparation course is the only reason for the difference in performance.

---

## 10. Analysis of Mathematics and Reading Scores

A scatter plot is used to study the relationship between Mathematics and Reading scores.

Each point in the scatter plot represents a student's performance in the two subjects.
<img width="571" height="455" alt="image" src="https://github.com/user-attachments/assets/88b1eb2d-8555-494d-8d7c-1fc88678bc34" />


### Observation

The scatter plot shows a positive relationship between Mathematics and Reading scores.

In general, students who have higher Mathematics scores also tend to have higher Reading scores.

This indicates that students who perform well in one subject may also perform well in another subject.

---

## 11. Correlation Analysis

Correlation analysis is used to measure the strength and direction of the relationship between the three academic subjects.

The correlation value ranges from **-1 to +1**.

* A value close to **+1** indicates a strong positive relationship.
* A value close to **-1** indicates a strong negative relationship.
* A value close to **0** indicates a weak or no linear relationship.

### Correlation Results

**Mathematics and Reading:** 0.818

**Mathematics and Writing:** 0.803

**Reading and Writing:** 0.955

### Interpretation

Mathematics and Reading have a strong positive relationship.

Mathematics and Writing also have a strong positive relationship.

The strongest relationship is between Reading and Writing, with a correlation of approximately **0.955**.

This indicates that students who obtain higher Reading scores generally tend to obtain higher Writing scores as well.

---

## 12. Correlation Heatmap

A correlation heatmap is used to visually represent the relationships between Mathematics, Reading and Writing scores.

The heatmap uses different shades to represent the strength of the correlation between the subjects. The actual correlation values are also displayed inside the heatmap.

<img width="548" height="435" alt="image" src="https://github.com/user-attachments/assets/caa96390-2dd1-4d2b-8bdb-8a55e5153bcb" />

### Observation

The heatmap shows strong positive relationships between all three subjects.

The strongest relationship is between Reading and Writing.

The heatmap provides a simple way to understand the relationships between different academic scores at a glance.

---

## 13. Key Findings

The major findings of the project are:

1. Mathematics, Reading and Writing scores are strongly related to each other.

2. Students with higher Mathematics scores generally tend to have higher Reading scores.

3. Mathematics and Writing also show a strong positive relationship.

4. Reading and Writing have the strongest correlation, approximately **0.955**.

5. Students who completed the test preparation course have a higher average score than students who did not complete it.

6. Parental level of education can be used to compare differences in students’ average academic performance.

7. Lunch type provides another useful factor for comparing student performance.

8. Visualizations make it easier to identify patterns and differences in the dataset.

---

## 14. Overall Interpretation

The analysis shows that several factors can be examined to understand student performance.

Test preparation shows a noticeable relationship with overall performance, as students who completed the preparation course achieved a higher average score.

The subject-wise correlation analysis shows that academic performance is interconnected. In particular, Reading and Writing scores have a very strong positive relationship.

Parental education and lunch type also provide useful categories for comparing student performance.

Therefore, data analysis can help educational institutions identify patterns in student achievement and understand areas that may require further attention.

---

## 15. Conclusion

The Student Performance Analysis project demonstrates how data analysis can be used to understand educational data.

The project analyzed students' Mathematics, Reading and Writing scores and examined their relationship with selected demographic and educational factors.

The analysis found that students who completed the test preparation course achieved a higher average score than those who did not complete the course.

The correlation analysis also showed strong positive relationships among Mathematics, Reading and Writing scores. The strongest relationship was found between Reading and Writing, with a correlation of approximately 0.955.

Overall, the project demonstrates how data analysis and visualization can transform raw student examination data into meaningful information and help in understanding academic performance.

---

## 16. Future Scope

The project can be further improved in several ways.

* Machine learning models can be used to predict students' future performance.
* Students who may require additional academic support can be identified.
* More demographic and socio-economic factors can be analyzed.
* An interactive dashboard can be developed for teachers and educational institutions.
* Student performance can be compared across different academic years.
* Larger datasets can be used for more reliable analysis.
* Performance prediction can be used to provide personalized academic recommendations.

---

## 17. Project Summary

The **Student Performance Analysis** project analyzes student examination data using Python-based data analysis techniques.

The project focuses on Mathematics, Reading and Writing scores and studies how academic performance varies across factors such as parental education, lunch type and test preparation.

Different visualizations are used to understand the data clearly. Bar charts are used for group comparisons, box plots are used to compare score distributions, scatter plots are used to study relationships, and correlation heatmaps are used to visualize relationships between subjects.

The analysis shows that test preparation is associated with higher average performance and that the three academic subjects have strong positive relationships.

This project provides a practical example of how data analysis can be applied to the education domain to discover useful patterns and support better understanding of student performance.
