# 🧮 DAX Measures – Chocolate Sales Dashboard

All DAX measures used in the Power BI report, grouped by category.

---

## 💰 Sales Measures

```dax
-- Sum of all shipment amounts
Total Sales = SUM(Shipments[Amount])

-- Sum of all boxes shipped
Total Boxes = SUM(Shipments[Boxes])

-- Count of shipments
Shipment Count = COUNTROWS(Shipments)
```

---

## 💵 Profit Measures

```dax
-- Calculate total cost using cost per box × boxes shipped
Total Cost =
SUMX(
    Shipments,
    RELATED(Products[Cost_per_box]) * Shipments[Boxes]
)

-- Profit = Sales minus Cost
Total Profit = [Total Sales] - [Total Cost]

-- Profit as a percentage of Sales
Profit % = DIVIDE([Total Profit], [Total Sales], 0)
```

---

## 📅 Time Intelligence – CY vs PY

```dax
-- Current Year Sales
CY Sales =
CALCULATE(
    [Total Sales],
    YEAR(Shipments[Shipdate]) = YEAR(TODAY())
)

-- Previous Year Sales using calendar table
PY Sales =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(Calendar[cal_date])
)

-- Year on Year difference
YoY Change = [CY Sales] - [PY Sales]

-- Year on Year % change
YoY % =
VAR _cy = [CY Sales]
VAR _py = [PY Sales]
RETURN
    DIVIDE(_cy - _py, _py, 0)
```

---

## 📦 Current Year Boxes

```dax
CY Boxes =
CALCULATE(
    [Total Boxes],
    YEAR(Shipments[Shipdate]) = YEAR(TODAY())
)

PY Boxes =
CALCULATE(
    [Total Boxes],
    SAMEPERIODLASTYEAR(Calendar[cal_date])
)
```

---

## 🏆 TopN Filtering (for Top 6 visuals)

```dax
-- Used with Visual-level TopN filter set to Top 6 by Total Sales
-- No separate measure needed — apply via Filters pane in Power BI
```

---

## 💡 Tips on Using VAR in DAX

```dax
-- Using VAR makes DAX easier to read and debug
Profit % with VAR =
VAR _sales = [Total Sales]
VAR _cost  = [Total Cost]
VAR _profit = _sales - _cost
RETURN
    DIVIDE(_profit, _sales, 0)
```

---

## 📌 Notes

- All time intelligence measures require a proper **Calendar table** connected to `Shipments[Shipdate]`
- Mark the Calendar table as a **Date Table** in Power BI (Table Tools → Mark as Date Table)
- Use `DIVIDE()` instead of `/` to safely handle division by zero
