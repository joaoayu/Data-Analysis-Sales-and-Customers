# Data-Analysis-Sales-and-Customers
This project focuses on analyzing sales data to extract valuable insights about product performance, customer behavior, and sales trends across different regions. The goal is to provide meaningful visualizations and reports that can assist in decision-making processes for businesses in the retail industry.<BR>
Dataset: https://www.kaggle.com/datasets/carrie1/ecommerce-data?resource=download

## Repository Structure
The repository is organized as follows:<br>
project-root/<br>
│<br>
├── src/                # Source code for data analysis<br>
├── data/               # Raw and processed data<br>
├── docs/               # Documentation and visualizations<br>

## Environment Setup
> [!TIP]
> If you're using Google Colab, simply execute the code cells to install the dependencies.

#### To run this project, follow these steps:
1. Clone the Repository
First, clone the repository to your local machine or create a new environment in Google Colab to work with the scripts and notebooks:
Use:
```
git clone https://github.com/your-username/repository-name.git
```

3. Install Dependencies
This project doesn't have a requirements.txt, but you can install the necessary libraries manually. Here are the libraries you need:
```
pip install pandas matplotlib oracledb
```

4. Load the Data
If you have the CSV file with the data, upload it to Google Colab or place it in the data/ folder if you're working locally.

```
import pandas as pd

# Replace with the correct file path
data = pd.read_csv('data/your_file.csv')

# Calculate TotalValue
data['TotalValue'] = data['Quantity'] * data['UnitPrice']
```

## Step-by-Step Execution
1. Load the Data
Once you have the data ready, the first step is to load it into a DataFrame.

2. Perform Data Analysis
The scripts and notebooks in the src/ folder contain the analyses. Below are the main steps you can execute:
```
#Top 10 Best-Selling Products
best_selling_products = data.groupby('Description')['Quantity'].sum().sort_values(ascending=False).head(10)
best_selling_products.plot(kind='bar', color='green')

#Top 10 Most Valuable Customers
most_valuable_customers = data.groupby('CustomerID')['TotalValue'].sum().sort_values(ascending=False).head(10)
most_valuable_customers.plot(kind='bar', color='blue')

#Monthly Sales
data['InvoiceDate'] = pd.to_datetime(data['InvoiceDate'])
monthly_sales = data.groupby(data['InvoiceDate'].dt.to_period('M'))['TotalValue'].sum()
monthly_sales.plot(kind='line')

```

## Description of Analyses and Decisions
1. Top 10 Best-Selling Products<br>
The analysis of the top-selling products aims to identify which products generated the most sales volume. The quantity of each product is summed, and the top 10 are selected.<br>

### Decisions Taken:

Duplicate products were handled to ensure accurate counting.<br>
A bar chart was used for easy visualization.<br>
2. Top 10 Most Valuable Customers<br>
We analyzed the customers with the highest purchase volume by summing the value of all their purchases.<br>

### Decisions Taken:

Only customers with valid purchases were considered.<br>
A bar chart was chosen to represent the most valuable customers.<br>
3. Monthly Sales<br>
The data was grouped by month, and the total sales for each month were calculated to identify monthly trends.<br>

### Decisions Taken:

The InvoiceDate column was converted to the datetime type.<br>
A line chart was used to show sales over time.<br>
4. Sales by Country<br>
The data was grouped by country to analyze which countries generated the most sales.<br>

### Decisions Taken:

The Country column was used for the analysis.<br>
A bar chart was chosen to compare sales across countries.<br>
