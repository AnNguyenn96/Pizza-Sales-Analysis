## 🍕 Pizza Sales Dashboard

This project focuses on analyzing historical pizza sales data to generate actionable insights that support business decision-making in sales, operations, and product strategy.

---

## 📑 Table of Contents
- 🍕 [Pizza Sales Dashboard](#-pizza-sales-dashboard)
- 📊 [Data Source](#-data-source)
- 🏗️ [Architecture](#-architecture)
- 🧠 [Data Model](#-data-model)
- 📈 [Business Insights](#-business-insights)

---

 

## 🧠 Data Model

The dataset was transformed from a denormalized flat file into a structured star schema to support efficient analysis.

The model consists of:

- **Fact Table**:
  - `Pizza_Sales`: Stores transactional sales data including order ID, pizza ID, price, and order type  

- **Supporting Fact Table**:
  - `Pizza_SaleVolume`: Aggregated table used for category-level volume analysis  

- **Dimension Tables**:
  - `Dim_Date`: Date attributes (day, day of week, holiday flags) for time-based analysis  
  - `DimPizza`: Pizza details including name, category, and size  
  - `Dim_Pizza_Ingredient`: Ingredient-level data for ingredient analysis  
  - `Orders`: Order-level information including order datetime, total items, and time intervals  

This structure enables flexible analysis across multiple dimensions such as time, product, customer behavior, and ingredients.
              
## 🧠 Semantic Model

<p align="center">
    <img src="Power BI/Pizza Sales Data Model.png" alt="powerbi" style="border-radius: 10px;">
    </br>
  Power BI Semantic Model
</p>


### 🔗 Defined Relationships

| From Table (Column)                  | Relationship Type | To Table (Column)                  |
| ----------------------------------- | ----------------- | ---------------------------------- |
| `Dim_Date(Date)`                    | One to Many       | `Pizza_Sales(date)`                |
| `Dim_Date(Date)`                    | One to Many       | `Pizza_SaleVolume(date)`           |
| `Orders(order_id)`                  | One to Many       | `Pizza_Sales(order_id)`            |
| `DimPizza(pizza_id)`                | One to Many       | `Pizza_Sales(pizza_id)`            |
| `DimPizza(category)`                | One to Many       | `Pizza_SaleVolume(category)`       |
| `Dim_Pizza_Ingredient(Ingredients_ID)` | One to Many    | `Pizza_SaleVolume(Ingredients_ID)` |

> 📌 Note:  
> - `Pizza_Sales` is the main transaction fact table used for revenue, quantity, and order-level analysis.  
> - `Pizza_SaleVolume` is a supporting fact table designed for category and ingredient-level volume analysis.  
> - `Orders` enables order frequency and turnaround-time analysis.  
> - `Dim_Date`, `DimPizza`, and `Dim_Pizza_Ingredient` provide time, product, and ingredient dimensions for slicing and drill-down.
## 📈 Business Insights
---
