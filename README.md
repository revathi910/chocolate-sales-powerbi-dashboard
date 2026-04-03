---

## 🗂️ Data Model – Star Schema

| Table | Type | Description |
|-------|------|-------------|
| `Shipments` | Fact | 25,076 rows — sales transactions |
| `Products` | Dimension | 22 products across 3 categories |
| `Geographies` | Dimension | 6 countries, 3 regions |
| `Salespersons` | Dimension | 25 salespeople across 5 teams |
| `Calendar` | Dimension | Date table for time intelligence |

---

## 🧮 DAX Measures
```dax
Total Sales = SUM(Shipments[Amount])

Total Cost = SUMX(Shipments, RELATED(Products[Cost_per_box]) * Shipments[Boxes])

Total Profit = [Total Sales] - [Total Cost]

Profit % = DIVIDE([Total Profit], [Total Sales], 0)

PY Sales = CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Calendar[cal_date]))

YoY % =
VAR _cy = [CY Sales]
VAR _py = [PY Sales]
RETURN DIVIDE(_cy - _py, _py, 0)
```

---

## 📈 Visuals Used

| Visual | Purpose |
|--------|---------|
| 📋 KPI Cards | Total Amount, Boxes, Shipments, Profit, Profit % |
| 📉 Line Chart | Amount & Boxes CY vs PY trend |
| 📊 Bar Chart | Shipments Distribution & Top 6 Products |
| 🍩 Donut Chart | Amount by Geography |
| 👤 Table with Images | Top 6 Salesperson performance |
| 📋 Product Table | All products with Amount & Profit % |
| 🎛️ Date Slicer | Filter report by date range |

---

## 🌍 Regional Breakdown

| Country | Region | Sales Share |
|---------|--------|-------------|
| India | APAC | 28.65% |
| New Zealand | APAC | 21.25% |
| Australia | APAC | 21.14% |
| USA | Americas | 14.67% |
| UK | Europe | 7.37% |
| Canada | Americas | 6.93% |

---

## 🏆 Top Salespersons

| Rank | Name | Total Amount | Profit % |
|------|------|-------------|----------|
| 1 | Ponnan Delhi | $9.9M | 59.6% |
| 2 | Suman Katte | $8.9M | 57.6% |
| 3 | Duran Appala | $7.7M | 57.3% |
| 4 | John Joseph | $7.2M | 57.3% |
| 5 | Subbarao Malladi | $6.9M | 56.7% |
| 6 | Dinanath Simhambhatla | $6.8M | 57.1% |

---

## ✅ Skills Demonstrated

- ✔️ Data Cleaning with Power Query
- ✔️ Star Schema Data Modelling
- ✔️ DAX – Measures, Variables, Time Intelligence
- ✔️ Year-on-Year (CY vs PY) Comparisons
- ✔️ Calendar Table for Time Analysis
- ✔️ Conditional Formatting
- ✔️ Custom Tooltips
- ✔️ Image URLs in Tables
- ✔️ Slicers & Report Filters
- ✔️ KPI Cards, Line, Donut, Bar, Table Visuals

---

## 📌 How to Use

1. Download `Chocolate_Sales_Dashboard.pbix`
2. Open with **Power BI Desktop** (free from Microsoft)
3. Re-link the Excel file if needed via **Transform Data → Data Source Settings**
4. Use the date slicer (top right) to filter by date range

---

## 👩‍💻 About Me

Hi, I'm **Revathi Koyala** — currently pursuing a **Data Analytics course** and continuously working on real-world projects to build strong analytical and problem-solving skills.

- 🔗 [LinkedIn](https://www.linkedin.com/in/revathi-koyala-3066b12b5?utm_source=share_via&utm_content=profile&utm_medium=member_android)
- 📧 revathikoyyala@gmail.com

---

## 📄 License

This project is licensed under the [MIT License](LICENSE)

---
*Made with ❤️ as part of my Data Analytics learning journey*
