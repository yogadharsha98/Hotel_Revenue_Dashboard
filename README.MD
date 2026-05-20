# 🏨 Hotel Revenue & Performance Dashboard

> **Excel dashboard** analysing hotel operational and financial performance across 6 months (January – June 2025).

![Dashboard Preview](./images/Monthly_Revenue.JPG)

---

## 📊 Dashboard Overview

This dashboard was built to help hotel management make data-driven decisions by tracking key revenue, occupancy, and expense metrics across all departments — summarised by month using PivotTables and interactive slicers built entirely in Microsoft Excel.

---

## ✨ Features

| Section                     | Description                                                                                  |
| --------------------------- | -------------------------------------------------------------------------------------------- |
| **KPI Cards**               | Total Revenue, Net Revenue, Occupancy Rate, Total Expenses — updated per selected month      |
| **Revenue Breakdown**       | Horizontal bar chart — Room Revenue, Restaurant Revenue, Net Revenue, Expenses side by side  |
| **Booking Source Analysis** | Revenue by channel — Direct, Agoda, Booking.com, Walk-in, Travel Agent, Website              |
| **Monthly Revenue Trend**   | Bar chart showing Jan–Jun revenue progression                                                |
| **Expenses by Department**  | Horizontal bar chart — Finance, HR, Maintenance, Sales, Spa, F&B, Housekeeping               |
| **Occupancy Summary**       | Table showing Rooms Available, Rooms Occupied, Occupancy Rate, ADR, RevPAR                   |
| **Monthly Detail Table**    | Room Revenue, Restaurant Revenue, Total Revenue, Expenses, Net Revenue, Occupancy % by month |
| **Net Revenue Line Chart**  | Trend line showing net revenue movement Jan–Jun                                              |
| **Month Slicer**            | Interactive filter — select any month to update all PivotTables and charts dynamically       |

---

## 🔑 Key Metrics (YTD — Jan to Jun 2025)

| Metric                   | Value            |
| ------------------------ | ---------------- |
| Total Revenue            | LKR 111.6M       |
| Total Expenses           | LKR 63.2M        |
| Total Net Revenue        | LKR 48.4M        |
| Average Occupancy Rate   | 70.29%           |
| Average ADR              | LKR 10,957       |
| Average RevPAR           | LKR 7,982        |
| Best Month (Revenue)     | June — LKR 21.2M |
| Best Month (Net Revenue) | June — LKR 11.3M |

---

## 🛠️ Tools & Technologies

| Tool                       | Purpose                                                             |
| -------------------------- | ------------------------------------------------------------------- |
| **Microsoft Excel**        | Dashboard development, PivotTables, charts, slicers                 |
| **Power Query**            | Data import, transformation, and cleaning for all 7 tables          |
| **PivotTables**            | Cross-table aggregation — revenue, expenses, seasonal adjustments   |
| **Conditional Formatting** | Visual highlighting — green for positive variance, red for negative |
| **Data Validation**        | Dropdown lists and input rules to maintain data integrity           |
| **Data Model**             | DateTable linked to all fact tables via Power Query connections     |

---

## 📐 Data Model

```
DateTable (Date)
     │
     ├── Reservations      (CheckInDate)
     ├── RestaurantSales   (SaleDate)
     ├── Occupancy         (Date)
     └── Expenses          (ExpenseDate)

Reservations
     ├── Customers         (CustomerID)
     └── Rooms             (RoomID)
```

All tables connected through a central **DateTable** in the Excel Data Model — enabling accurate cross-table PivotTable filtering via the month slicer.

---

## 📐 Key Excel Formulas & Functions Used

```excel
-- Revenue calculation (PivotTable Values)
Sum of RoomRevenue        → Total Room Revenue
Sum of TotalAmount        → Total Restaurant Revenue
Sum of Amount             → Total Expenses

-- Calculated columns
Net Revenue   = Room Revenue + Restaurant Revenue - Expenses
Variance %    = (Actual - Budget) / Budget

-- Hotel KPIs
ADR    = Room Revenue / Rooms Occupied
RevPAR = Room Revenue / Rooms Available

-- Date intelligence
=TEXT(A2, "mmmm")         -- Month name
=YEAR(A2)                 -- Year extraction
=EOMONTH(TODAY(), 0)      -- End of current month
```

---

## 📋 Dataset Description

| Table           | Rows  | Key Columns                                                                |
| --------------- | ----- | -------------------------------------------------------------------------- |
| Reservations    | 1,000 | ReservationID, CustomerID, RoomID, BookingSource, CheckInDate, RoomRevenue |
| RestaurantSales | 1,500 | SaleID, SaleDate, MenuItem, TotalAmount, Outlet, MealPeriod                |
| Occupancy       | 181   | Date, RoomsAvailable, RoomsOccupied, OccupancyRate, ADR, RevPAR            |
| Expenses        | 279   | ExpenseID, ExpenseDate, Department, ExpenseCategory, Amount                |
| Customers       | 100   | CustomerID, CustomerName, Country, LoyaltyMember                           |
| Rooms           | 50    | RoomID, RoomType, BaseRate, Status                                         |
| Employees       | 36    | EmployeeID, Department, Role, MonthlySalary                                |

> All data is **sample/synthetic** — generated for learning and portfolio purposes only.

---

## 🏨 Hotel KPIs Explained

| KPI                | Formula                                | What it tells management                                        |
| ------------------ | -------------------------------------- | --------------------------------------------------------------- |
| **Occupancy Rate** | Rooms Occupied ÷ Rooms Available × 100 | What % of rooms are being filled                                |
| **ADR**            | Room Revenue ÷ Rooms Occupied          | Average price paid per occupied room                            |
| **RevPAR**         | Room Revenue ÷ Rooms Available         | Revenue earned per available room — combines occupancy and rate |
| **Net Revenue**    | Total Revenue − Total Expenses         | Actual profit after all costs                                   |

---

## 📈 Reports Built

| Report                     | Frequency | Contents                                               |
| -------------------------- | --------- | ------------------------------------------------------ |
| Daily Revenue Flash Report | Daily     | Revenue by dept, occupancy, ADR, RevPAR vs target      |
| Weekly Performance Summary | Weekly    | Day-by-day breakdown, week vs prior week, observations |
| Monthly Executive Report   | Monthly   | Revenue vs budget, YTD summary, expense breakdown      |
| 6-Month Forecast           | One-off   | Revenue and occupancy forecast with confidence bounds  |

---

## 💡 Key Insights from the Data

- **June was the strongest month** — LKR 21.2M total revenue and 73.49% occupancy
- **April had the highest expenses** — LKR 11.3M, impacting net revenue despite strong room sales
- **Website and Booking.com** are the top OTA channels by revenue contribution
- **Housekeeping and HR** are the largest expense departments
- **Net revenue improved steadily** from January (7.7M) to June (11.3M) — positive growth trend
<!-- - **Forecast shows December** as the projected peak month — aligned with Sri Lanka holiday season -->

---

<!-- ## 🚀 How to Use

1. Download the Excel file from the repository
2. Open in **Microsoft Excel 2016 or later**
3. Go to the **Dashboard** sheet
4. Use the **Month slicer** to filter all visuals dynamically
5. Go to **Forecast_Data** sheet to view the 6-month forecast with confidence bounds -->

---

## 👩‍💻 About

Built by **Yogeswaran Yogakrishanthi** as part of a data analytics portfolio.

- 🔗 [LinkedIn](https://www.linkedin.com/in/yogeswaran-yogakrishanthi/)
- 💻 [GitHub](https://github.com/yogadharsha98)
- 📧 yogeswarandharsha@gmail.com

---

> _This project demonstrates end-to-end Excel BI development — from raw CSV data through Power Query transformation, data modelling with DateTable relationships, PivotTable reporting, advanced Excel formulas, and interactive dashboard design._
