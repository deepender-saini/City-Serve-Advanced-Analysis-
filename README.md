# CityServe — Advanced Excel Analytics

## Project overview

CityServe Service Operations & Revenue Analytics is a portfolio project built around a synthetic service-business dataset. The workbook contains an Excel dashboard and supporting analyses for bookings, revenue, service mix, cities, customers, status, and ratings.

## Business questions

- How do booking volume and revenue change by month?
- Which cities and services contribute the most revenue?
- How does customer mix differ by customer type?
- How do booking outcomes relate to customer ratings?
- Where should management focus capacity and service improvement?

## Dataset

- Raw records: 40,010
- Deduplicated analytical records: 40,000
- Duplicate Booking_ID records removed: 10
- Period: FY 2026
- Data type: Synthetic / simulated portfolio data

## Workbook contents

| Sheet | Purpose |
|---|---|
| Dashboard | Interactive KPI dashboard with City, Service Type, Customer Type, and Booking Status filters |
| Raw_Data | Source dataset |
| Clean_Data | Deduplicated analytical dataset |
| Monthly_Analysis | Monthly booking and revenue analysis |
| City_Analysis | City-level performance |
| Service_Analysis | Service performance |
| Status_Analysis | Booking status analysis |
| Customer_Analysis | Customer-type analysis |
| Data_Dictionary | Field definitions and business rules |
| Dashboard_Calc | Hidden dashboard calculation support |

## Excel features

- Excel tables and data validation
- Formula-based calculations and summaries
- Dashboard filters and charts
- Conditional formatting
- KPI reporting and date-based analysis

## Known workbook follow-up

The workbook still needs data and formula review before its revenue and completion-rate results should be treated as final:

- 12 completed bookings have negative Service_Cost and Final_Amount values. Their Service_Cost totals -23,962,384. Verify them against the source; correct or exclude invalid values in the analytical data using a documented rule, and keep Raw_Data unchanged.
- Clean_Data retains blanks in Area (817 records), Payment_Mode (439), and Average_Rating (203). Decide whether to fill these fields or retain them as unknown, and document that choice.
- Completion Rate is affected by the Booking Status filter in the denominator. Update the dashboard and monthly calculations so the denominator counts all eligible bookings while honoring the other filters; the rate should not exceed 100%.
- Data_Dictionary omits definitions for Year, Month_No, Month_Name, Duplicate_ID_Flag, Missing_Area_Flag, Missing_Payment_Flag, and Missing_Rating_Flag.
- The dashboard filter helper lists in columns P:R are visible. Hide those support columns.

## Tools

Microsoft Excel | Advanced Excel | Excel charts | Data analysis | Dashboarding

## Portfolio note

This is a synthetic portfolio project created to demonstrate analytics skills. It does not represent confidential company data, client data, or employment experience.

## Author

**Deepender Saini**

Business Analyst | Data Analyst

Delhi, India
