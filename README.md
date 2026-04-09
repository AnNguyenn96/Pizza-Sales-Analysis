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


Power BI/Page 1 Sales Analysis .png

## 📈 Business Insights

## 🎯 Overall Problem Statement  
How can the business understand sales performance, customer behavior, and product demand to optimize revenue and operations?

---

## 🔍 Sales Trends & Anomalies  

<p align="center">
    <img src="Power BI/Page 1 Sales Analysis .png" alt="Employee Analysis" style="border-radius: 10px;">
    </br>
    Sales Trends & Anomalies 
</p>

### 🎯 Objective  
Analyze sales performance over time and identify patterns or anomalies.

### 💡 Key Insights
- Total revenue reached **$817.86K** from **21K orders** and **50K pizzas sold** in 2015.  
- Daily revenue remains stable at approximately **$2K–$3K**, with occasional spikes above **$4K**.  
- Monthly revenue ranges from **$64K to $72.6K**, indicating moderate variability with no strong seasonality.  
- Peak demand occurs during:
  - **12–3 PM (~6.4K orders)**  
  - **6–9 PM (~6.1K orders)**  
- Fridays show the highest demand (~**3.5K orders**), highlighting strong end-of-week consumption.  
- Holidays such as New Year and Easter generate higher-than-average sales (~**$2.6K–$2.7K per event**).
- Sales anomalies are likely driven by seasonal factors, promotions, and customer behavior during major holidays.

### 📌 Recommendations  

| Area | Action |
|------|--------|
| Demand Planning | Increase staffing during lunch and dinner peak hours |
| Marketing Strategy | Run promotions during high-demand periods |
| Holiday Planning | Prepare inventory and campaigns around key holidays |
---
## 🍕 Product Performance & Customer Ordering Patterns  

<p align="center">
    <img src="Power BI/Page 1 Sales Analysis .png" alt="Employee Analysis" style="border-radius: 10px;">
    </br>
    Operational & Product Analysis
</p>

### 🎯 Objective  
Evaluate product performance and understand how pricing, size, and customer behavior influence sales.


### 💡 Key Insights
- Large and extra-large pizzas dominate demand:
  - Example: Classic XL size recorded **6,139 orders**, significantly higher than smaller sizes.  
- Strong negative correlation (**-0.95**) between price and sales volume:
  - Higher-priced categories (~$17–$18) sell less than lower-priced (~$14–$15).  
- Category performance:
  - **Classic:** ~$220K revenue (highest)  
  - **Supreme:** ~$208K  
  - **Chicken:** ~$195K  
  - **Veggie:** ~$193K  
- Multi-item orders dominate customer behavior:
  - **13K multi-item (~62%) vs 8K single-item (~38%)**  
- Average time between orders is **~11 minutes**, indicating consistent demand flow.

  
### 📌 Recommendations  

| Area | Action |
|------|--------|
| Pricing Strategy | Optimize pricing to balance demand and margin |
| Product Strategy | Focus on high-demand sizes (M, L, XL) |
| Sales Strategy | Introduce combo deals to increase order value |
| Operations | Maintain consistent kitchen capacity to handle demand |

---

## 🏆 Product Ranking & Performance  


<p align="center">
    <img src="Power BI/Page 1 Sales Analysis .png" alt="Employee Analysis" style="border-radius: 10px;">
    </br>
    Operational & Product Analysis
</p>

### 🎯 Objective  
Identify top-performing and underperforming products to optimize the menu.


### 💡 Key Insights
- Top pizzas by quantity:
  - Classic Deluxe (~**2,453 orders**)  
  - Barbecue Chicken (~**2,432 orders**)  
  - Hawaiian (~**2,422 orders**)  
- Top pizzas by revenue:
  - Thai Chicken (~**$43K**)  
  - Barbecue Chicken (~**$43K**)  
  - California Chicken (~**$41K**)  
- Bottom performer:
  - Brie Carre Pizza (~**490 orders**, ~$**12K revenue**)  
- Some pizzas show high volume but lower revenue → pricing inefficiency.

### 📌 Recommendations  

| Area | Action |
|------|--------|
| Menu Optimization | Promote top-performing pizzas |
| Product Strategy | Review or remove low-performing items |
| Pricing Strategy | Adjust pricing for high-volume low-revenue products |

---

## 🧂 Ingredient Analysis  

### 🎯 Objective  
Understand ingredient popularity and its contribution to sales.

### 💡 Key Insights
- Most popular ingredients:
  - Garlic (~**27K units**)  
  - Tomatoes (~**27K units**)  
  - Red onions (~**20K units**)  
- Least popular ingredients:
  - Brie Carre Cheese (~**480 units**)  
  - Pears (~**480 units**)  
- Sales are heavily driven by familiar, mainstream ingredients, while niche ingredients contribute minimally.


### 📌 Recommendations  

| Area | Action |
|------|--------|
| Ingredient Strategy | Focus on high-demand ingredients |
| Cost Optimization | Reduce low-performing ingredients |
| Product Innovation | Develop new pizzas based on popular ingredients |


## 🎯 Final Impact  

This dashboard provides insights into sales trends, customer behavior, and product performance, enabling the business to optimize pricing, improve product strategy, and enhance operational efficiency.
---
