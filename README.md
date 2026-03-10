# Python List and Dictionary Comprehension
==========================================

This repository contains examples and exercises for learning **Python List Comprehension** and **Dictionary Comprehension**.

---

## List Comprehension

### Q1: Convert Celsius to Fahrenheit

Given this list of temperatures in Celsius:
>celsius_temps = [0, 20, 37, 100, -10, 15]

Write a list comprehension to convert them to Fahrenheit using the formula:  F = (C × 9/5) + 32

  #### Solution
  ```python
celsius_temps = [0, 20, 37, 100, -10, 15]

Fahrenheit  = [(x * 9/5) + 32 for x in celsius_temps]
print(Fahrenheit )
```
#### Output
> [32.0, 68.0, 98.6, 212.0, 14.0, 59.0]

### Q2: You have a list of customer ages:
> ages = [25, 42, 17, 30, 65, 19, 21, 55, 16]

Create a list comprehension that keeps only ages 18 and older.
#### Solution
``` python
ages = [25, 42, 17, 30, 65, 19, 21, 55, 16]
age_above_18=[age for age in ages if age >=18]
print(age_above_18)
```
#### Output
>  [25, 42, 30, 65, 19, 21, 55]

### Q3: You're analyzing sales data:
> sales = [1250, 890, 2100, 540, 3100, 980]

Create a list comprehension that returns "High" for sales > 1500, "Medium" for sales between 500-1500, and "Low" for sales < 500
#### Solution
``` python
sales = [1250, 890, 2100, 540, 3100, 980]
sale_analysis=[    "High" if sale > 1500 
    else "Medium" if 500 <= sale <= 1500 
    else "Low"
    for sale in sales]
print(sale_analysis)
```
#### Output
> ['Medium', 'Medium', 'High', 'Medium', 'High', 'Medium']

### Q4: Given this list of strings:
> products = ["laptop", "mouse", "keyboard", "monitor", "printer"]

Create a list comprehension that returns each product name capitalized and with " - In Stock" appended.
#### Solution
``` python
products = ["laptop", "mouse", "keyboard", "monitor", "printer"]
instock_product = [product.upper() +"-In Stock" for product in products]
print(instock_product)
```
#### Output
> ['LAPTOP-In Stock', 'MOUSE-In Stock', 'KEYBOARD-In Stock', 'MONITOR-In Stock', 'PRINTER-In Stock']

### Q5: You have a list with mixed data types:
> data = [10, "20", 30.5, "invalid", 40, "50.5", "error"]

Write a list comprehension that converts only the numeric strings to floats, leaving non-numeric strings as they are.
#### Solution
``` python
data = [10, "20", 30.5, "invalid", 40, "50.5", "error"]
data_conversion=[float(x) if isinstance(x, str) and x.replace('.', '', 1).isdigit() else x for x in data]
print(data_conversion)
```
#### Output
> [10, 20.0, 30.5, 'invalid', 40, 50.5, 'error']


## Dictionary  Comprehension

### Q6: You have two lists:
> products = ["laptop", "mouse", "keyboard", "monitor"]
> prices = [999.99, 29.99, 79.99, 299.99]

Create a dictionary comprehension that pairs each product with its price.
#### Solution
``` python
products = ["laptop", "mouse", "keyboard", "monitor"]
prices = [999.99, 29.99, 79.99, 299.99]
product_items ={p:pr for p,pr in zip(products,prices)}
print(product_items)
```
#### Output
> {'laptop': 999.99, 'mouse': 29.99, 'keyboard': 79.99, 'monitor': 299.99}

### Q7: Using the dictionary from Q6, create a new dictionary with 15% discount applied only to items priced above $100.
#### Solution
``` python
discount_items ={p:pr*0.15 for p,pr in product_items.items() if pr >100}
print(discount_items)
```
#### Output
> {'laptop': 149.9985, 'monitor': 44.9985}

### Q8: From the sales_data list in your example:
Create a dictionary comprehension that shows for each product:
> Key: product name
> Value: tuple containing (price, units, revenue)
#### Solution
``` python
units =[1,4,6,8]
sales_data= {p:(pr,u,u*pr) for p,u,pr in zip(products,prices,units)}
print(sales_data)
```
#### Output
> {'laptop': (1, 999.99, 999.99), 'mouse': (4, 29.99, 119.96), 'keyboard': (6, 79.99, 479.93999999999994), 'monitor': (8, 299.99, 2399.92)}

### Q9: You have a dictionary of student names and their scores:
> scores = {"Alice": 88, "Bob": 72, "Charlie": 95, "Diana": 81}
Create a new dictionary that shows letter grades:
```
 A for scores ≥ 90
 B for scores 80-89
 C for scores 70-79
D for scores < 70
```
#### Solution
``` python
scores = {"Alice": 88, "Bob": 72, "Charlie": 95, "Diana": 81}
grades ={ name: "A" if G >= 90 else
          "B" if 80 <= G <= 89 else
          "C" if 70 <= G <= 79 else
          "D"for name,G in scores.items() } 
print(grades)
```
#### Output
> {'Alice': 'B', 'Bob': 'C', 'Charlie': 'A', 'Diana': 'B'}

### Q10: Given this list of employee data dictionaries:
```
employees = [
    {"name": "John", "hours": 45, "rate": 25.50},
    {"name": "Sarah", "hours": 40, "rate": 32.00},
    {"name": "Mike", "hours": 50, "rate": 28.75}> ]
```
Create a dictionary comprehension where:
> 
> Key: employee name
> Value: total pay (hours × rate) with overtime pay (1.5× rate) for hours over 40

#### Solution
``` python
employees = [
    {"name": "John", "hours": 45, "rate": 25.50},
    {"name": "Sarah", "hours": 40, "rate": 32.00},
    {"name": "Mike", "hours": 50, "rate": 28.75}
]
employee_report = {
    e["name"]: e["hours"] * e["rate"] if e["hours"] <= 40 else
                40 * e["rate"] + (e["hours"] - 40) * e["rate"] * 1.5
    for e in employees
}

print(employee_report)
```
#### Output
> {'John': 1211.25, 'Sarah': 1280.0, 'Mike': 1581.25}


## Combined  Comprehension

### Q11: Using the sales_data list from your example, create a list comprehension that returns only the products with revenue greater than $300.
#### Solution
``` python
product_item_list = list(product_items.items())
highest_revenue = [x[0] for x in product_item_list if x[1] >300]
print(highest_revenue)
```
#### Output
> ['laptop']

Q12: Create a dictionary from the sales_data where:

> Key: product name
> Value: percentage of total revenue that product contributes
#### Solution
``` python
total_revenue =sum(v[2] for v in sales_data.values())
print(f"total_revenue:{total_revenue}")
revenue_percentage = {
    product: (data[2] / total_revenue) * 100
    for product, data in sales_data.items()
}
print(f"revenue_percentage:{revenue_percentage}")

```
#### Output
> total_revenue:3999.81
revenue_percentage:{'laptop': 25.000937544533365, 'mouse': 2.9991424592668148, 'keyboard': 11.9990699558229, 'monitor': 60.00085004037692}

### Q13: Given this data:
```
customers = [
    {"name": "Alice", "purchases": [50, 125, 75]},
    {"name": "Bob", "purchases": [200, 50]},
    {"name": "Charlie", "purchases": [300, 150, 100, 50]}
]
```
Create a dictionary comprehension where:

> Key: customer name
> Value: total amount spent

#### Solution
``` python
customers = [
    {"name": "Alice", "purchases": [50, 125, 75]},
    {"name": "Bob", "purchases": [200, 50]},
    {"name": "Charlie", "purchases": [300, 150, 100, 50]}
]

amount_spent ={c["name"]:sum(c["purchases"]) for c in customers}
print(amount_spent)
```
#### Output
>  {'Alice': 250, 'Bob': 250, 'Charlie': 600}
### Q14: From the customers list in Q13, create a list comprehension that returns customer names who have spent more than $400 in total.

#### Solution
``` python
customer_list = list(amount_spent.items())
highest_customer_spent = [x[0] for x in customer_list if x[1] >400]
highest_customer_spent
```
#### Output
> ['Charlie']

### Q15: You're analyzing website traffic data:
```
daily_visitors = {
    "Monday": [1200, 1100, 1300, 1400],
    "Tuesday": [1000, 900, 1100, 1200],
    "Wednesday": [1500, 1400, 1600, 1700]
}
```
Create a dictionary comprehension that shows for each day:

> Key: day name
> Value: average visitors (sum/4)

#### Solution
``` python
daily_visitors = {
    "Monday": [1200, 1100, 1300, 1400],
    "Tuesday": [1000, 900, 1100, 1200],
    "Wednesday": [1500, 1400, 1600, 1700]
}
avg_day = {d:sum(v)/4 for d,v in daily_visitors.items()}
avg_day
```
#### Output
> {'Monday': 1250.0, 'Tuesday': 1050.0, 'Wednesday': 1550.0}

### Q16: The company is running a promotion: "Buy 2, get 1 free" on all items.
Using your original sales_data, calculate the new revenue if this promotion was applied to all sales.
#### Solution
``` python
promo_revenue = {
    product: (units - units//3) * price
    for product, (units, price, revenue) in sales_data.items()
}

print(promo_revenue)
```
#### Output
> {'laptop': 999.99, 'mouse': 89.97, 'keyboard': 319.96, 'monitor': 1799.94}

### Q17: You need to create an inventory report that shows:

- Products sorted by profitability (revenue per unit sold)
-  Mark each product as "Restock Needed" if units sold > 10
#### Solution
``` python

inventory_report = {
    p: {
        "profit_per_unit": r/u,
        "status": "Restock Needed" if u > 10 else "Stock OK"
    }
    for p,(u,pr,r) in sales_data.items()
}

sorted_inventory = dict(
    sorted(inventory_report.items(),
    key=lambda x: x[1]["profit_per_unit"],
    reverse=True)
)

print(sorted_inventory)
```
#### Output
> {'laptop': {'profit_per_unit': 999.99, 'status': 'Stock OK'}, 'monitor': {'profit_per_unit': 299.99, 'status': 'Stock OK'}, 'keyboard': {'profit_per_unit': 79.99, 'status': 'Stock OK'}, 'mouse': {'profit_per_unit': 29.99, 'status': 'Stock OK'}}

### Q18: Create a comprehensive sales summary dictionary using only comprehensions that includes:
- Total revenue for each product
- Average price across all products
-  Total units sold
-  Most profitable product
-  list of products that need restocking (units > 10)

#### Solution
``` python
#Report Summary
summarry ={
    "Revenue_PerProduct":{p:r for p,(u,pr,r) in sales_data.items()},
    "average_price":sum(pr for _,(_,pr,_)in sales_data.items())/len(sales_data),
    "total_units": sum(u for _,(u,_,_) in sales_data.items()),
    "most_profitable": max(sales_data, key=lambda x: sales_data[x][2]),
    "restock_list": [p for p,(u,_,_) in sales_data.items() if u > 10]
}

print(summarry)
```
#### Output
> {'Revenue_PerProduct': {'laptop': 999.99, 'mouse': 119.96, 'keyboard': 479.93999999999994, 'monitor': 2399.92}, 'average_price': 352.49, 'total_units': 19, 'most_profitable': 'monitor', 'restock_list': []}
### Q19: Write a single dictionary comprehension that transforms sales_data into:
  ``` javascript
{
    "Laptop": {
        "price": 999.99,
        "units": 5,
        "revenue": 4999.95,
        "category": "Electronics"
    },
    # ... and so on for other products
}
```
(Assume categories: Laptop="Electronics", Mouse="Accessories", Keyboard="Accessories", Monitor="Electronics")

#### Solution
``` python
categories = {
    "laptop":"Electronics",
    "mouse":"Accessories",
    "keyboard":"Accessories",
    "monitor":"Electronics"
}

transformed = {
    p.capitalize():{
        "price":price,
        "units":units,
        "revenue":revenue,
        "category":categories[p]
    }
    for p,(units,price,revenue) in sales_data.items()
}

print(transformed)
```
#### Output
> {'Laptop': {'price': 999.99, 'units': 1, 'revenue': 999.99, 'category': 'Electronics'}, 'Mouse': {'price': 29.99, 'units': 4, 'revenue': 119.96, 'category': 'Accessories'}, 'Keyboard': {'price': 79.99, 'units': 6, 'revenue': 479.93999999999994, 'category': 'Accessories'}, 'Monitor': {'price': 299.99, 'units': 8, 'revenue': 2399.92, 'category': 'Electronics'}}

### Q20: Create a function that takes any sales data list and returns a complete analysis using comprehensions only. The function should return a dictionary with all the metrics you've calculated.

#### Solution
``` python
def analyze_sales(data):

    return {
        "revenue_per_product": {p:r for p,(u,pr,r) in data.items()},

        "profit_per_unit": {p:r/u for p,(u,pr,r) in data.items()},

        "promotion_revenue": {
            p:(u-u//3)*pr for p,(u,pr,r) in data.items()
        },

        "total_units": sum(u for _,(u,_,_) in data.items()),

        "total_revenue": sum(r for _,(_,_,r) in data.items()),

        "average_price": sum(pr for _,(_,pr,_) in data.items())/len(data),

        "most_profitable_product": max(data,key=lambda x:data[x][2]),

        "restock_needed":[p for p,(u,_,_) in data.items() if u>10]
    }
report = analyze_sales(sales_data)
print(report)
```
#### Output
> {'revenue_per_product': {'laptop': 999.99, 'mouse': 119.96, 'keyboard': 479.93999999999994, 'monitor': 2399.92}, 'profit_per_unit': {'laptop': 999.99, 'mouse': 29.99, 'keyboard': 79.99, 'monitor': 299.99}, 'promotion_revenue': {'laptop': 999.99, 'mouse': 89.97, 'keyboard': 319.96, 'monitor': 1799.94}, 'total_units': 19, 'total_revenue': 3999.81, 'average_price': 352.49, 'most_profitable_product': 'monitor', 'restock_needed': []}




