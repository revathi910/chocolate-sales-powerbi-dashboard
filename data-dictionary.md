# 📖 Data Dictionary – Chocolate Sales Dataset

---

## 📋 Table 1: Shipments (Fact Table)
> 25,076 rows | Date range: Jan 2023 – Mar 2025

| Column | Data Type | Description | Example |
|--------|-----------|-------------|---------|
| ShipmentID | Text | Unique ID for each shipment | S00000004 |
| SPID | Text | Foreign key → Salespersons table | SP01 |
| PID | Text | Foreign key → Products table | P14 |
| GID | Text | Foreign key → Geographies table | G2 |
| Shipdate | Date | Date shipment was made | 2023-05-05 |
| Amount | Decimal | Revenue from the shipment ($) | 7107.75 |
| Boxes | Integer | Number of boxes shipped | 285 |
| Order_Status | Text | Status of order | Delivered / Shipped / Cancelled / Placed |

---

## 📋 Table 2: Products (Dimension)
> 22 products across 3 categories

| Column | Data Type | Description | Example |
|--------|-----------|-------------|---------|
| PID | Text | Primary key | P01 |
| Product | Text | Product name | Milk Bars |
| Category | Text | Product category | Bars / Bites / Other |
| Cost_per_box | Decimal | Cost to produce one box ($) | 5.26 |

### Product Categories
| Category | Products |
|----------|---------|
| Bars | Milk Bars, Almond Choco, Raspberry Choco, Mint Chip Choco, 99% Dark & Pure, Orange Choco, Fruit & Nut Bars, 85% Dark Bars, Baker's Choco Chips, Caramel Stuffed Bars, Smooth Silky Salty |
| Bites | 50% Dark Bites, Eclairs, Spicy Special Slims, After Nines, 70% Dark Bites, Choco Coated Almonds, Peanut Butter Cubes |
| Other | Drinking Coco, White Choc, Organic Choco Syrup, Manuka Honey Choco |

---

## 📋 Table 3: Geographies (Dimension)
> 6 countries across 3 regions

| Column | Data Type | Description | Example |
|--------|-----------|-------------|---------|
| GID | Text | Primary key | G1 |
| Geo | Text | Country name | India |
| Region | Text | Regional grouping | APAC / Americas / Europe |

### Countries
| GID | Country | Region |
|-----|---------|--------|
| G1 | India | APAC |
| G2 | USA | Americas |
| G3 | Canada | Americas |
| G4 | New Zealand | APAC |
| G5 | Australia | APAC |
| G6 | UK | Europe |

---

## 📋 Table 4: Salespersons (Dimension)
> 25 salespeople across 5 teams

| Column | Data Type | Description | Example |
|--------|-----------|-------------|---------|
| SPID | Text | Primary key | SP01 |
| Sales_person | Text | Full name of salesperson | Ramalingam Kothapeta |
| Team | Text | Team name | Yummies / Delish / Jucies / Tempo |
| Picture | Text (URL) | Profile image URL for Power BI table visual | https://... |

### Teams
| Team | Members |
|------|---------|
| Yummies | SP01, SP02, SP03, SP11, SP12, SP15 |
| Delish | SP04, SP05, SP06, SP07, SP08, SP13, SP14 |
| Jucies | SP09, SP10, SP16, SP17, SP18, SP19, SP20 |
| Tempo | SP21, SP22, SP23, SP24, SP25 |

---

## 📋 Table 5: Calendar (Dimension)
> 822 rows | Jan 2023 – Mar 2025

| Column | Data Type | Description | Example |
|--------|-----------|-------------|---------|
| cal_date | Date | Full date | 2023-01-01 |
| Year | Integer | Year number | 2023 |
| Month | Integer | Month number | 1 |
| Quarter | Text | Quarter label | Q1 |
| weekday_num | Integer | Day of week number (1=Mon) | 7 |
| weekday_name | Text | Day of week name | Sunday |

---

## 🔗 Relationships (Star Schema)

```
Shipments[PID]      → Products[PID]        (Many to One)
Shipments[GID]      → Geographies[GID]     (Many to One)
Shipments[SPID]     → Salespersons[SPID]   (Many to One)
Shipments[Shipdate] → Calendar[cal_date]   (Many to One)
```
