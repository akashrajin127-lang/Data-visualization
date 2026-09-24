# Task 1 – Big Data Analytics

## 📌 Project Overview

This project performs **exploratory data analysis (EDA)** on a Sample Superstore dataset using Python. The analysis focuses on understanding sales, quantity, discount, profit, product categories, regions, and order dates.

The project is implemented in a **Google Colab / Jupyter Notebook** using popular Python data-analysis and visualization libraries.

## 🎯 Objectives

- Load and explore the Superstore dataset.
- Understand the structure and characteristics of the data.
- Perform basic statistical analysis.
- Check and handle date-related data.
- Identify missing values.
- Analyze sales by product category.
- Visualize sales distributions and category-wise sales.
- Extract useful business insights from the dataset.

## 🗂️ Dataset

The dataset contains **100 records and 10 columns**.

### Columns

| Column | Description |
|---|---|
| Order ID | Unique identifier for each order |
| Order Date | Date on which the order was placed |
| Category | Product category |
| Sub-Category | Product sub-category |
| State | Customer/order state |
| Region | Sales region |
| Sales | Sales amount |
| Quantity | Number of items ordered |
| Discount | Discount applied to the order |
| Profit | Profit or loss generated |

The dataset contains three main categories: **Technology, Furniture, and Office Supplies**.

## 🛠️ Technologies Used

- **Python 3**
- **Pandas** – Data manipulation and analysis
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical visualization
- **Google Colab / Jupyter Notebook**

## 🔄 Analysis Workflow

The notebook follows these main steps:

1. **Import Libraries**
   - Pandas
   - NumPy
   - Matplotlib
   - Seaborn

2. **Load Dataset**
   ```python
   df = pd.read_csv("/SampleSuperstore.csv")
   ```

3. **Data Exploration**
   - `df.head()`
   - `df.info()`
   - `df.describe()`

4. **Data Type Conversion**

   The `Order Date` column is converted into a datetime format:

   ```python
   df['Order Date'] = pd.to_datetime(df['Order Date'])
   ```

5. **Category Analysis**

   Total sales are calculated for each category using `groupby()`:

   ```python
   category_sales = df.groupby('Category')['Sales'].sum()
   ```

6. **Visualization**

   A bar chart is used to compare sales across categories.

   A histogram is also created to visualize the distribution of sales.

## 📊 Key Results

### Category-wise Sales

| Category | Total Sales |
|---|---:|
| Furniture | 27,931.75 |
| Office Supplies | 43,584.58 |
| Technology | 38,462.42 |

Based on the notebook's calculated results, **Office Supplies has the highest total sales**, followed by Technology and Furniture.

### Descriptive Statistics

The dataset contains:

- **Average Sales:** 1099.79
- **Average Quantity:** 5.16
- **Average Discount:** 0.137
- **Average Profit:** 87.36
- **Minimum Profit:** -283.40
- **Maximum Profit:** 595.18

The dataset has 100 non-null values for each of its 10 columns. 
## 📈 Visualizations

The notebook includes:

- **Sales by Category** – Bar chart comparing total sales among product categories.
- **Sales Distribution** – Histogram showing the distribution of sales values. 
## 🔍 Data Quality

Missing-value analysis was performed using:

```python
df.isnull().sum()
```

All 10 columns contain **0 missing values** in the analyzed dataset.

## 📁 Project Structure

```text
Task-1-BDA/
│
├── Task_1_BDA_(2).ipynb
├── SampleSuperstore.csv
└── README.md
```

## ▶️ How to Run

### Option 1: Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Upload `Task_1_BDA_(2).ipynb`.
3. Upload the `SampleSuperstore.csv` dataset.
4. Update the dataset path if required.
5. Run all notebook cells.

### Option 2: Jupyter Notebook

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

Then start Jupyter:

```bash
jupyter notebook
```

Open `Task_1_BDA_(2).ipynb` and run the cells.

## 💡 Conclusion

This project demonstrates how Python-based data analytics can be used to explore and visualize business data. The analysis identifies sales patterns across product categories and provides basic statistical insights into sales, quantity, discount, and profit.

The results show that **Office Supplies generated the highest total sales** among the three categories in the analyzed dataset.

## 👨‍💻 Author

**Akash Raj T**

BCA – Bachelor of Computer Application