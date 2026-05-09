# Internship Applications Data Cleaning Project

## Project Overview
This project focuses on cleaning and transforming raw internship application data using Python and Pandas. The dataset contains common real-world data quality issues such as missing values, duplicate records, inconsistent formatting, and outliers.

The objective of this project is to prepare the dataset for accurate analysis and reporting.

---

# Objectives
- Handle missing values
- Remove duplicate records
- Detect and manage outliers
- Standardize inconsistent formatting
- Transform raw data into structured format
- Automate data cleaning using Python (Pandas)


#  Problems
The dataset intentionally contains:

- Missing values
- Duplicate rows
- Outliers
- Inconsistent text formatting
- Mixed categorical values

### Examples:
- `male` / `Male` / `MALE`
- Extra spaces in names
- Invalid CGPA values
- Unrealistic ages

---

# Project Workflow

## 1. Import Libraries

```python
import pandas as pd
import numpy as np
```

---

## 2. Load Dataset

```python
df = pd.read_csv("internship_applications_dirty_dataset.csv")
```

---

## 3. Explore Dataset

```python
df.head()
df.info()
df.describe()
```

---

## 4. Handle Missing Values

```python
df['Age'] = df['Age'].fillna(df['Age'].mean())

df['Skills'] = df['Skills'].fillna(
    df['Skills'].mode()[0]
)
```

---

## 5. Remove Duplicate Rows

```python
df = df.drop_duplicates()
```

---

## 6. Detect and Remove Outliers

Used the IQR (Interquartile Range) method.

```python
Q1 = df['CGPA'].quantile(0.25)
Q3 = df['CGPA'].quantile(0.75)

IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

df = df[
    (df['CGPA'] >= lower) &
    (df['CGPA'] <= upper)
]
```

---

## 7. Standardize Data Formatting

```python
df['Gender'] = df['Gender'].str.capitalize()

df['Name'] = df['Name'].str.strip()
```

---

## 8. Save Cleaned Dataset

```python
df.to_csv(
    "cleaned_internship_data.csv",
    index=False
)
```

---

# Key Skills Demonstrated
- Data Cleaning
- Data Transformation
- Data Preprocessing
- Outlier Detection
- Pandas Operations
- Data Standardization
- Exploratory Data Analysis (EDA)

---

# Learning Outcomes
Through this project, I learned:
- How to clean messy real-world datasets
- How to automate preprocessing tasks using Python
- How to improve data quality for analysis
- Best practices for handling missing values and outliers

---


# Author
**Yasmeen Rafique**
