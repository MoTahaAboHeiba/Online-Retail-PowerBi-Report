# 📊 Online Retail Analytics Dashboard

> **Interactive Power BI dashboard transforming 541K retail transactions into actionable business intelligence**

[![Power BI](https://img.shields.io/badge/Power%20BI-Interactive%20Dashboard-gold?style=flat-square&logo=powerbi)](https://app.powerbi.com/links/SGgKQbvxT0?ctid=5f593c84-cad4-46c8-b3de-321c3e829a99&pbi_source=linkShare)
[![Dataset](https://img.shields.io/badge/Dataset-UCI%20Machine%20Learning-blue?style=flat-square)](https://archive.ics.uci.edu/ml/datasets/Online+Retail)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)]()

---

## 📖 The Story

### **SITUATION**
A retail company sits on 541,909 transactions spanning 13 months across 38 countries. Raw data scattered across spreadsheets. **No visibility** into customer behavior. **No insights** on revenue drivers. **No way** to make data-driven decisions.

### **TASK**
Build an **enterprise-grade dashboard** that:
- Transforms messy data into clean, actionable insights
- Enables executives to understand business performance at a glance
- Allows stakeholders to drill into specifics when needed
- Provides real-time visibility into key metrics

### **ACTION**
Engineered a **3-page interactive Power BI dashboard** with:
- ✅ **Automated ETL pipeline** (Python + Power Query)
- ✅ **5 strategic DAX measures** for KPI tracking
- ✅ **3 intelligent DAX columns** for dynamic segmentation
- ✅ **Advanced interactivity** (drill-down, slicers, drill-through)
- ✅ **Professional design** (dark theme, optimized UX)

### **RESULT**
**£9.73M revenue insight** | **25,900+ orders analyzed** | **4,372 customers segmented** | **85% data coverage**

👉 **[View Live Dashboard](https://app.powerbi.com/links/SGgKQbvxT0?ctid=5f593c84-cad4-46c8-b3de-321c3e829a99&pbi_source=linkShare)**

---

## 🎯 What You Get

### **Page 1: Executive Overview**
4 KPI cards + Revenue trends + Geographic heatmap + Customer value breakdown
- **One-page snapshot** of business health
- **Drill down** from years to months in seconds
- **Filter** by country in real-time

### **Page 2: Product Intelligence**  
Top 20 products + Price-quantity analysis + Time-of-day breakdown
- Identify **best-performing products** instantly
- Understand **pricing dynamics**
- Optimize **inventory** by peak hours

### **Page 3: Customer Analytics**
Customer segmentation + Growth trends + VIP identification
- Spot **high-value customers** (top 25% = 65% revenue)
- Track **customer lifecycle** over time
- Plan **retention strategies** by segment

---

## 🔧 Tech Stack

| Component | Technology | Why It Matters |
|-----------|-----------|----------------|
| **Dashboard** | Power BI Desktop | Industry-standard BI tool |
| **Data Transformation** | Power Query + Python | Automated, scalable ETL |
| **Calculations** | DAX (8 formulas) | Dynamic, optimized metrics |
| **Data Source** | CSV (cleaned) | Fast, efficient loading |

---

## 📊 Key Metrics at a Glance

```
Total Revenue        £9.73M
Average Order Value  £375.52
Total Customers      4,372
Total Orders         25,900
Data Coverage        406K rows (75% of raw data)
Countries            38
Time Period          13 months (Dec 2010 - Nov 2011)
```

---

## ⚡ Why This Project Matters

### For **Executives**
- 📈 Revenue trends visible in seconds
- 🌍 Market concentration identified (84% UK)
- 👥 Customer value clearly segmented

### For **Product Teams**
- 📦 Top products ranked by revenue
- 💰 Price elasticity visualized
- ⏰ Peak sales hours identified

### For **Data Engineers**
- 🏗️ Clean, production-ready ETL
- 📐 Scalable data modeling
- 🔄 Automated refresh capability

---

## 🚀 Quick Start

### **View the Dashboard** (No Installation)
Click here → **[Live Power BI Dashboard](https://app.powerbi.com/links/SGgKQbvxT0?ctid=5f593c84-cad4-46c8-b3de-321c3e829a99&pbi_source=linkShare)**

### **Explore Locally** (With Code)
```bash
# Clone repository
git clone https://github.com/yourusername/online-retail-powerbi.git

# Open Power BI file
powerbi/Online_Retail_Analysis.pbix

# Review documentation
docs/Project_Documentation.md
```

---

## 💡 Inside the Dashboard

### **5 DAX Measures** (Business Logic)
```dax
Total Revenue        = SUM(TotalPrice)
Average Order Value  = DIVIDE([Total Revenue], DISTINCTCOUNT(InvoiceNo))
Total Customers      = DISTINCTCOUNT(CustomerID)
Total Orders         = DISTINCTCOUNT(InvoiceNo)
Total Quantity       = SUM(Quantity)
```

### **3 DAX Columns** (Smart Segmentation)
```dax
Transaction Size     = SWITCH(TotalPrice, >=500→Large, >=100→Medium, >=50→Small, →Micro)
Customer Type        = SWITCH(Orders, >=10→VIP, >=5→Regular, →Occasional)
Time of Day          = SWITCH(Hour, >=18→Evening, >=12→Afternoon, >=6→Morning, →Night)
```

### **Interactive Features**
- 🎯 **Drill-down hierarchy** - Explore Year → Quarter → Month
- 🔍 **Synchronized slicers** - Filter by Date + Country across all pages
- 📌 **Bookmarks** - One-click preset views ("UK Focus" / "Global View")
- 🎨 **Custom tooltips** - Hover for detailed context

---

## 📁 Repository Structure

```
online-retail-powerbi/
├── README.md                          ← You are here
├── LICENSE                            ← MIT License
│
├── powerbi/
│   └── Online_Retail_Analysis.pbix    ← Main dashboard file
│
├── data/
│   ├── Online_Retail_Cleaned.csv      ← Clean dataset
│   └── data-dictionary.md             ← Column reference
│
├── docs/
│   ├── Project_Documentation.md       ← Full technical report
│   ├── ETL_Process.md                 ← Data pipeline details
│   └── DAX_Measures.md                ← Formula documentation
│
└── images/
    ├── dashboard-page1.png            ← Executive Overview
    ├── dashboard-page2.png            ← Product Intelligence
    └── dashboard-page3.png            ← Customer Analytics
```

---

## 🎓 What This Demonstrates

✅ **Data Engineering** - ETL pipeline (Python + Power Query)  
✅ **BI Development** - Professional dashboard architecture  
✅ **DAX Expertise** - Advanced measures and columns  
✅ **Data Storytelling** - Actionable insights from raw data  
✅ **User Experience** - Intuitive, interactive design  
✅ **Problem Solving** - Real-world business questions answered  

---

## 📈 Impact by the Numbers

| Metric | Finding | Action |
|--------|---------|--------|
| 84% revenue from UK | Market concentration | Expand internationally |
| VIP = 65% revenue | High-value dependency | Implement VIP retention |
| £375.52 AOV | Strong B2B signals | Increase order value |
| Afternoon peak | Time concentration | Optimize staffing |

---

## 🔗 Resources

- **View Dashboard:** [Power BI Live Link](https://app.powerbi.com/links/SGgKQbvxT0?ctid=5f593c84-cad4-46c8-b3de-321c3e829a99&pbi_source=linkShare)
- **Dataset Source:** [UCI Machine Learning](https://archive.ics.uci.edu/ml/datasets/Online+Retail)
- **Full Documentation:** See `docs/` folder
- **Code Examples:** See `docs/DAX_Measures.md`

---

## 👨‍💻 About

**Built by:** [Your Name]  
**Role:** Data Engineer / Business Intelligence Developer  
**Contact:** [your.email@example.com]

**Project Type:** Final Year Computer Science Graduation Project (2025)

---

## 📄 License

MIT License - Free to use, modify, and distribute.

---

## ⭐ Show Your Support

If this project helped you learn Power BI or data engineering:
- ⭐ Star this repository
- 🔗 Share with others
- 💬 Provide feedback
- 🐛 Report issues

---

**Built with precision. Designed for impact. Ready for production.** ✨

👉 **[Explore the Dashboard Now](https://app.powerbi.com/links/SGgKQbvxT0?ctid=5f593c84-cad4-46c8-b3de-321c3e829a99&pbi_source=linkShare)**
