```
# Project 1: Data Cleaning

**DecodeLabs Internship – Task 1**  
*Batch: 2026*

---

## Project Overview

The objective of this task is to clean a raw e-commerce dataset containing **2,000+ order records**. Raw data typically contains missing values, inconsistent formatting, and duplicate entries—all of which can lead to incorrect analysis and poor business decisions.

This project applies systematic data cleaning techniques using **Python (Pandas)** in a **Jupyter Notebook** environment to transform raw, messy data into a consistent, analysis-ready format.

---

## Tools Used

| Tool | Purpose |
|------|---------|
| Python 3.x | Core programming language |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations and validation |
| OpenPyXL | Excel file reading and writing |
| Jupyter Notebook | Interactive development environment |

---

## Dataset Overview

The raw dataset consists of **2,000+ transactions** with the following 14 columns:

| Column Name | Description | Data Type (Raw) |
|-------------|-------------|-----------------|
| OrderID | Unique order identifier | Text |
| Date | Order placement date | Text (YYYY-MM-DD HH:MM:SS) |
| CustomerID | Unique customer identifier | Text |
| Product | Product category purchased | Text |
| Quantity | Number of units ordered | Text/Integer |
| UnitPrice | Price per unit | Text/Float |
| ShippingAddress | Delivery location | Text |
| PaymentMethod | Payment type used | Text |
| OrderStatus | Current order status | Text |
| TrackingNumber | Shipment tracking ID | Text |
| ItemsInCart | Total items in cart | Text/Integer |
| CouponCode | Promotional code applied | Text (with blanks) |
| ReferralSource | Channel of acquisition | Text |
| TotalPrice | Total order value | Text/Float |

---

## Data Cleaning Steps Performed

### Step 1: Load the Dataset
The raw Excel file was loaded into a Pandas DataFrame. Verified successful loading using `df.head()`.

```python
import pandas as pd
df = pd.read_excel('Dataset for Data Analytics.xlsx')
df.head()
```

### Step 2: Check for Missing Values
A systematic scan was performed to identify columns with null or empty values.

```python
print(df.isnull().sum())
```

**Findings:**
- `CouponCode`: Several hundred missing values (customers who did not use a coupon)
- All other columns: 0 missing values

### Step 3: Handle Missing Values
All blank entries in the `CouponCode` column were filled with the value `"None"`.

```python
df['CouponCode'] = df['CouponCode'].fillna('None')
```

**Verification:**
```python
print(df.isnull().sum())
# Output: All columns now show 0 missing values.
```

### Step 4: Check for Duplicate Records
The `OrderID` column (unique identifier) was used to check for duplicates.

```python
duplicate_count = df.duplicated(subset=['OrderID']).sum()
print(f"Duplicate OrderIDs: {duplicate_count}")
```

**Result:** 0 duplicates found. The dataset was already unique.

```python
df.drop_duplicates(subset=['OrderID'], keep='first', inplace=True)
```

### Step 5: Correct Data Types
Ensured columns are stored in the correct data types for accurate calculations.

```python
df['Date'] = pd.to_datetime(df['Date'])
df['Quantity'] = pd.to_numeric(df['Quantity'])
df['UnitPrice'] = pd.to_numeric(df['UnitPrice'])
df['TotalPrice'] = pd.to_numeric(df['TotalPrice'])
df['ItemsInCart'] = pd.to_numeric(df['ItemsInCart'])
```

**Data Type Summary:**
- `Date`: Object (Text) → datetime64
- `Quantity`, `UnitPrice`, `TotalPrice`, `ItemsInCart`: Object → Float/Int

### Step 6: Validate Data Accuracy
Performed a validation check to ensure `TotalPrice` equals `Quantity × UnitPrice`.

```python
import numpy as np
df['PriceCheck'] = np.isclose(df['TotalPrice'], df['Quantity'] * df['UnitPrice'])
print(df['PriceCheck'].value_counts())
```

**Result:** All rows passed validation (True for all entries).

### Step 7: Final Output
The cleaned DataFrame was saved as a new Excel file.

```python
df.to_excel('Dataset_for_Analytics_CLEANED.xlsx', index=False)
```

---

## Cleaning Summary

| Metric | Before | After |
|--------|--------|-------|
| Total Rows | 2,000+ | 2,000+ (unchanged) |
| Total Columns | 14 | 14 |
| Duplicate OrderIDs | 0 | 0 |
| Missing Values (CouponCode) | Several hundred | 0 (filled with "None") |
| Missing Values (Other Columns) | 0 | 0 |
| Date Format | Text string | datetime type |
| Numeric Columns | Object/Text | Float/Int |
| TotalPrice Validation | Not checked | ✅ All passed |

---

## Repository Contents

| File | Description |
|------|-------------|
| `Dataset for Data Analytics.xlsx` | Original raw dataset (kept as reference) |
| `Dataset_for_Analytics_CLEANED.xlsx` | Final cleaned dataset |
| `Project_1_Cleaning.ipynb` | Jupyter Notebook with complete cleaning code |
| `screenshots/` | Folder containing screenshot outputs |
| `README.md` | This document |

---

## How to Run This Notebook

1. **Clone** this repository or download the files.
2. Ensure `Dataset for Data Analytics.xlsx` is in the same folder as the notebook.
3. **Open** `Project_1_Cleaning.ipynb` in Jupyter Notebook or VS Code.
4. **Run** all cells sequentially (`Cell → Run All`).
5. The cleaned file `Dataset_for_Analytics_CLEANED.xlsx` will be generated in the same folder.

---

## Screenshots

Place your screenshots in the `screenshots/` folder with the following names:

| File Name | Description |
|-----------|-------------|
| `01_data_loaded.png` | `df.head()` output showing first 5 rows |
| `02_missing_values_before.png` | `df.isnull().sum()` before cleaning |
| `03_missing_values_after.png` | `df.isnull().sum()` after filling CouponCode |
| `04_no_duplicates.png` | Output of duplicate check |
| `05_data_types.png` | `df.dtypes` after type conversion |
| `06_validation.png` | Price validation result |
| `07_file_saved.png` | Confirmation of saved file |

---

## Key Learnings

- Real-world datasets often have missing values that require systematic handling.
- Filling missing values with neutral placeholders (like `"None"`) preserves data structure.
- Duplicate checks are essential even when data appears clean.
- Correct data types are crucial for accurate calculations and time-series analysis.
- Validating derived columns (like TotalPrice) ensures mathematical integrity.
- Pandas provides efficient, vectorized operations for handling large datasets quickly.

---

## Next Steps

This cleaned dataset serves as the foundation for subsequent tasks:

- **Task 2:** Exploratory Data Analysis (EDA)
- **Task 3:** SQL Data Analysis
- **Task 4:** Data Visualization

---

## Author

**Misma Yaseen**  
*Data Analytics Intern* | DecodeLabs  
*

