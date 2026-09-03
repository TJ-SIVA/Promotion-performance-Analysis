
# Promotional Coupon Performance Analysis — Brothers BBQ

End-to-end data analytics project analyzing promotional coupon performance for a food business (chicken leg/wings/lollipop stall), covering ~5,200 transactions over a 4-month period (Feb–May). The project spans the full pipeline — data collection, cleaning, modeling, analysis, and dashboarding — built and delivered solo.

## Preview Of The DashBoard
### **[Dashborad Link](https://app.powerbi.com/links/fpY0GJpYA-?ctid=406a6e9a-2c6d-4cd4-b5fc-299c924534e7&pbi_source=linkShare)**
![Dashboard Preview](https://github.com/TJ-SIVA/Promotion-performance-Analysis/blob/main/Reports/Promotional%20_cupon_performance.png)


## Business Problem
The business runs promotional coupon campaigns but had no visibility into who actually redeems them, whether they drive new customer acquisition or just discount existing loyal traffic, and how redemption trends move month over month. This project builds that visibility from raw transaction logs to a decision-ready dashboard.

## Tech Stack
| Layer | Tools |
|---|---|
| Data collection & storage | MySQL |
| Data cleaning & preprocessing | Python (Pandas, NumPy) |
| Database connectivity | ODBC connection (MySQL → Power BI) |
| Data modeling | Power BI Data Modeling, star-schema relationships |
| Transformation | Power Query |
| Calculations | DAX |
| Reporting / validation | Excel |
| Dashboarding | Power BI |

## Pipeline
1. **Data Collection** — Raw daily stock/sales logs and transaction-level sales data (customer, order channel, item, coupon, payment, rating, review) sourced from operational records.
2. **Cleaning (Python/Pandas)** — Handled missing values (age, ratings), resolved stock-reconciliation mismatches, dropped redundant columns, standardized data types (dates, categorical fields), and exported cleaned datasets.
3. **Database Load** — Cleaned data loaded into a MySQL database (`bbq_brothers`) via SQLAlchemy; verified with query round-trips.
4. **Connection & Modeling** — Connected Power BI to MySQL via ODBC; built a relational data model linking transactions, stock, and customer dimensions.
5. **Transformation (Power Query)** — Additional shaping, type conversions, and calculated columns ahead of modeling.
6. **Analysis (DAX + Excel)** — Built measures for coupon redemption rate, revenue, profit, customer segmentation (Loyal/New/Returning), and channel behavior; cross-validated key figures in Excel.
7. **Dashboarding (Power BI)** — Interactive report with month and customer-category slicers, KPI cards, trend lines, and segment breakdowns.

## Key Insights
- **781K total revenue / 404K profit** across 2,095 customers and 5,238 transactions, holding a stable ~50–53% margin every month.
- Coupon redemption **rate stayed flat (~15%)** even as raw transaction volume declined ~12% over the period — coupons kept working proportionally even as footfall dropped.
- **Loyal customers drive 57–63% of all coupon redemptions** each month; New customers ~33–40%; Returning customers under 5% — the program functions more as a retention tool than an acquisition driver.
- **No meaningful age skew** in coupon usage — redemption behavior is consistent across all age brackets.
- **Channel behavior differs sharply**: Phone Call orders are dominated by Loyal customers, while Walk-in orders show a much more balanced Loyal/New mix — making Walk-in the stronger channel for reaching new customers.
- Revenue per transaction **increased** over the period even as customer count fell, partially offsetting the volume decline.

## Data Quality Notes
- Identified and flagged a stock-reconciliation mismatch present in 37% of daily records (`total_stock_kg` ≠ sum of item-level stock).
- ~15% of transactions were missing customer age; handled explicitly rather than silently dropped, to preserve analysis integrity.

## Files
- `Sales_data_preprocessing.ipynb` — daily stock/sales cleaning and MySQL load
- `Transaction_data_Preprocessing.ipynb` — transaction-level cleaning, type handling, MySQL/Parquet export
- Power BI `Model_Report.pbix` dashboard (promotional coupon performance report)

## Author
Built independently — data collection through dashboard delivery.
