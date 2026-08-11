📊 Task 2 – Superstore Sales Data Analysis

# About the Project

This project is a Superstore Sales Data Analysis project using Python.

The main purpose of this project is to analyze sales, profit, discount, and delivery information from the Superstore dataset.

Different Python libraries are used to understand the data and create graphs.



# Objectives

The main objectives of this project are:

- Load the Superstore dataset.
- Understand the dataset.
- Check the data information.
- Generate basic statistics.
- Convert order and shipping dates.
- Calculate delivery days.
- Find different product categories.
- Check missing values.
- Analyze sales by category.
- Analyze profit by category.
- Study the relationship between discount and profit.
- Find correlations between numerical variables.
- Create different visualizations.


# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab



# Libraries

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

Pandas

Used for loading, cleaning, grouping, and analyzing the dataset.

NumPy

Used for numerical operations.

Matplotlib

Used for creating charts and graphs.

Seaborn

Used for creating statistical visualizations.


# Dataset

The project uses the:

"samplesuperstore.csv"

dataset.

The dataset is loaded using:

df = pd.read_csv("/content/samplesuperstore.csv")

The analysis mainly uses columns such as:

- Order Date
- Ship Date
- Category
- Sales
- Profit
- Discount


# Project Steps

1. Import Libraries

First, the required Python libraries are imported.

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

These libraries help us perform data analysis and visualization.


2. Load the Dataset

The CSV file is loaded using Pandas.

df = pd.read_csv("/content/samplesuperstore.csv")

The data is stored in the variable "df".


3. View the Dataset

df.head()

"head()" displays the first few rows of the dataset.

It helps us understand what the data looks like.


4. Check Dataset Information

df.info()

This shows:

- Column names
- Number of values
- Data types
- Dataset structure



5. Generate Statistics

df.describe()

This provides basic statistical information such as:

- Count
- Mean
- Minimum
- Maximum
- Standard deviation
- Quartiles
  

6. Convert Date Columns

The "Order Date" and "Ship Date" columns are converted into date format.

df['Order Date'] = pd.to_datetime(df['Order Date'])
df['Ship Date'] = pd.to_datetime(df['Ship Date'])

This allows us to perform date calculations.


7. Calculate Delivery Days

A new column called "Delivery Days" is created.

df['Delivery Days'] = (
    df['Ship Date'] - df['Order Date']
).dt.days

Meaning

Delivery Days = Ship Date - Order Date

It tells us how many days an order took to ship.



8. Find Categories

df['Category'].unique()

This finds the different categories available in the dataset.


9. Check Missing Values

df.isnull().sum()

This checks whether any columns contain missing values.

It helps us understand the quality of the dataset.


# Data Analysis

10. Sales by Category

First, total sales for each category are calculated.

category_sales = (
    df.groupby('Category')['Sales'].sum()
)

Explanation

"groupby()" groups the data by category.

"sum()" calculates the total sales.



11. Sales by Category – Bar Plot

category_sales.plot(
    kind='bar',
    figsize=(8,5)
)

plt.title("Sales by Category")
plt.ylabel("Total Sales")
plt.show()

Purpose

The bar plot is used to compare sales between different categories.



12. Sales Distribution

A histogram is created to understand the distribution of sales.

sns.histplot(
    df['Sales'],
    bins=30
)

plt.title("Sales Distribution")
plt.show()

Purpose

The histogram shows how sales values are distributed.


13. Profit by Category

sns.barplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit by Category")
plt.show()

Purpose

This graph compares profit between different categories.


14. Sales Distribution by Category

sns.barplot(
    data=df,
    x="Category",
    y="Sales"
)

plt.title("Sales Distribution by Category")
plt.show()

This visualization compares sales across categories.

# Box Plot Analysis

15. Profit Distribution

sns.boxplot(
    data=df,
    y="Profit"
)

plt.title("Profit Distribution")
plt.show()

A box plot helps understand:

- Data distribution
- Median
- Variation
- Outliers


16. Profit Variation Across Categories

sns.boxplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit Variation Across Categories")
plt.show()

This helps compare profit variation between categories.


# Discount vs Profit

17. Check Discount Values

df["Discount"].unique()

This displays the different discount values in the dataset.

18. Analyze Discount and Profit

sns.scatterplot(
    data=df,
    x="Discount",
    y="Profit"
)

plt.title("Impact of Discount on Profit")
plt.show()

Purpose

The scatter plot is used to study the relationship between:

Discount → Profit

The main question is:

At what discount level does profit start decreasing?


# Correlation Analysis

19. Select Numerical Columns

numeric_df = df.select_dtypes(
    include="number"
)

This selects the numerical columns from the dataset.



20. Calculate Correlation

corr = numeric_df.corr()

Correlation shows the relationship between numerical variables.

Correlation values range from:

-1 to +1

Simple meaning

- +1 → Strong positive relationship
- 0 → No linear relationship
- -1 → Strong negative relationship



21. Correlation Heatmap

sns.heatmap(
    corr,
    annot=True
)

plt.title("Correlation Heatmap")
plt.show()

The heatmap makes it easier to understand relationships between numerical columns.


# Visualizations Used

Graph| Purpose
Bar Plot| Compare sales and profit
Histogram| Show sales distribution
Box Plot| Show profit distribution and variation
Scatter Plot| Study discount vs profit
Heatmap| Show correlations


#  What I Learned

Through this project, I learned how to:

- Load a CSV dataset using Pandas.
- Explore a dataset.
- Check dataset information.
- Generate statistics.
- Convert date columns.
- Create a new column.
- Calculate delivery days.
- Check missing values.
- Group data using "groupby()".
- Calculate total sales.
- Analyze profit.
- Analyze discounts.
- Create different types of graphs.
- Calculate correlation.
- Create a correlation heatmap.


# Future Improvements

This project can be improved by adding:

- Monthly sales analysis
- Year-wise sales analysis
- Region-wise analysis
- State-wise analysis
- Product-wise analysis
- Customer analysis
- Interactive dashboard
- Sales prediction using Machine Learning


 # Conclusion

This project demonstrates the basic process of Data Analysis and Data Visualization using Python.

The Superstore dataset is explored and analyzed using Pandas.

Sales, profit, discount, and delivery information are studied using different graphs.

The project also uses correlation analysis to understand relationships between numerical variables.

Overall, this project provides practical experience in:

Data Loading
     ↓
Data Exploration
     ↓
Data Processing
     ↓
Data Analysis
     ↓
Data Visualization
     ↓
Correlation Analysis

 # Output
 
 <img width="992" height="716" alt="Screenshot 2026-08-11 103129" src="https://github.com/user-attachments/assets/40385b0c-b39f-4fd4-a999-7616657b8635" />
<img width="928" height="603" alt="Screenshot 2026-08-11 103227 - Copy" src="https://github.com/user-attachments/assets/25ebf57d-c8dc-4492-840b-6b49775aaf4f" />
<img width="705" height="562" alt="Screenshot 2026-08-11 103257" src="https://github.com/user-attachments/assets/b24f04ed-7b39-4d7c-8313-10a8a33ec55d" />
<img width="741" height="566" alt="Screenshot 2026-08-11 103321" src="https://github.com/user-attachments/assets/22633c06-a7a3-4e00-9e4f-9e124d800563" />
<img width="822" height="527" alt="Screenshot 2026-08-11 103330" src="https://github.com/user-attachments/assets/5987c21c-bfcd-4614-8c68-a7cc83c3a3d0" />
<img width="780" height="576" alt="Screenshot 2026-08-11 103408" src="https://github.com/user-attachments/assets/e2199d10-9de4-4235-930f-951e229fa279" />
<img width="806" height="555" alt="Screenshot 2026-08-11 103426" src="https://github.com/user-attachments/assets/eec6d37e-6366-4c9c-8863-2ef02d19a91e" />
<img width="860" height="641" alt="Screenshot 2026-08-11 103450" src="https://github.com/user-attachments/assets/3bdb1985-f0db-45e5-8984-7ae8e2e07029" />


 # Author

S. Naranjana

II BCA -"A"

Kamaraj college (Face Prep Campus)


