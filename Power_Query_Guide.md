# Power Query Guide

This guide documents a repeatable way to prepare the CityServe service-booking data with Power Query. It describes the workflow used for this project; it does not add a saved query connection by itself.

## 1. Import the source

1. Open the workbook and go to Raw_Data.
2. Select a cell in the source table.
3. Choose Data > From Table/Range.
4. Rename the query to CityServe_Clean. Keep Raw_Data unchanged.

## 2. Set data types

Set Booking_ID and category fields to Text; Booking_Date to Date; Year and Month_No to Whole Number; Month_Name to Text; Service_Cost, Discount, and Final_Amount to Decimal Number or Currency; and Average_Rating to Decimal Number.

Check that dates and numeric fields were parsed correctly before adding transformations.

## 3. Clean text fields

For text columns, use Transform > Format > Trim and Clean. Review distinct values in City, Service_Type, Customer_Type, Booking_Status, and Payment_Mode, and standardize inconsistent spelling or whitespace. Keep the original source table unchanged.

## 4. Add or validate date fields

Use Booking_Date to create or validate Year, Month_No, and Month_Name. Power Query custom-column expressions:

```text
Date.Year([Booking_Date])
Date.Month([Booking_Date])
Date.MonthName([Booking_Date])
```

Confirm Month_No and Month_Name agree for dates across the year.

## 5. Flag missing values

Create Missing_Area_Flag, Missing_Payment_Flag, and Missing_Rating_Flag. Example custom column for Area:

```text
if [Area] = null or Text.Trim(Text.From([Area])) = "" then "Missing" else "OK"
```

Use the same pattern for Payment_Mode and Average_Rating. Keep missing ratings null; if you label missing categories as Unknown, retain the missing flags. The current source has 817 missing Area values, 439 missing Payment_Mode values, and 203 missing Average_Rating values.

## 6. Review duplicate Booking_ID values

Group or sort by Booking_ID to inspect duplicates, then keep the approved record according to a documented business rule. Do not rely on an undocumented Remove Duplicates choice.

The current source contains 40,010 rows and 10 extra duplicate-ID rows. The deduplicated output currently has 40,000 unique Booking_ID values.

## 7. Validate financial fields

Check for negative Service_Cost values, discounts outside the accepted range, and whether Final_Amount equals Service_Cost minus Discount. Investigate exceptions against the source; do not silently overwrite or discard them.

The current file has 12 Completed records with negative Service_Cost values. Review these before treating revenue totals as final.

## 8. Load the result

Choose Home > Close & Load To, load the approved output as a table on Clean_Data, and confirm downstream analysis uses the refreshed output. Preserve Raw_Data as the source.

## 9. Refresh and reconcile

After source changes, choose Data > Refresh All. Check row counts, unique Booking_ID values, missing-value flags, financial totals, and monthly/city/service/status/customer summaries.

## Workbook note

The workbook currently stored in this repository does not contain saved Power Query definitions. Follow these steps in Excel and save the query connection if you want the workbook to refresh from Raw_Data. The workbook also does not currently contain saved PivotTable objects.