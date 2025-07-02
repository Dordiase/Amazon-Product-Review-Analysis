
# 📦 Amazon Product Review Analysis

This project presents an **Exploratory Data Analysis (EDA)** on an Amazon product review dataset using **Microsoft Excel**. The analysis was conducted as part of a data analytics case study to extract insights into product performance, customer engagement, and revenue generation.

---

## 🧠 Project Objective

To uncover actionable insights from Amazon product data through:
- Cleaning and transforming raw data
- Analyzing customer ratings, reviews, discounts, and pricing
- Visualizing patterns and trends using Excel dashboards

---

## 📁 Dataset Overview

- **Total Records:** 1,465
- **Total Columns:** 16
- **Source:** Web-scraped Amazon product listing data

Key fields include:
- `product_name`, `category`, `actual_price`, `discounted_price`
- `rating`, `rating_count`, `discount_perc`
- `review_title`, `review_content`, and product metadata

---

## 🧹 Data Cleaning & Transformation Steps

1. **Duplicate the Raw Sheet** for safe editing.
2. **Check for and Remove Duplicates** using product_id or product_name.
3. **Drop Unnecessary Columns**:  
   (`review_id`, `user_name`, `review_content`, `img_link`, etc.)
4. **Create `clean_category` Column**:  
   Used `SEARCH()` & `IF()` functions to standardize product categories.
5. **Check Data Types** for consistency across numeric and text fields.
6. **Create New Columns for Deeper Analysis**:
   - `revenue` = `actual_price * rating_count`
   - `price_bucket` using `IF()`:
     ```excel
     =IF(actual_price<200,"<₹200", IF(actual_price<=500,"₹200–₹500", ">₹500"))
     ```
   - `high_discount` (>= 50%):
     ```excel
     =IF(discount_perc>=0.5, "Yes", "No")
     ```
   - `low_rating_count` (<1000):
     ```excel
     =IF(rating_count<1000, "Yes", "No")
     ```
   - `rating_score` = `rating * rating_count` (used to find top 5 products)

7. **Create a Cleaned Sheet** (`amazon_cleaned`) for final pivot/dash work
8. **Duplicate Cleaned Sheet and Remove Category Column** (optional modeling)

---

## 📊 Dashboard Visualizations

The following visuals were created using Excel's built-in charting tools:

| Visualization | Chart Type |
|---------------|------------|
| Number of Products by Category | Bar Chart |
| Distribution of Ratings | Column Chart |
| Product Categories with Highest Discounts | Pie Chart |
| Ratings vs Discount Percentage | Scatter Plot |
| Total Review Count per Category | Column Chart |
| Avg Actual vs Discounted Price by Category | Clustered Bar Chart |
| Revenue by Product Category | Column Chart |
| Price Bucket Filter | Slicer |
| Product Category Filter | Slicer |

---

## 🧩 Key Insights

- **Top Categories by Volume**: Home & Kitchen and Electronics
- **Categories with Highest Discounts**: Electronics, Office Supplies
- **Rating Patterns**: Most products are clustered around 3.5–4.5 stars
- **Low Engagement Products**: Over 50% of products have <1000 reviews
- **Top 5 Products** (by rating * rating_count) show both high quality and high volume
- **Revenue Trends**: Certain low-cost items with high rating count generated high potential revenue

---

## 📦 Tools Used

- **Microsoft Excel**
  - Pivot Tables
  - Excel Formulas (IF, SEARCH, ROUND)
  - Charts & Slicers
- **GitHub** for version control and portfolio hosting

---

## 📁 Repository Structure

📂 amazon-product-review-analysis/

├── Amazon_Project_Cleaned.xlsx

├── screenshots/

│ └── dashboard.png

└── README.md
