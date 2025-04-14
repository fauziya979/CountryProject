# 🇺🇸 USA Online Retail Data Analysis

## 📊 Project Overview

This Jupyter Notebook analyzes online retail transactions **specific to the United States (USA)**. It leverages the `pandas` library to filter data, explore product trends, and visualize monthly sales activity.

The analysis is based on a dataset titled:

**`dat.xlsx - Online Retail.csv`**

This dataset contain transaction-level data from an e-commerce or wholesale retail platform.

---

## 📁 Dataset Summary

The dataset includes the following typical columns:

- `InvoiceNo`: Unique identifier for each transaction  
- `StockCode`: Product identifier  
- `Description`: Product name  
- `Quantity`: Number of units purchased  
- `InvoiceDate`: Date and time of purchase  
- `UnitPrice`: Price per unit  
- `CustomerID`: Unique identifier for each customer  
- `Country`: Customer’s country  

---

## 🛠️ Analysis Workflow

### 1. **Importing and Loading Data**

```python
import pandas as pd
messy = pd.read_csv("dat.xlsx - Online Retail.csv")


2. Filtering Transactions by Country (USA)
python
Copy
Edit
Country = "Country"
target_USA = "USA"
usa = messy[messy[Country] == target_USA]


3. Exploring the Data
python
Copy
Edit
usa.head()
usa.describe()


4. Product Popularity Analysis
a. Most Frequently Ordered Products
python
Copy
Edit
usa["Description"].value_counts()
b. Top 10 Product Descriptions by Count
python
Copy
Edit
usa["Description"].value_counts().head(10).plot(kind='barh')
c. Top 10 Products by Quantity Sold
python
Copy
Edit
usa.groupby("Description")["Quantity"].sum().sort_values(ascending=False).head(10).plot(kind="bar")



5. Time Series Sales Trend
python
Copy
Edit
usa["InvoiceDate"] = pd.to_datetime(usa["InvoiceDate"])
usa.set_index("InvoiceDate", inplace=True)
usa.resample("M").sum(numeric_only=True)["Quantity"].plot()


📈 Visual Insights Summary
Visualization	Description
📊 Top Products (Bar Chart)	Highlights most commonly purchased items in the USA
📦 Top Quantity Sellers	Shows which products sold the most units
📆 Monthly Sales Line Chart	Visualizes how USA sales quantities changed over time
🔍 Key Takeaways
Popular Products: Some items appear frequently but may not have the highest quantity sold.


Sales Trends: Monthly sales trend reveals patterns—useful for forecasting.

Simple Yet Insightful: The notebook uses basic but effective tools to extract meaningful insights.









