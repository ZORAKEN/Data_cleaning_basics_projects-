# Data_cleaning_basics_projects-
cleaned amd formatted an excel sheet using pands.numpy
# Sales Data Cleaning Project

## Overview

This project focuses on cleaning and preprocessing a sales dataset (`sales.csv`) using Python and Pandas. The goal is to identify and fix common data quality issues such as missing values, invalid entries, incorrect data types, duplicate records, and inconsistent formatting.

## Dataset

File:

* `sales.csv`

The dataset contains sales transaction information, including:

* Transaction ID
* Item
* Quantity
* Price Per Unit
* Total Spent
* Payment Method
* Location
* Transaction Date

## Data Cleaning Tasks Performed

### 1. Missing and Invalid Values

* Identified missing values using:

  ```python
  df.isna().sum()
  ```
* Detected invalid values such as:

  * `UNKNOWN`
  * `ERROR`

### 2. Duplicate Records

* Counted duplicate rows:

  ```python
  df.duplicated().sum()
  ```
* Inspected duplicate entries:

  ```python
  df[df.duplicated()]
  ```

### 3. Data Type Conversion

Converted columns to appropriate data types:

```python
df["Quantity"] = pd.to_numeric(df["Quantity"], errors="coerce")
df["Price Per Unit"] = pd.to_numeric(df["Price Per Unit"], errors="coerce")
df["Total Spent"] = pd.to_numeric(df["Total Spent"], errors="coerce")
df["Transaction Date"] = pd.to_datetime(
    df["Transaction Date"],
    errors="coerce"
)
```

### 4. Handling Invalid Values

Replaced invalid entries with missing values:

```python
df = df.replace(["UNKNOWN", "ERROR"], pd.NA)
```

### 5. Sorting and Index Reset

```python
df = df.sort_values("Transaction ID").reset_index(drop=True)
```

## Technologies Used

* Python
* Pandas
* NumPy
* Jupyter Notebook

## Output Files

Cleaned datasets can be exported as:

### CSV

```python
df.to_csv("sales_cleaned.csv", index=False)
```

### JSON

```python
df.to_json(
    "sales_cleaned.json",
    orient="records",
    indent=4
)
```

### Excel

```python
df.to_excel(
    "sales_cleaned.xlsx",
    index=False
)
```

## Project Structure

```text
.
├── sales.csv
├── sales_cleaned.csv
├── sales_cleaned.json
├── notebook.ipynb
└── README.md
```

## Learning Outcomes

Through this project, I practiced:

* Exploratory Data Analysis (EDA)
* Data cleaning techniques
* Handling missing and invalid data
* Working with data types
* Detecting duplicates
* Exporting cleaned datasets
* Using Pandas for preprocessing

## Author

Data Cleaning Practice Project using Python and Pandas.

