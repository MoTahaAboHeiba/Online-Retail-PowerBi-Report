# Data Dictionary

**Dataset:** Online Retail Cleaned Dataset  
**File:** `Online_Retail_Cleaned.csv`  
**Rows:** 406,829 transactions  
**Columns:** 16 (8 original + 8 engineered)  
**Date Range:** December 1, 2010 - December 9, 2011

---

## 📊 Column Reference

### **Original Columns (8)**

| Column Name | Data Type | Description | Example Values | Null Values |
|-------------|-----------|-------------|----------------|-------------|
| **InvoiceNo** | String | 6-digit invoice number. Prefix 'C' indicates cancelled transaction | 536365, 536366, C536367 | 0 (0%) |
| **StockCode** | String | Product/item code. 5-6 characters alphanumeric | 85123A, 71053, 84406B | 0 (0%) |
| **Description** | String | Product name/description | WHITE HANGING HEART T-LIGHT HOLDER | 0 (0%) |
| **Quantity** | Integer | Number of items purchased per transaction. Must be positive | 6, 24, 12 | 0 (0%) |
| **InvoiceDate** | DateTime | Date and time of transaction | 2010-12-01 08:26:00 | 0 (0%) |
| **UnitPrice** | Decimal | Price per unit in British Pounds (£) | 2.55, 3.39, 2.75 | 0 (0%) |
| **CustomerID** | String | Unique 5-digit customer identifier | 17850, 13047, 12583 | 0 (0%) |
| **Country** | String | Customer's country of residence | United Kingdom, France, Germany | 0 (0%) |

---

### **Engineered Columns (8)**

| Column Name | Data Type | Description | Example Values | Calculation Method |
|-------------|-----------|-------------|----------------|-------------------|
| **TotalPrice** | Decimal | Total transaction amount (Quantity × UnitPrice) | 15.30, 81.36, 33.00 | `Quantity * UnitPrice` |
| **Year** | Integer | Year extracted from InvoiceDate | 2010, 2011 | `InvoiceDate.year` |
| **Quarter** | Integer | Quarter of the year (1-4) | 1, 2, 3, 4 | `InvoiceDate.quarter` |
| **Month** | Integer | Month number (1-12) | 1, 2, 3, ..., 12 | `InvoiceDate.month` |
| **MonthName** | String | Full month name | January, February, March | `InvoiceDate.strftime('%B')` |
| **DayOfWeek** | String | Day of the week | Monday, Tuesday, Wednesday | `InvoiceDate.day_name()` |
| **Hour** | Integer | Hour of transaction (0-23) | 8, 12, 15, 19 | `InvoiceDate.hour` |
| **CustomerSegment** | String | Customer value category based on total spend | High Value, Medium Value, Low Value | Quantile-based (75th, 25th percentile) |

---

## 📈 Data Statistics

### Overall Dataset
| Metric | Value |
|--------|-------|
| Total Transactions | 406,829 |
| Unique Customers | 4,372 |
| Unique Products | 3,684 |
| Countries | 38 |
| Date Range | Dec 1, 2010 - Dec 9, 2011 (13 months) |
| Total Revenue | £9,747,748 |
| Average Order Value | £375.52 |
| Total Items Sold | 5,176,450 |

---

## 🔢 Column-Level Statistics

### **Quantity**
- **Min:** 1
- **Max:** 80,995
- **Mean:** 12.7
- **Median:** 6
- **Data Type:** Integer (positive values only)

### **UnitPrice**
- **Min:** £0.001
- **Max:** £38,970
- **Mean:** £4.61
- **Median:** £2.08
- **Data Type:** Decimal (positive values only)

### **TotalPrice**
- **Min:** £0.01
- **Max:** £168,469.60
- **Mean:** £23.97
- **Median:** £12.75
- **Data Type:** Decimal (calculated field)

### **Hour** (Transaction Time)
- **Min:** 6 (6:00 AM)
- **Max:** 20 (8:00 PM)
- **Peak Hour:** 12 (12:00 PM - Afternoon)
- **Distribution:** Most transactions occur 10:00 AM - 3:00 PM

---

## 🌍 Country Distribution

| Country | Transaction Count | % of Total | Revenue (£) |
|---------|-------------------|------------|-------------|
| United Kingdom | 354,321 | 87.1% | £8,187,806 (84%) |
| Germany | 9,495 | 2.3% | £228,644 |
| France | 8,557 | 2.1% | £197,403 |
| EIRE (Ireland) | 8,196 | 2.0% | £263,276 |
| Spain | 2,533 | 0.6% | £54,774 |
| Others (33 countries) | 23,727 | 5.9% | £815,845 |

---

## 👥 Customer Segmentation Logic

### **CustomerSegment** Calculation

```python
# Customer segments based on total spend per customer
customer_totals = df.groupby('CustomerID')['TotalPrice'].sum()

# Define thresholds
high_threshold = customer_totals.quantile(0.75)   # Top 25%
low_threshold = customer_totals.quantile(0.25)    # Bottom 25%

# Segment assignment
if total_spend >= high_threshold:
    segment = "High Value"
elif total_spend <= low_threshold:
    segment = "Low Value"
else:
    segment = "Medium Value"
```

### **Segment Distribution**

| Segment | Customer Count | % of Customers | Revenue Contribution |
|---------|---------------|----------------|---------------------|
| High Value | 1,093 (25%) | 25% | £6,332,000 (65%) |
| Medium Value | 2,186 (50%) | 50% | £1,767,000 (18%) |
| Low Value | 1,093 (25%) | 25% | £1,649,000 (17%) |

---

## 📅 Temporal Patterns

### **Year Distribution**
| Year | Transaction Count | Revenue (£) |
|------|-------------------|-------------|
| 2010 | 26,893 | £1,128,229 |
| 2011 | 379,936 | £8,619,519 |

### **Quarter Distribution (2011)**
| Quarter | Transaction Count | Revenue (£) |
|---------|-------------------|-------------|
| Q1 | 106,873 | £2,257,871 |
| Q2 | 102,645 | £2,074,136 |
| Q3 | 93,712 | £2,143,297 |
| Q4 | 76,706 | £2,144,215 |

### **Top Months by Revenue**
| Month | Revenue (£) |
|-------|-------------|
| November 2011 | £1,509,870 |
| October 2011 | £1,070,704 |
| September 2011 | £1,072,593 |

---

## 🔍 Data Quality Rules Applied

### **1. Missing Values**
- **CustomerID:** 0 null values (all nulls removed during cleaning)
- **Description:** 0 null values
- **All other columns:** 0 null values

### **2. Valid Ranges**
- **Quantity:** Must be > 0 (negative values removed)
- **UnitPrice:** Must be > 0 (zero/negative prices removed)
- **TotalPrice:** Always positive (calculated from valid Quantity × UnitPrice)

### **3. Cancelled Transactions**
- Transactions with InvoiceNo starting with 'C' removed
- These represent returns/cancellations

### **4. Duplicates**
- No duplicate rows present
- Duplicate check performed on all 16 columns

---

## 🎯 Usage Examples

### **Power BI**
```
// Load data
Source = Csv.Document(File.Contents("Online_Retail_Cleaned.csv"))

// Create relationship-ready table
Table = Table.TransformColumnTypes(Source, {
    {"InvoiceNo", type text},
    {"InvoiceDate", type datetime},
    {"Quantity", Int64.Type},
    {"UnitPrice", type number},
    {"TotalPrice", type number}
})
```

### **Python**
```python
import pandas as pd

# Load data
df = pd.read_csv('Online_Retail_Cleaned.csv', parse_dates=['InvoiceDate'])

# Quick exploration
print(df.info())
print(df.describe())
print(df.head())
```

### **SQL**
```sql
-- Import to database
LOAD DATA INFILE 'Online_Retail_Cleaned.csv'
INTO TABLE retail_transactions
FIELDS TERMINATED BY ','
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;

-- Query example
SELECT Country, SUM(TotalPrice) as Revenue
FROM retail_transactions
GROUP BY Country
ORDER BY Revenue DESC;
```

---

## 🚨 Important Notes

1. **Currency:** All monetary values are in British Pounds (£)
2. **Timezone:** All timestamps are in UK timezone (GMT/BST)
3. **Date Range:** Data ends December 9, 2011 (incomplete December)
4. **Customer IDs:** Anonymized 5-digit identifiers
5. **Product Codes:** Some codes may represent bundles or special offers

---

## 📚 References

- **Original Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+Retail)
- **License:** Open for academic/research use
- **Citation:** Daqing Chen, Sai Liang Sain, and Kun Guo. Data mining for the online retail industry: A case study of RFM model-based customer segmentation using data mining, Journal of Database Marketing and Customer Strategy Management, Vol. 19, No. 3, pp. 197-208, 2012

---

**Last Updated:** December 23, 2025  
**Version:** 1.0  
**Contact:** [Your email for data-related questions]
