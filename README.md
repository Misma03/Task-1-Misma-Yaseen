# Project 1: Data Cleaning

**DecodeLabs Internship – Task 1**  
*Batch: 2026*

---

## 📌 Project Overview

The objective of this task is to clean a raw, messy e-commerce dataset containing **2,000+ order records**. Raw data often contains missing values, inconsistent formatting, and duplicates—which can skew analysis and lead to incorrect business decisions.

This project applies systematic data cleaning techniques using **Python (Pandas)** in a **Jupyter Notebook** environment to transform raw data into a consistent, analysis-ready format.

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **Python 3.x** | Core programming language |
| **Pandas** | Data manipulation and cleaning |
| **NumPy** | Numerical operations |
| **OpenPyXL** | Excel file reading/writing |
| **Jupyter Notebook** | Interactive development environment |

---

## 📂 Dataset Overview

The raw dataset consists of **2,000+ transactions** with the following columns:

| Column Name | Description |
|-------------|-------------|
| OrderID | Unique order identifier |
| Date | Order placement date |
| CustomerID | Unique customer identifier |
| Product | Product category purchased |
| Quantity | Number of units ordered |
| UnitPrice | Price per unit |
| ShippingAddress | Delivery location |
| PaymentMethod | Payment type used |
| OrderStatus | Current order status |
| TrackingNumber | Shipment tracking ID |
| ItemsInCart | Total items in cart |
| CouponCode | Promotional code applied |
| ReferralSource | Channel of acquisition |
| TotalPrice | Total order value |

---

## 🧹 Data Cleaning Methodology

The following cleaning procedures were applied sequentially to ensure data integrity.

### 1. Loading the Dataset

The raw Excel file was loaded into a Pandas DataFrame for processing.

```python
import pandas as pd
df = pd.read_excel('Dataset for Data Analytics.xlsx')
