# 🛒 Zepto Product Data — SQL Analysis Project

A end-to-end SQL project analysing Zepto's product catalogue — covering data exploration, cleaning, and business-focused queries to uncover pricing, inventory, and discount trends.

---

## 📁 Project Structure

```
zepto-sql-analysis/
├── zepto.csv         
├── zepto.sql
├── README.md
├── Outputs        
└── LICENSE
```

---

## 🗂️ Dataset Overview

The dataset contains product-level SKU data scraped from Zepto's catalogue across multiple categories.

| Column | Description |
|---|---|
| `sku_id` | Unique product identifier (Primary Key) |
| `category` | Product category (e.g. Fruits & Vegetables, Snacks) |
| `name` | Product name |
| `mrp` | Maximum Retail Price (in paise → converted to ₹) |
| `discountPercent` | Discount offered (%) |
| `availableQuantity` | Units currently in stock |
| `discountedSellingPrice` | Final price after discount |
| `weightInGms` | Product weight in grams |
| `outOfStock` | Boolean — whether the product is out of stock |
| `quantity` | Pack size / quantity |

---

## 🧰 Tools Used

- **PostgreSQL** — all queries written and tested in PostgreSQL
- **pgAdmin / psql** — query execution environment

---

## 🔍 Project Workflow

### 1. Table Creation
Defined schema with appropriate data types, constraints, and a serial primary key.

### 2. Data Exploration
- Counted total rows and checked for NULL values
- Identified distinct product categories
- Compared in-stock vs out-of-stock product counts
- Found product names with multiple SKUs (e.g. different pack sizes)

### 3. Data Cleaning
- Removed rows where `mrp = 0` (invalid/corrupt entries)
- **Converted prices from paise to rupees** by dividing `mrp` and `discountedSellingPrice` by 100

### 4. Business Problem Solving (8 Queries)
See the [SQL file](zepto.sql) for full queries.

---

## 📊 Business Questions Answered

| # | Question |
|---|---|
| Q1 | Top 10 best-value products by discount % |
| Q2 | High MRP products that are currently out of stock |
| Q3 | Estimated revenue per category |
| Q4 | Premium products (MRP > ₹500) with low discounts (<10%) |
| Q5 | Top 5 categories by average discount offered |
| Q6 | Best price-per-gram products (above 100g) |
| Q7 | Products grouped into Low / Medium / Bulk weight categories |
| Q8 | Total inventory weight per category |

---

## 💡 Key Insights

### 🏷️ Discounts
- **Health & Hygiene** and **Snacks & Beverages** categories tend to offer the highest average discounts, often exceeding 15–20% on select products.
- Some products carry **0% discount** despite high MRPs — particularly in Cooking Essentials (oils, ghee, atta), indicating lower price sensitivity in staples.
- The top discounted SKUs reach up to **50% off** (e.g. Epigamia Fruit Yogurts) — likely used as acquisition or trial-driving offers.

### 📦 Inventory & Stock
- A significant portion of SKUs are marked **out of stock**, particularly in Fruits & Vegetables and Health & Hygiene — suggesting high demand or supply chain gaps.
- Several **high-MRP products (>₹300)** are out of stock, representing potential lost revenue opportunities.
- Many product names appear **multiple times** as separate SKUs, differing by pack size (e.g. Onion 1kg vs 3kg) — a standard quick-commerce bundling strategy.

### 💰 Revenue
- **Cooking Essentials** and **Snacks & Beverages** are the highest estimated revenue-generating categories due to high available quantities and consistent pricing.
- Categories like **Fruits & Vegetables**, despite high transaction volume, have lower per-unit prices, contributing moderate estimated revenue.

### ⚖️ Price Per Gram
- Spices and specialty items (e.g. Saffron, certain herbs) have the **highest price per gram**, while staples like flour, oil, and pulses offer the **best value per gram**.
- Bulk SKUs consistently offer better per-gram pricing, confirming the value proposition of larger pack sizes.

### 🗂️ Weight Distribution
- Most products fall in the **Low (<1kg)** weight bucket — typical of quick-commerce where small, frequent purchases dominate.
- **Bulk (5kg+)** SKUs are limited to staples — atta, oil, and pulses — catering to planned monthly purchases.

---

## ⭐ Give a Star

If you found this project helpful or interesting, consider giving it a star — it means a lot and helps others discover it too!
