#  Task 2 – Superstore Sales Data Analysis

# 1. Project Title

**Superstore Sales Data Analysis and Visualization using Python**

# 2. 📖 Introduction

This project is about analyzing a **Superstore sales dataset** using Python.

The dataset contains information about sales, profit, categories, discounts, order dates, shipping dates, and other business-related information.

The main purpose of this project is to understand the data and find useful information from it using:

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn

The project uses **Exploratory Data Analysis (EDA)** and different types of graphs to understand the dataset easily.


# 3.  Project Objective

The main objectives of this project are:

# Objective 1 – Understand the Dataset

First, we load the dataset and check:

* How many rows are present
* How many columns are present
* What are the column names
* What type of data each column contains

# Objective 2 – Clean and Prepare the Data

We prepare the data for analysis by:

* Converting date columns
* Checking missing values
* Creating a new delivery-days column

# Objective 3 – Analyze Sales

We calculate and compare sales for different categories.

# Objective 4 – Analyze Profit

We study profit values and compare profit between different categories.

# Objective 5 – Analyze Discount

We check the relationship between discount and profit.

# Objective 6 – Analyze Correlation

We calculate correlations between numerical columns and display them using a heatmap.


# 4. Technologies Used

| Technology       | Use                         |
| ---------------- | --------------------------- |
| Python           | Main programming language   |
| Pandas           | Data handling and analysis  |
| NumPy            | Numerical operations        |
| Matplotlib       | Creating graphs             |
| Seaborn          | Creating advanced graphs    |
| Jupyter Notebook | Running the project         |
| Google Colab     | Online notebook environment |



# 5. Python Libraries

The project uses the following libraries:

 python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns


# Pandas

Pandas is used to:

* Read the CSV file
* Store data in a DataFrame
* Analyze data
* Group data
* Find missing values
* Perform calculations

# NumPy

NumPy is used for numerical operations.

# Matplotlib

Matplotlib is used for creating graphs and charts.

# Seaborn

Seaborn is used for attractive statistical visualizations.


# 6.  Dataset

The project uses the following dataset:

text
samplesuperstore.csv


The dataset contains Superstore business information.

Important columns used in the project include:

* Order Date
* Ship Date
* Category
* Sales
* Profit
* Discount

The dataset is loaded using:

```python
df = pd.read_csv("/content/samplesuperstore.csv")
```

Here:

* `pd` means Pandas.
* `read_csv()` reads the CSV file.
* `df` is the DataFrame containing the dataset.

---

# 7.  Project Workflow

The project follows these steps:

```text
Superstore Dataset
       ↓
Load Dataset
       ↓
Explore Dataset
       ↓
Check Data Information
       ↓
Descriptive Statistics
       ↓
Convert Date Columns
       ↓
Calculate Delivery Days
       ↓
Find Categories
       ↓
Check Missing Values
       ↓
Analyze Sales
       ↓
Analyze Profit
       ↓
Analyze Discount
       ↓
Correlation Analysis
       ↓
Create Visualizations
       ↓
Find Useful Insights
```

---

# 8.  Load the Dataset

The first step is loading the CSV dataset.

```python
df = pd.read_csv("/content/samplesuperstore.csv")
```

### Explanation

`read_csv()` is a Pandas function.

It reads the CSV file and converts it into a DataFrame.

The DataFrame is stored in:

```text
df
```

We can think of `df` as a table containing all the dataset information.

---

# 9. 👀 View the Dataset

We can display the first few rows using:

```python
df.head()
```

### What does `head()` do?

By default, `head()` displays the first **5 rows**.

It helps us understand:

* What the data looks like
* Column names
* Values in each column
* Dataset structure

---

# 10. 🔎 Dataset Information

The following command is used:

```python
df.info()
```

### What does `info()` show?

It shows:

1. Number of rows
2. Column names
3. Number of non-null values
4. Data types
5. Memory usage

For example:

```text
Column       Data Type
----------------------
Sales        float
Profit       float
Category     object
Discount     float
```

This helps us understand what type of data we are working with.

---

# 11. 📊 Descriptive Statistics

The following command is used:

```python
df.describe()
```

### What does `describe()` do?

It provides statistical information about numerical columns.

It includes:

* Count
* Mean
* Standard deviation
* Minimum
* 25% value
* 50% value
* 75% value
* Maximum

### Example

```text
Mean
 ↓
Average value
```

For example, if the average sales value is high, it tells us that sales values are generally high in the dataset.

---

# 12. 📅 Convert Order Date

The project converts the `Order Date` column into datetime format.

```python
df['Order Date'] = pd.to_datetime(df['Order Date'])
```

### Why?

Sometimes dates are stored as text.

For example:

```text
01/01/2025
```

Python may treat this as a string.

Using:

```python
pd.to_datetime()
```

converts it into a proper date format.

This allows us to perform date calculations.



# 13.  Convert Ship Date

The `Ship Date` column is also converted.

 python
df['Ship Date'] = pd.to_datetime(df['Ship Date'])


Now both:

 text
Order Date
Ship Date


are in datetime format.


# 14. Calculate Delivery Days

The project creates a new column:

python
df['Delivery Days'] = (
    df['Ship Date'] - df['Order Date']
).dt.days


# What does this mean?

It calculates how many days were taken to ship an order.

# Formula

 text
Delivery Days =
Ship Date - Order Date


#  Example

Suppose:

  text
Order Date = January 1
Ship Date  = January 4


Then:

 text
Delivery Days = 3


So the new column tells us how many days each order took to ship.



# 15.  Find Product Categories

The project checks the unique categories using:

  python
df['Category'].unique()


# What is `unique()`?

`unique()` returns different values without repeating them.

For example:

 text
Technology
Furniture
Office Supplies

This helps us understand the categories available in the dataset.



# 16.  Check Missing Values

The project checks missing values using:

 python
df.isnull().sum()


# Explanation

`isnull()` checks whether a value is missing.

`sum()` counts the missing values.

So:

 python
df.isnull().sum()


gives the number of missing values in each column.

# Why is this important?

Missing values can affect analysis.

Before performing analysis, it is important to know whether the dataset contains missing data.



# 17. Sales Analysis

One important part of the project is analyzing sales.

We calculate total sales for each category.

 python
category_sales = (
    df.groupby('Category')['Sales'].sum()
)


# Explanation

First:

 python
df.groupby('Category')


groups the data according to category.

Then:

 python
['Sales'].sum()


calculates the total sales.

The result is stored in:

 text
category_sales



# 18. Sales by Category

A bar chart is used to visualize category-wise sales.

 python
category_sales.plot(
    kind='bar',
    figsize=(8,5)
)

plt.title("Sales by Category")
plt.ylabel("Total Sales")
plt.show()


# Why use a bar chart?

A bar chart makes it easy to compare categories.

For example:

 text
Category A  █████████
Category B  ███████
Category C  ███████████


A taller bar means higher sales.



# 19.  Sales Distribution

The project uses a histogram to understand sales distribution.

```python
plt.figure(figsize=(8,5))

sns.histplot(
    df['Sales'],
    bins=30
)

plt.title("Sales Distribution")
plt.show()


### What is a histogram?

A histogram shows how frequently values occur within ranges.

For example:

```text
Number of Orders
      │
      │       ███
      │    ███████
      │ ███████████
      └────────────────
          Sales


It helps us understand the distribution of sales.


# 20. Profit Analysis

Profit is another important part of the project.

The project creates a bar plot to compare profit by category.

 python
sns.barplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit by Category")
plt.show()


# Purpose

This graph helps compare profit between categories.

We can easily see which category has:

* Higher profit
* Lower profit
* Different profit levels



# 21.  Sales Distribution by Category

Another bar plot is used:

 python
sns.barplot(
    data=df,
    x="Category",
    y="Sales"
)

plt.title("Sales Distribution by Category")
plt.show()


# Purpose

This graph helps us visually compare sales values among categories.



# 22. Profit Distribution – Box Plot

The project uses a box plot:

```python
sns.boxplot(
    data=df,
    y="Profit"
)

plt.title("Profit Distribution")
plt.show()


# What is a box plot?

A box plot shows the distribution of numerical data.

It helps identify:

* Minimum
* Maximum
* Median
* Spread
* Possible outliers

# Simple structure

 text
Maximum
   │
   ─
   │
┌───────┐
│       │
│Median │
│       │
└───────┘
   │
   ─
   │
Minimum

# 23.  Profit Variation Across Categories

The project also compares profit variation between categories.

```python
sns.boxplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit Variation Across Categories")
plt.show()


# Purpose

This graph helps us understand:

* Which category has greater profit variation
* Which category has more consistent profit
* Where possible outliers exist


# 24. Discount Analysis

The project checks the different discount values using:

  python
df["Discount"].unique()


This shows the different discount levels present in the dataset.



# 25. Discount vs Profit

A scatter plot is used to analyze discount and profit.

  python
sns.scatterplot(
    data=df,
    x="Discount",
    y="Profit"
)

plt.title("Impact of Discount on Profit")
plt.show()


### What is a scatter plot?

A scatter plot displays individual data points.

Here:

text
X-axis → Discount
Y-axis → Profit


Each point represents a data record.

### Main purpose

The graph helps us visually study whether changes in discount are associated with changes in profit.



# 26.  Select Numerical Columns

For correlation analysis, numerical columns are selected.

python
numeric_df = df.select_dtypes(
    include="number"
)


# What does this do?

It selects only numerical columns.

Examples include:

* Sales
* Profit
* Discount
* Quantity
* Delivery Days

depending on the columns available in the dataset.



# 27.  Calculate Correlation

The project calculates correlation using:

python
corr = numeric_df.corr()


# What is correlation?

Correlation tells us how two numerical variables are related.

The value generally ranges from:

 text
-1 to +1


# Simple explanation

 text
+1  → Strong positive relationship

 0  → Little/no linear relationship

-1  → Strong negative relationship


# Positive correlation

When one variable increases, another tends to increase.

# Negative correlation

When one variable increases, another tends to decrease.



# 28.  Correlation Heatmap

The correlation values are visualized using:

python
sns.heatmap(
    corr,
    annot=True
)

plt.title("Correlation Heatmap")
plt.show()


# What is a heatmap?

A heatmap represents numerical values using different visual intensities.

The `annot=True` option displays the actual correlation value.

For example:

text
             Sales   Profit   Discount
Sales         1.00    0.48      -0.10
Profit        0.48    1.00      -0.22
Discount     -0.10   -0.22       1.00


The exact values depend on the dataset.



# 29.  Visualizations Used

The project uses several visualization techniques.

| Visualization | Purpose                              |
| ------------- | ------------------------------------ |
| Bar Plot      | Compare categories                   |
| Histogram     | Understand distribution              |
| Box Plot      | Understand spread and outliers       |
| Scatter Plot  | Study relationship between variables |
| Heatmap       | Study correlations                   |



# 30. What We Learn From This Project

This project helps us understand how to perform a complete basic data analysis workflow.

#Step 1

Load the dataset.

#Step 2

Understand the dataset.

#Step 3

Check missing values.

#Step 4

Prepare date columns.

#Step 5

Create a new feature called `Delivery Days`.

#Step 6

Analyze sales.

#Step 7

Analyze profit.

#Step 8

Analyze discount.

#Step 9

Calculate correlations.

#Step 10

Create graphs to understand the results.



# 31.  Project Folder Structure

The recommended GitHub folder structure is:

  text
Task-2-Superstore-Analysis/
│
├── README.md
│
├── Task 2.ipynb
│
├── samplesuperstore.csv
│
└── images/
    │
    ├── sales_by_category.png
    ├── sales_distribution.png
    ├── profit_by_category.png
    ├── profit_distribution.png
    ├── profit_variation.png
    ├── discount_vs_profit.png
    └── correlation_heatmap.png


# 32. How to Run the Project

## Google Colab

### Step 1

Open Google Colab.

### Step 2

Upload:

text
Task 2.ipynb


### Step 3

Upload:

text
samplesuperstore.csv


### Step 4

Run the cells one by one.



## Jupyter Notebook

Install the required libraries:

bash
pip install pandas numpy matplotlib seaborn


Then open Jupyter Notebook:

bash
jupyter notebook


Open:

text
Task 2.ipynb


Run all cells.



# 33.  Important Python Concepts Used

This project demonstrates the following Python and Data Science concepts:

# DataFrame

A DataFrame is a table-like structure provided by Pandas.

# `read_csv()`

Used to read CSV files.

# `head()`

Used to view the first rows.

# `info()`

Used to understand dataset structure.

# `describe()`

Used for statistical summary.

# `groupby()`

Used to group data.

# `sum()`

Used to calculate totals.

# `unique()`

Used to find unique values.

# `isnull()`

Used to identify missing values.

# `to_datetime()`

Used to convert values into date format.

# `corr()`

Used to calculate correlations.

# 34.  Learning Outcomes

After completing this project, we can understand:

* How to load a dataset using Pandas
* How to explore a dataset
* How to check data types
* How to check missing values
* How to convert dates
* How to create new columns
* How to group data
* How to calculate total sales
* How to analyze profit
* How to analyze discount
* How to create different graphs
* How to calculate correlation
* How to create a heatmap
* How to perform basic Exploratory Data Analysis



# 35.  Future Improvements

This project can be improved by adding:

# 1. Monthly Sales Analysis

Analyze sales month by month.

# 2. Yearly Sales Analysis

Compare sales between different years.

# 3. Region Analysis

Analyze sales and profit by region.

# 4. State Analysis

Find states with higher sales and profit.

# 5. Product Analysis

Find the best-selling products.

# 6. Customer Analysis

Analyze customer purchasing behavior.

# 7. Interactive Dashboard

Create an interactive dashboard using:

* Plotly
* Streamlit
* Power BI

# 8. Machine Learning

Future versions can use machine learning for sales prediction.



# 36. Conclusion

The **Superstore Sales Data Analysis** project demonstrates how Python can be used to analyze business data.

The project starts with loading and understanding the dataset.

Then the data is prepared by converting date columns and calculating delivery days.

After that, sales, profit, and discount are analyzed.

Different graphs are used to make the data easier to understand.

Finally, numerical correlations are calculated and visualized using a heatmap.

The complete process is:

  text
Load Data
   ↓
Explore Data
   ↓
Clean / Prepare Data
   ↓
Analyze Data
   ↓
Visualize Data
   ↓
Study Relationships
   ↓
Generate Insights


# Output

<img width="992" height="716" alt="Screenshot 2026-08-11 103129" src="https://github.com/user-attachments/assets/ddf134c7-17e0-4997-931c-fc4fd90a26f3" />
<img width="928" height="603" alt="Screenshot 2026-08-11 103227 - Copy" src="https://github.com/user-attachments/assets/015917cd-ef23-4f73-8356-e99f010680c0" />
<img width="705" height="562" alt="Screenshot 2026-08-11 103257" src="https://github.com/user-attachments/assets/b4ebc1ad-db59-4445-b649-174317557642" />
<img width="741" height="566" alt="Screenshot 2026-08-11 103321" src="https://github.com/user-attachments/assets/e4d6520c-446b-4d61-baf3-60ea54f467dc" />
<img width="822" height="527" alt="Screenshot 2026-08-11 103330" src="https://github.com/user-attachments/assets/953098cf-5eb6-4854-a2c0-aa7b01a18c5c" />
<img width="780" height="576" alt="Screenshot 2026-08-11 103408" src="https://github.com/user-attachments/assets/e0e362a2-c73c-41d3-a468-d43def37d460" />
<img width="806" height="555" alt="Screenshot 2026-08-11 103426" src="https://github.com/user-attachments/assets/b2519d41-caa4-4e6f-9252-ef0b73b6b0b1" />
<img width="860" height="641" alt="Screenshot 2026-08-11 103450" src="https://github.com/user-attachments/assets/c98a9d6c-b4ec-442a-acc6-2853ede1a979" />



 # Author
 
S. Naranjana

Course: Bachelor of Computer Applications

College: Kamaraj College(Face prep campus)

