# E-commerce Dataset Analysis

## Project Overview
This project analyzes an e-commerce dataset containing 5,000 orders from different customers across various cities in Egypt. The dataset includes information such as customer demographics, product categories, quantities, prices, payment methods, and order dates.

The main goal is to explore sales patterns, customer behavior, and key metrics for better business insights.

---

## Dataset Description
The dataset (`ecommerce_dataset.csv`) contains 11 columns:

| Column | Description |
|--------|-------------|
| `order_id` | Unique identifier for each order |
| `customer_id` | Unique identifier for each customer |
| `gender` | Customer's gender (`Male` or `Female`) |
| `age` | Customer's age |
| `city` | Customer's city |
| `product_category` | Category of the purchased product (`Books`, `Clothing`, `Electronics`, `Home`, `Sports`) |
| `product_price` | Price of a single product |
| `quantity` | Number of products purchased in the order |
| `payment_method` | Payment method used (`Cash`, `Credit Card`, `Debit Card`) |
| `order_date` | Date of the order |
| `total_amount` | Total amount of the order (product_price * quantity) |

---

## Key Insights

- Total customers: **989 unique customers**  
- Top 5 cities by number of orders: **Mansoura, Aswan, Giza, Cairo, Alexandria**  
- Average quantity per order by city ranges from ~2.98 to ~3.08  
- Most used payment method: **Debit Card**  
- Month with highest total sales: **July**  
- Customer segmentation based on total spending:
  - **Low**
  - **Medium**
  - **High**
- Total sales by gender are almost equal:
  - Female: 19,662,741.58  
  - Male: 19,560,510.21  

---

## Data Processing Steps

- Converted `order_date` to datetime type and extracted `month` and `year`  
- Categorized customers by `age_group` into 3 intervals  
- Computed customer lifetime value (`CLV`) and segmented customers based on total spending  

---

## Libraries Used
- `pandas`  
- `numpy`  

---

## Usage
```python
import pandas as pd
import numpy as np

df = pd.read_csv("ecommerce_dataset.csv")
# Example: Get top 10 customers by total spending
top_customers = df.groupby("customer_id")["total_amount"].sum().sort_values(ascending=False).head(10)
print(top_customers)
