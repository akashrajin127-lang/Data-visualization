# Healthcare Dataset Analysis

## 📌 Project Overview

This project focuses on **Healthcare Dataset Analysis** using Python. The dataset contains patient-related information such as medical conditions, admission and discharge dates, admission types, gender, medical codes, and billing amounts.

The project performs **data understanding, data cleaning, exploratory data analysis, and feature engineering** to identify useful patterns in healthcare data.

---

## 🎯 Objectives

The main objectives of this project are:

* Load and understand the healthcare dataset.
* Inspect dataset columns and structure.
* Identify missing values.
* Check missing values in specific columns.
* Convert admission and discharge dates into datetime format.
* Clean categorical data.
* Analyze different admission types.
* Analyze billing amounts statistically.
* Calculate hospital stay duration.
* Analyze the relationship between medical conditions and gender.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Jupyter Notebook / Google Colab**

---

## 📂 Dataset

The project uses:

```text
healthcare_dataset.csv
```

The dataset contains healthcare-related patient information.

### Important Features

| Feature             | Description                              |
| ------------------- | ---------------------------------------- |
| `Medical_Code`      | Code associated with the medical record  |
| `Admission_Date`    | Date on which the patient was admitted   |
| `Discharge_Date`    | Date on which the patient was discharged |
| `Admission_Type`    | Type of hospital admission               |
| `Gender`            | Patient gender                           |
| `Medical_Condition` | Patient's medical condition              |
| `Billing_Amount`    | Amount billed for healthcare services    |

### Engineered Feature

| Feature              | Description                                    |
| -------------------- | ---------------------------------------------- |
| `Hospital_Stay_Days` | Number of days between admission and discharge |

---

## 1. Import Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

These libraries are used for:

* **Pandas** – data manipulation and analysis
* **NumPy** – numerical operations
* **Matplotlib** – data visualization
* **Seaborn** – statistical visualization

---

## 2. Load the Dataset

```python
df = pd.read_csv("healthcare_dataset.csv")
```

The CSV file is loaded into a Pandas DataFrame called `df`.

---

## 3. Data Understanding

### View the First Five Records

```python
df.head()
```

Displays the first five rows of the dataset.

### Display Column Names

```python
df.columns
```

Displays all available columns.

---

## 4. Missing Value Analysis

To check missing values:

```python
df.isnull()
```

To count missing values in each column:

```python
df.isnull().sum()
```

A specific column can also be checked:

```python
df['Medical_Code'].isnull().sum()
```

This identifies the number of missing values specifically in the `Medical_Code` column.

---

## 5. Date Conversion

The admission date is converted into datetime format:

```python
df['Admission_Date'] = pd.to_datetime(
    df['Admission_Date']
)
```

Similarly, the discharge date is converted:

```python
df['Discharge_Date'] = pd.to_datetime(
    df['Discharge_Date']
)
```

Converting dates to datetime allows date calculations and time-based analysis.

---

## 6. Cleaning Admission Type

The `Admission_Type` column is cleaned using:

```python
df['Admission_Type'] = (
    df['Admission_Type']
    .str.strip()
    .str.lower()
)
```

### Cleaning Operations

* `str.strip()` removes unnecessary spaces.
* `str.lower()` converts all text to lowercase.

For example:

```text
" Emergency " → "emergency"
"Urgent"      → "urgent"
```

This makes categorical values more consistent.

---

## 7. Admission Type Analysis

A cross-tabulation is created using:

```python
pd.crosstab(
    df['Admission_Type'],
    df['Admission_Date']
)
```

This creates a frequency table showing admission types across admission dates.

The number of records for each admission type can be found using:

```python
df["Admission_Type"].value_counts()
```

This helps determine how frequently each type of admission occurs.

---

## 8. Billing Amount Analysis

Descriptive statistics for billing amounts are calculated using:

```python
df["Billing_Amount"].describe()
```

This provides:

* Count
* Mean
* Standard deviation
* Minimum
* 25th percentile
* Median
* 75th percentile
* Maximum

The billing values can also be displayed directly:

```python
df["Billing_Amount"]
```

---

## 9. Feature Engineering – Hospital Stay

A new feature called `Hospital_Stay_Days` is created:

```python
df['Hospital_Stay_Days'] = (
    df['Discharge_Date'] -
    df['Admission_Date']
).dt.days
```

This calculates the number of days each patient stayed in the hospital.

### Example

```text
Admission Date:  2025-01-01
Discharge Date: 2025-01-06

Hospital Stay = 5 days
```

The statistical summary of hospital stay duration is displayed using:

```python
display(
    df['Hospital_Stay_Days'].describe()
)
```

---

## 10. Medical Condition and Gender Analysis

The relationship between medical condition and gender is analyzed using:

```python
pd.crosstab(
    df["Medical_Condition"],
    df["Gender"]
)
```

This produces a frequency table showing the number of patients of each gender for each medical condition.

Example structure:

```text
Gender              Female    Male
Medical_Condition
Diabetes              120     115
Asthma                105     110
Cancer                130     125
```

The actual values depend on the dataset.

---

## 📊 Analysis Performed

The project performs the following analysis:

| Analysis                    | Method                       |
| --------------------------- | ---------------------------- |
| Dataset inspection          | `head()`, `columns`          |
| Missing value analysis      | `isnull().sum()`             |
| Date processing             | `pd.to_datetime()`           |
| Categorical cleaning        | `str.strip()`, `str.lower()` |
| Admission analysis          | `value_counts()`             |
| Billing analysis            | `describe()`                 |
| Hospital stay               | Date difference              |
| Medical condition vs gender | `pd.crosstab()`              |

---

## 🚀 Project Workflow

```text
Healthcare Dataset
       ↓
Load Dataset
       ↓
Understand Data
       ↓
Check Columns
       ↓
Check Missing Values
       ↓
Convert Date Columns
       ↓
Clean Admission Type
       ↓
Analyze Admission Types
       ↓
Analyze Billing Amount
       ↓
Calculate Hospital Stay
       ↓
Analyze Medical Condition vs Gender
```

---

## 📁 Project Structure

```text
Healthcare-Data-Analysis/
│
├── healthcare_dataset.csv
├── Healthcare_Analysis.ipynb
└── README.md
```

---

## ⚠️ Note

The following imports are included for future visualization work:

```python
import matplotlib.pyplot as plt
import seaborn as sns
```

The current analysis primarily uses **Pandas** for data cleaning, feature engineering, and statistical analysis.

---

## ✅ Conclusion

This project demonstrates a basic **healthcare data analysis workflow using Python**. The dataset is inspected for structure and missing values, date columns are converted into a usable format, categorical admission types are cleaned, billing statistics are analyzed, hospital stay duration is calculated, and medical conditions are compared across gender.

The resulting dataset can be used for further **exploratory data analysis and visualization**.

---

## 👨‍💻 Author

**Akash Raj T.**

BCA – Bachelor of Computer Applications
