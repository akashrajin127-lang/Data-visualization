# Student Performance Analysis & Visualization

Exploratory data analysis of the **Students Performance** dataset. The project uses `pandas`, `matplotlib`, and `seaborn` to examine how factors such as parental education, lunch type, and test preparation relate to students' math, reading, and writing scores.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Repository Structure](#repository-structure)
- [Dataset](#dataset)
- [Requirements](#requirements)
- [How to Run](#how-to-run)
- [Analysis Performed](#analysis-performed)
- [Key Findings](#key-findings)
- [Notes](#notes)

---

## Project Overview

The goal of this project is to explore the dataset visually and statistically to answer questions like:

- Do students with different parental education levels score differently?
- Does lunch type (standard vs. free/reduced) relate to performance?
- Does completing a test preparation course improve scores?
- How strongly are the three subject scores related to each other?

## Repository Structure

```
.
├── task_8.ipynb                          # Jupyter / Colab notebook with the full analysis
├── task_8.py                             # Same analysis exported as a Python script
├── StudentsPerformance_csv.xls           # Raw dataset (CSV content, despite the .xls extension)
├── StudentsPerformance_preprocessed.csv  # Cleaned dataset used by the analysis
└── README.md
```

## Dataset

**File used:** `StudentsPerformance_preprocessed.csv`
**Size:** 1,000 rows × 11 columns, no missing values.

| Column | Type | Description |
|---|---|---|
| `gender` | categorical | `female` / `male` |
| `race/ethnicity` | categorical | Anonymized groups: `group a` – `group e` |
| `parental level of education` | categorical | some high school, high school, some college, associate's degree, bachelor's degree, master's degree |
| `lunch` | categorical | `standard` / `free/reduced` |
| `test preparation course` | categorical | `none` / `completed` |
| `math score` | integer | Score from 0 to 100 |
| `reading score` | integer | Score from 0 to 100 |
| `writing score` | integer | Score from 0 to 100 |
| `total marks` | integer | Sum of the three scores (out of 300) |
| `percentage` | float | Total marks as a percentage |
| `outlier` | boolean | Flag marking outlier records (12 rows flagged) |

The raw file `StudentsPerformance_csv.xls` is a plain CSV with only the first 8 columns. The preprocessed version lowercases the text values and adds `total marks`, `percentage`, and `outlier`.

## Requirements

- Python 3.8+
- pandas
- matplotlib
- seaborn

Install dependencies:

```bash
pip install pandas matplotlib seaborn
```

## How to Run

### Option 1: Google Colab
1. Upload `task_8.ipynb` and `StudentsPerformance_preprocessed.csv` to Colab.
2. Place the CSV in `/content/` (the default Colab working directory).
3. Run all cells.

### Option 2: Local machine
1. Clone or download this repository.
2. Open `task_8.py` and update the file path on the data-loading line:
   ```python
   df = pd.read_csv('StudentsPerformance_preprocessed.csv')
   ```
   (The original path `/content/StudentsPerformance_preprocessed.csv` only works in Colab.)
3. Run the script:
   ```bash
   python task_8.py
   ```
   Or open `task_8.ipynb` in Jupyter Notebook / JupyterLab.

## Analysis Performed

**1. Grouped bar chart:** Average math, reading, and writing scores grouped by parental level of education and lunch type.

**2. Box plots:** Score distribution (variance) for each subject by test preparation course status:
- Math score
- Writing score
- Reading score

**3. Scatter plots:** Relationships between pairs of subjects:
- Math vs. Reading
- Math vs. Writing
- Reading vs. Writing

**4. Correlation heatmap:** Pearson correlation matrix across the three subject scores.

**5. Summary statistics (printed to console):**
- Average scores by lunch type
- Average scores by test preparation course
- Average scores by parental education
- Dataset shape, overall average scores, and the correlation matrix

## Key Findings

Values below are computed from the preprocessed dataset.

**Lunch type**

| Lunch | Math | Reading | Writing |
|---|---|---|---|
| Standard | 70.03 | 71.65 | 70.82 |
| Free/reduced | 58.92 | 64.65 | 63.02 |

**Test preparation course**

| Course | Math | Reading | Writing |
|---|---|---|---|
| Completed | 69.70 | 73.89 | 74.42 |
| None | 64.08 | 66.53 | 64.50 |

**Parental education:** Students whose parents hold a master's, bachelor's, or associate's degree generally score higher than those whose parents have a high school education or less. The lowest averages appear in the "high school" group.

**Score correlations**

| | Math | Reading | Writing |
|---|---|---|---|
| Math | 1.00 | 0.82 | 0.80 |
| Reading | 0.82 | 1.00 | 0.95 |
| Writing | 0.80 | 0.95 | 1.00 |

Reading and writing scores are very strongly correlated (0.95), while math is strongly but less tightly correlated with both.

> These are descriptive observations, not causal claims. The analysis shows association only and does not control for other variables.

## Notes

- The raw file has an `.xls` extension but is actually comma-separated text. Read it with `pd.read_csv`, not `pd.read_excel`.
- The `outlier` column is present in the preprocessed data but is not used by the current visualizations.
- `task_8.py` was auto-generated from a Google Colab notebook, so the data path points to `/content/`.

## License

This project is intended for educational purposes.
