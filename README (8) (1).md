# 🍫 Chocolate Sales Performance Dashboard – Power BI

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

> An end-to-end interactive Sales Performance Dashboard built with Power BI, analyzing 25,000+ chocolate shipment records across 6 countries, 22 products, and 25 salespeople from 2023–2025.

---

## 📊 Dashboard Preview

![Chocolate Sales Dashboard](screenshots/dashboard-overview.png)

---

## 🎯 Key KPIs (2023 – 2024 filtered view)

| Metric | Value |
|--------|-------|
| 💰 Total Amount | **$120M** |
| 📦 Total Boxes | **7M** |
| 🚚 Shipment Count | **21K** |
| 💵 Total Profit | **$69M** |
| 📈 Profit % | **57.5%** |
| 🌍 Countries | 6 (India, USA, Canada, UK, Australia, New Zealand) |
| 👥 Salespeople | 25 across 5 teams |
| 🍫 Products | 22 across 3 categories |

---

## 📁 Project Structure

```
chocolate-sales-powerbi-dashboard/
│
├── 📊 Chocolate_Sales_Dashboard.pbix          # Power BI Report File
├── 📂 data/
│   └── sample-chocolate-shipments-data.xlsx   # Source Dataset (25,076 rows)
├── 📂 screenshots/
│   └── dashboard-overview.png                 # Dashboard Screenshot
├── 📂 dax/
│   └── measures.md                            # All DAX Measures with explanations
├── 📄 data-dictionary.md                      # Column & Table Descriptions
└── 📄 README.md
```

---

## 🗂️ Data Model – Star Schema

```
                    ┌─────────────┐
                    │  Calendar   │
                    │  (Dim)      │
                    └──────┬──────┘
                           │
┌────────────┐    ┌────────┴────────┐    ┌──────────────┐
│  Products  ├────┤   Shipments     ├────┤ Salespersons │
│  (Dim)     │    │   (Fact Table)  │    │  (Dim)       │
└────────────┘    └────────┬────────┘    └──────────────┘
                           │
                    ┌──────┴──────┐
                    │ Geographies │
                    │  (Dim)      │
                    └─────────────┘
```
| Table | Type | Rows | Key Columns |
|-------|------|------|-------------|
| `Shipments` | Fact | 25,076 | ShipmentID, Amount, Boxes, Shipdate |
| `Products` | Dimension | 22 | Product, Category, Cost_per_box, PID |
| `Geographies` | Dimension | 6 | Geo, Region, GID |
| `Salespersons` | Dimension | 25 | Sales_person, Team, Picture, SPID |
| `Calendar` | Dimension | 822 | cal_date, Year, Month, Quarter |

---

## 📈 Visuals Used

| Visual | Purpose |
|--------|---------|
| 📋 KPI Cards | Total Amount, Boxes, Shipments, Profit, Profit % |
| 📉 Line Chart | Amount CY vs PY (month-over-month trend) |
| 📉 Line Chart | Boxes CY vs PY |
| 📊 Bar Chart | Shipments Distribution by Boxes bins |
| 🍩 Donut Chart | Amount by Geography |
| 🏆 Bar Chart | Top 6 Products by Sales |
| 👤 Table with Images | Top 6 Salesperson with photo, Amount, Boxes, Profit% |
| 📋 Product Table | All products with Total Amount & Profit % |
| 🎛️ Date Slicer | Filter entire report by date range |

---

## 🧮 DAX Measures

```dax
-- Total Sales
Total Sales = SUM(Shipments[Amount])

-- Total Cost
Total Cost = SUMX(Shipments, RELATED(Products[Cost_per_box]) * Shipments[Boxes])

-- Total Profit
Total Profit = [Total Sales] - [Total Cost]

-- Profit Margin
Profit % = DIVIDE([Total Profit], [Total Sales], 0)

-- Current Year Sales
CY Sales = CALCULATE([Total Sales], YEAR(Shipments[Shipdate]) = YEAR(TODAY()))

-- Previous Year Sales
PY Sales = CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Calendar[cal_date]))

-- Year on Year Change
YoY % = DIVIDE([CY Sales] - [PY Sales], [PY Sales], 0)
```

> See full DAX file → [`dax/measures.md`](dax/measures.md)

---

## ✅ Skills Demonstrated

- ✔️ Data Cleaning with Power Query
- ✔️ Star Schema Data Modelling
- ✔️ DAX – Measures, Variables, Time Intelligence
- ✔️ Year-on-Year Comparisons
- ✔️ Calendar Table for Time Analysis
- ✔️ Conditional Formatting
- ✔️ Custom Tooltips
- ✔️ Image URLs in Tables (Salesperson photos)
- ✔️ Slicers & Report Filters
- ✔️ KPI Cards, Line, Donut, Bar, Treemap, Table Visuals

---

## 🌍 Regional Breakdown

| Region | Country | Sales Share |
|--------|---------|-------------|
| APAC | India | 28.65% |
| APAC | New Zealand | 21.25% |
| APAC | Australia | 21.14% |
| Americas | USA | 14.67% |
| Europe | UK | 7.37% |
| Americas | Canada | 6.93% |

---

## 🏆 Top Salesperson

| Rank | Name | Total Amount | Profit % |
|------|------|-------------|----------|
| 1 | Ponnan Delhi | $9.9M | 59.6% |
| 2 | Suman Katte | $8.9M | 57.6% |
| 3 | Duran Appala | $7.7M | 57.3% |
| 4 | John Joseph | $7.2M | 57.3% |
| 5 | Subbarao Malladi | $6.9M | 56.7% |

---

## 👨‍💻 About Me

I am currently pursuing a **Data Analytics course** and continuously working on real-world projects to build strong analytical and problem-solving skills.

- 🔗 [LinkedIn]https://www.linkedin.com/in/revathi-koyala-3066b12b5?utm_source=share_via&utm_content=profile&utm_medium=member_android
- 📧 revathikoyyla@gmail.com

---

## 📌 How to Use

1. Download `Chocolate_Sales_Dashboard.pbix`
2. Open with **Power BI Desktop** (free download from Microsoft)
3. If data doesn't load, re-link the Excel file via **Transform Data → Data Source Settings**
4. Explore the dashboard using the date slicer at the top right

---

*Made with ❤️ as part of Data Analytics learning journey*
