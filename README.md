# Project 1: Data Cleaning & Preparation

Internship: DecodeLabs  Data Analytics Industrial Training (Batch 2026)

##  Objective
Clean a raw e-commerce orders dataset by handling missing values, duplicate records, and inconsistent data formats  turning raw, messy data into a reliable "source of truth" for downstream analysis (EDA, SQL, and Visualization projects).

##  Dataset
Input file: `Dataset_for_Data_Analytics.xlsx`
Output file: `Dataset_for_Analytics_CLEANED.xlsx`
Rows: 1,200 orders
Columns: 14 (OrderID, Date, CustomerID, Product, Quantity, UnitPrice, ShippingAddress, PaymentMethod, OrderStatus, TrackingNumber, ItemsInCart, CouponCode, ReferralSource, TotalPrice)

##  Tools & Technologies
 Python
 pandas

##  Steps Performed

1. Loaded the raw dataset into a pandas DataFrame using `pd.read_excel()`.
2. Checked for missing values across all columns:
   Found 309 missing values in the `CouponCode` column only; all other columns were complete.
3. Checked for duplicate records using `OrderID` as the unique key:
Result: 0 duplicate OrderIDs found.
4. Handled missing values:
    Filled missing `CouponCode` entries with `'None'` to represent "no coupon applied."
5. Corrected data formats:
   Converted the `Date` column to proper `datetime` format.
   Converted `Quantity`, `UnitPrice`, `TotalPrice`, and `ItemsInCart` to numeric types.
6. Verified the cleaning results:
Confirmed 0 missing values remained.
Confirmed 0 duplicate OrderIDs.
 Verified date range: `2023-01-01` to `2025-06-30`.
7. **Exported the cleaned dataset** to a new file: `Dataset_for_Analytics_CLEANED.xlsx`.

##  Cleaning Summary

| Metric | Result |
|---|---|
| Total rows in cleaned dataset | 1,200 |
| Total columns | 14 |
| Missing values before cleaning | 309 (CouponCode only) |
| Missing values after cleaning | 0 |
| Duplicate OrderIDs | 0 |

##  Deliverables
- `Dataset_for_Analytics_CLEANED.xlsx`  the cleaned dataset used as input for Project 2, 3, and 4.

##  Key Skill Demonstrated
Data cleaning, missing value imputation, duplicate detection, and data type standardization using Python/pandas.
