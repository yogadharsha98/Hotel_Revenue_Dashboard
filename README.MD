# 🏨 Hotel Revenue & Performance Dashboard

> **Power BI dashboard** analysing hotel operational and financial performance across 6 months (January – June 2025).

![Dashboard Preview](./images/Monthly_Revenue.JPG)

---

## 📊 Dashboard Overview

This dashboard was built to help hotel management make data-driven decisions by tracking key revenue, occupancy, and expense metrics across all departments — updated dynamically by month using an interactive slicer.

---

## ✨ Features

| Section                     | Description                                                                                           |
| --------------------------- | ----------------------------------------------------------------------------------------------------- |
| **KPI Cards**               | Total Revenue, Net Revenue, Occupancy Rate, Total Expenses — updated per selected month               |
| **Revenue Breakdown**       | Horizontal bar chart showing Room Revenue, Restaurant Revenue, Net Revenue, and Expenses side by side |
| **Booking Source Analysis** | Revenue by channel — Direct, Agoda, Booking.com, Walk-in, Travel Agent, Website                       |
| **Monthly Revenue Trend**   | Bar chart showing Jan–Jun revenue progression                                                         |
| **Expenses by Department**  | Horizontal bar chart — Finance, HR, Maintenance, Sales, Spa, F&B, Housekeeping                        |
| **Occupancy Summary**       | Table showing Rooms Available, Rooms Occupied, Occupancy Rate, ADR, RevPAR                            |
| **Monthly Detail Table**    | Room Revenue, Restaurant Revenue, Total Revenue, Expenses, Net Revenue, Occupancy % by month          |
| **Net Revenue Line Chart**  | Trend line showing net revenue movement Jan–Jun                                                       |
| **Month Slicer**            | Interactive filter — select any month to update all visuals dynamically                               |

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

| Tool                 | Purpose                                             |
| -------------------- | --------------------------------------------------- |
| **Power BI Desktop** | Dashboard development and visualisation             |
| **DAX**              | Measures — SUM, DIVIDE, AVERAGE, CALCULATE, DATEADD |
| **Power Query**      | Data transformation and cleaning                    |
| **Microsoft Excel**  | Source data preparation and validation              |
| **Data Modelling**   | Star schema — DateTable linked to all fact tables   |

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

All tables connected through a central **DateTable** using a star schema — enabling accurate cross-table filtering via the month slicer.

---

## 📐 DAX Measures Created

```dax
Total Room Revenue = SUM(Reservations[RoomRevenue])

Total Restaurant Revenue = SUM(RestaurantSales[TotalAmount])

Total Revenue = [Total Room Revenue] + [Total Restaurant Revenue]

Total Expenses = SUM(Expenses[Amount])

Net Revenue = [Total Revenue] - [Total Expenses]

Avg Occupancy Rate = AVERAGE(Occupancy[OccupancyRate])

ADR = DIVIDE(SUM(Reservations[RoomRevenue]), SUM(Occupancy[RoomsOccupied]))

RevPAR = DIVIDE(SUM(Reservations[RoomRevenue]), SUM(Occupancy[RoomsAvailable]))
```

---

## 📁 Repository Structure

```
hotel-revenue-dashboard-powerbi/
│
├── README.md                        ← You are here
├── dashboard_preview.png            ← Dashboard screenshot
├── Hotel_Revenue_Dashboard.pdf      ← Exported PDF report
│
└── data/
    ├── Reservations.csv             ← 1,000 reservation records
    ├── RestaurantSales.csv          ← 1,500 F&B transaction records
    ├── Occupancy.csv                ← 181 daily occupancy records
    ├── Expenses.csv                 ← 279 expense records
    ├── Customers.csv                ← 100 customer profiles
    ├── Rooms.csv                    ← 50 room definitions
    └── Employees.csv                ← 36 employee records
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

## 💡 Key Insights from the Data

- **June was the strongest month** — LKR 21.2M total revenue and 73.49% occupancy
- **April had the highest expenses** — LKR 11.3M, impacting net revenue despite strong room sales
- **Website and Booking.com** are the top OTA channels by revenue contribution
- **Housekeeping and HR** are the largest expense departments
- **Net revenue improved steadily** from January (7.7M) to June (11.3M) — positive growth trend

---

## 🚀 How to Use

1. Download the `.pbix` file (if uploaded) or view the PDF export
2. Open in **Power BI Desktop**
3. Use the **Month slicer** on the top right to filter all visuals by month
4. All KPI cards, charts, and tables update dynamically based on selection

---

## 👩‍💻 About

Built by **Yogeswaran Yogakrishanthi** as part of a data analytics portfolio.

- 🔗 [LinkedIn](https://www.linkedin.com/in/yogeswaran-yogakrishanthi/)
- 💻 [GitHub](https://github.com/yogadharsha98)
- 📧 yogeswarandharsha@gmail.com

---

> _This project demonstrates end-to-end BI development — from raw CSV data through Power Query transformation, data modelling, DAX measure creation, and interactive dashboard design in Power BI._
