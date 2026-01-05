# 📊 Online Retail Pricing & Demand Analysis (2009–2011)

## 📌 Project Overview
This project analyzes transactional data from an online retail business using the **UCI Online Retail dataset (2009–2011)** to understand how **pricing, discounts, and customer behavior** affect **revenue, demand, and profitability**.

The analysis focuses on pricing effectiveness, demand sensitivity, and customer-level margin impact, moving beyond descriptive analytics to support **data-driven pricing and revenue decisions**.

---

## 🧠 Business Questions
1. Do discounts increase net revenue, or do they primarily lift sales volume?
2. Which products exhibit elastic vs inelastic demand?
3. Which customers destroy margin at scale due to heavy discount reliance?

---

## 📂 Data Source & Final Tables

**Source:**  
UCI Online Retail Dataset (December 2009 – December 2011)  
Transaction-level invoice data

### Final Tables
| Table | Description |
|------|------------|
| `fact_sales.csv` | Cleaned transaction-level sales data |
| `dim_product.csv` | Unique product dimension |
| `dim_customer.csv` | Unique customer dimension |

---

## 🧹 Data Cleaning & Preparation
- Removed cancelled invoices (Invoice starting with `"C"`)
- Removed returns (negative quantities)
- Dropped duplicate rows
- Standardized customer identifiers
- Engineered analytical fields:
  - Revenue
  - Discount percentage
  - YearMonth
  - Cancellation and return flags

Final data follows a **star-schema-style analytical structure** with one fact table and supporting dimensions.

---

## 📈 Analysis Summary

### 1️⃣ Discount Effectiveness
**Finding:**  
Discounts significantly increase sales volume, but revenue does not grow proportionally, especially at higher discount levels.

**Implication:**  
Deep discounts clear inventory but do not materially improve net revenue. Discounting should be **targeted and selective**, not blanket.

---

### 2️⃣ Product Price Elasticity
**Method:**  
Monthly product-level price and quantity panels were constructed and price elasticity was estimated using:

Δ log(Q) / Δ log(P)

**Findings:**
- Many high-revenue products are price elastic and respond strongly to price changes
- A subset of products is near-inelastic, indicating pricing power

**Implication:**  
Elasticity-aware pricing strategies can materially improve margins by avoiding unnecessary discounts on sensitive products.

---

### 3️⃣ Margin-Destroying Customers
**Approach:**  
A proxy cost model (cost = 60% of revenue) was applied and profitability was aggregated at customer level.

**Findings:**
- Identified high-revenue customers with heavy reliance on discounted purchases
- These customers generate volume but erode margins disproportionately

**Implication:**  
High revenue does not equal high value. Customer strategy should be guided by **discount-adjusted profitability**, not sales alone.

---

## 🧠 Key Insights
- Discounts should be applied where elasticity justifies them
- Inelastic products can sustain margin-accretive price increases
- Revenue is a misleading metric without profitability context
- Customer segmentation should incorporate margin behavior

---

## ⚠️ Limitations
- Costs modeled as a fixed percentage due to lack of SKU-level cost data
- Elasticity estimates are simplified and do not control for external factors
- Promotions inferred from price variation rather than explicit flags

---

## 🚀 Next Steps
- Introduce category-level pricing rules
- Implement regression-based elasticity models
- Incorporate customer lifetime value (CLV)
- Simulate optimized pricing and discount strategies

---

## 🛠 Tools Used
- **Python:** pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Environment:** Jupyter Notebook
