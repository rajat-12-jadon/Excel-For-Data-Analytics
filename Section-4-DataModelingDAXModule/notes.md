# Section 4: Data Modeling & Power Pivot (Part 1)

## Overview

Power Pivot is an advanced Excel feature used for **Data Modeling**, creating **relationships** between multiple tables, and performing calculations using **DAX (Data Analysis Expressions)**.

It allows working with millions of rows of data efficiently and forms the foundation of Power BI.

---

# What is Data Modeling?

Data Modeling is the process of connecting multiple related tables to create a single analytical model.

Instead of storing everything in one huge table, data is separated into multiple related tables.

### Example

Employees Table

| EmployeeID | Name | DepartmentID |
| ---------- | ---- | ------------ |
| 101        | Raj  | D01          |
| 102        | Aman | D02          |

Departments Table

| DepartmentID | Department |
| ------------ | ---------- |
| D01          | HR         |
| D02          | IT         |

Sales Table

| SaleID | EmployeeID | Amount |
| ------ | ---------- | ------ |
| S101   | 101        | 25000  |
| S102   | 102        | 31000  |

Relationships connect these tables.

---

# Advantages of Data Modeling

* Eliminates duplicate data
* Improves performance
* Reduces workbook size
* Makes reporting easier
* Supports Pivot Tables and Power BI

---

# What is Power Pivot?

Power Pivot is Excel's Data Modeling engine.

It allows you to:

* Import large datasets
* Create relationships
* Build calculated columns
* Create measures
* Write DAX formulas
* Analyze millions of records

---

# Opening Power Pivot

```text
Power Pivot → Manage
```

---

# Importing Data into Power Pivot

If tables are in the same workbook:

```text
Select Table
↓
Power Pivot
↓
Add to Data Model
```

If data is in another workbook:

```text
Power Pivot
↓
Get External Data
↓
From Other Sources
```

---

# Diagram View

Diagram View displays relationships between tables.

Benefits:

* Easy visualization
* Drag-and-drop relationships
* Better understanding of data model

---

# Data View

Data View displays actual table records.

Used for:

* Creating Calculated Columns
* Viewing imported data
* Checking data types

---

# Relationships

Relationships connect tables using common columns.

Example

Employees

```text
EmployeeID
```

↓

Sales

```text
EmployeeID
```

---

Departments

```text
DepartmentID
```

↓

Employees

```text
DepartmentID
```

---

Date

```text
Date
```

↓

Sales

```text
SaleDate
```

---

# Types of Relationships

## One-to-Many (1:*)

Most common relationship.

Example

One Department

↓

Many Employees

---

One Employee

↓

Many Sales

---

## One-to-One

Rarely used.

Example

Employee

↓

Employee Passport

---

## Many-to-Many

Supported using bridge tables.

Used in advanced models.

---

# Primary Key

A column containing unique values.

Examples

```text
EmployeeID
DepartmentID
ProductID
```

---

# Foreign Key

A column referencing another table's primary key.

Example

Sales table contains:

```text
EmployeeID
```

which references

Employees table.

---

# Star Schema

Recommended model.

```text
             Date
               |
               |
Products ---- Sales ---- Employees
               |
          Departments
```

Advantages

* Faster
* Cleaner
* Easy to maintain
* Preferred in Power BI

---

# Snowflake Schema

Dimension tables are normalized.

Example

```text
Country
    |
State
    |
City
    |
Customers
    |
Sales
```

Advantages

* Less redundancy

Disadvantages

* More relationships
* Slightly slower

---

# Star Schema vs Snowflake

| Star Schema | Snowflake Schema |
| ----------- | ---------------- |
| Faster      | Slower           |
| Simple      | Complex          |
| Less Joins  | More Joins       |
| Preferred   | Less Common      |

---

# Calculated Columns

Created row-by-row.

Stored in memory.

Example

```DAX
Annual Salary = Employees[Salary] * 12
```

Characteristics

* Stored physically
* Uses row context
* Increases model size

---

# Measures

Calculated only when required.

Example

```DAX
Total Sales = SUM(Sales[Amount])
```

Characteristics

* Not stored
* Uses filter context
* Faster than calculated columns

---

# Calculated Column vs Measure

| Calculated Column    | Measure              |
| -------------------- | -------------------- |
| Row Context          | Filter Context       |
| Stored               | Calculated on demand |
| Increases model size | Lightweight          |
| Used in rows         | Used in Pivot Tables |

---

# DAX (Data Analysis Expressions)

DAX is the formula language used in:

* Power Pivot
* Power BI
* SSAS Tabular

Used for

* Aggregation
* Filtering
* Time Intelligence
* Business Calculations

---

# DAX Formula Structure

```DAX
Measure Name = FUNCTION(Table[Column])
```

Example

```DAX
Total Sales = SUM(Sales[Amount])
```

---

# Types of DAX Functions

* Aggregation Functions
* Logical Functions
* Filter Functions
* Relationship Functions
* Text Functions
* Date & Time Functions
* Time Intelligence Functions
* Math Functions
* Statistical Functions

---

# Best Practices

* Always create relationships before writing DAX.
* Use Star Schema whenever possible.
* Prefer Measures over Calculated Columns.
* Use meaningful table and column names.
* Keep fact tables large and dimension tables small.
* Avoid duplicate keys.

---

# Key Learnings

* Understood Data Modeling.
* Learned Power Pivot interface.
* Created relationships.
* Understood Star & Snowflake Schema.
* Learned Primary & Foreign Keys.
* Understood Calculated Columns vs Measures.
* Introduced to DAX.

---

# Section 4: Data Modeling & Power Pivot (Part 2)

# DAX Aggregation Functions

Aggregation functions summarize data from one or more rows.

---

## SUM()

Returns the total of a numeric column.

### Syntax

```DAX
SUM(Table[Column])
```

### Example

```DAX
Total Sales = SUM(Sales[SalesAmount])
```

### Use Cases

* Total Revenue
* Total Salary
* Total Profit

---

## SUMX()

Iterates row by row before calculating.

### Syntax

```DAX
SUMX(Table, Expression)
```

### Example

```DAX
Total Revenue =
SUMX(
    Sales,
    Sales[Quantity] * Sales[UnitPrice]
)
```

### Difference

| SUM                  | SUMX                                 |
| -------------------- | ------------------------------------ |
| Adds values directly | Evaluates an expression for each row |

---

## AVERAGE()

Returns the average value.

```DAX
Average Salary =
AVERAGE(Employees[Salary])
```

---

## AVERAGEX()

Average after evaluating an expression.

```DAX
Average Revenue =
AVERAGEX(
Sales,
Sales[Quantity]*Sales[UnitPrice]
)
```

---

## MIN()

Returns minimum value.

```DAX
Minimum Salary =
MIN(Employees[Salary])
```

---

## MAX()

Returns maximum value.

```DAX
Highest Sale =
MAX(Sales[SalesAmount])
```

---

## COUNT()

Counts numeric values.

```DAX
COUNT(Sales[SalesAmount])
```

---

## COUNTA()

Counts non-empty values.

```DAX
COUNTA(Employees[EmployeeName])
```

---

## DISTINCTCOUNT()

Counts unique values.

```DAX
Total Employees =
DISTINCTCOUNT(Sales[EmployeeID])
```

---

# Logical Functions

---

## IF()

Checks a condition.

### Syntax

```DAX
IF(condition, true_result, false_result)
```

### Example

```DAX
Salary Category =
IF(
Employees[Salary]>60000,
"High",
"Low"
)
```

---

## SWITCH()

Cleaner alternative to multiple IF statements.

```DAX
Department Name =
SWITCH(
Employees[DepartmentID],
1,"HR",
2,"IT",
3,"Finance",
"Unknown"
)
```

---

## AND()

Returns TRUE if all conditions are true.

```DAX
AND(
Employees[Salary]>50000,
Employees[Age]>25
)
```

---

## OR()

Returns TRUE if any condition is true.

```DAX
OR(
Employees[Salary]>50000,
Employees[DepartmentID]=1
)
```

---

## NOT()

Reverses TRUE/FALSE.

```DAX
NOT(
Employees[Salary]>50000
)
```

---

# Filter Functions

These are among the most important DAX functions.

---

## CALCULATE()

Changes filter context.

### Syntax

```DAX
CALCULATE(
Expression,
Filter
)
```

### Example

```DAX
IT Sales =
CALCULATE(
SUM(Sales[SalesAmount]),
Employees[Department]="IT"
)
```

### Use Cases

* Department-wise Sales
* Year-wise Revenue
* Region-wise Profit

---

## FILTER()

Returns rows satisfying a condition.

### Syntax

```DAX
FILTER(Table, Condition)
```

### Example

```DAX
High Salary =
FILTER(
Employees,
Employees[Salary]>70000
)
```

Often used inside CALCULATE.

---

## ALL()

Removes filters.

```DAX
Overall Sales =
CALCULATE(
SUM(Sales[SalesAmount]),
ALL(Sales)
)
```

Useful for percentage calculations.

---

## ALLEXCEPT()

Removes all filters except selected columns.

```DAX
ALLEXCEPT(
Sales,
Sales[Department]
)
```

---

# Relationship Functions

---

## RELATED()

Fetches value from a related table.

### Example

```DAX
Department Name =
RELATED(Departments[DepartmentName])
```

---

## RELATEDTABLE()

Returns related rows.

```DAX
RELATEDTABLE(Sales)
```

---

## LOOKUPVALUE()

Looks up values without relationships.

### Example

```DAX
Department =
LOOKUPVALUE(
Departments[DepartmentName],
Departments[DepartmentID],
Employees[DepartmentID]
)
```

---

# Text Functions

---

## LEFT()

```DAX
LEFT(
Employees[EmployeeName],
3
)
```

---

## RIGHT()

```DAX
RIGHT(
Employees[EmployeeName],
3
)
```

---

## MID()

```DAX
MID(
Employees[EmployeeName],
2,
4
)
```

---

## LEN()

```DAX
LEN(
Employees[EmployeeName]
)
```

---

## UPPER()

```DAX
UPPER(
Employees[EmployeeName]
)
```

---

## LOWER()

```DAX
LOWER(
Employees[EmployeeName]
)
```

---

## CONCATENATE()

```DAX
CONCATENATE(
Employees[FirstName],
Employees[LastName]
)
```

---

## FORMAT()

Formats numbers or dates.

```DAX
FORMAT(
Sales[SaleDate],
"DD-MMM-YYYY"
)
```

---

# Common Interview Questions

### Difference between SUM and SUMX?

SUM simply adds values.

SUMX evaluates an expression row by row.

---

### Difference between FILTER and CALCULATE?

FILTER returns a table.

CALCULATE changes filter context.

---

### Difference between RELATED and LOOKUPVALUE?

RELATED requires relationships.

LOOKUPVALUE works even without relationships.

---

### Difference between COUNT and DISTINCTCOUNT?

COUNT counts all numeric values.

DISTINCTCOUNT counts unique values.

---

# Best Practices

* Prefer Measures over Calculated Columns.
* Keep DAX formulas simple.
* Use meaningful measure names.
* Avoid duplicate calculations.
* Use CALCULATE whenever filter context changes.
* Create relationships before writing DAX.

---

# Key Learnings

* Learned Aggregation Functions.
* Learned Logical Functions.
* Understood CALCULATE.
* Understood FILTER.
* Learned ALL and ALLEXCEPT.
* Learned RELATED and LOOKUPVALUE.
* Learned Text Functions.
* Understood DAX best practices.

---

# Section 4: Data Modeling & Power Pivot (Part 3)

# Time Intelligence Functions

Time Intelligence functions are used to compare sales, revenue, profit, and other KPIs over different periods such as daily, monthly, quarterly, or yearly.

These functions require a **Date Table** that:

* Contains every date without gaps.
* Is marked as a Date Table.
* Has a relationship with the Fact table.

---

# DATEADD()

Returns data shifted by a specified time interval.

### Syntax

```DAX
DATEADD(Date[Date], -1, YEAR)
```

### Example

```DAX
Previous Year Sales =
CALCULATE(
    SUM(Sales[SalesAmount]),
    DATEADD(Date[Date], -1, YEAR)
)
```

### Use Cases

* Compare this year vs last year
* Monthly comparisons
* Quarterly reports

---

# DATESYTD()

Returns dates from the beginning of the year until the current date.

### Syntax

```DAX
DATESYTD(Date[Date])
```

### Example

```DAX
YTD Sales =
CALCULATE(
    SUM(Sales[SalesAmount]),
    DATESYTD(Date[Date])
)
```

### Use Cases

* Running yearly sales
* Financial reports

---

# TOTALYTD()

Calculates cumulative totals from the beginning of the year.

### Syntax

```DAX
TOTALYTD(
Expression,
Date[Date]
)
```

### Example

```DAX
Total Sales YTD =
TOTALYTD(
SUM(Sales[SalesAmount]),
Date[Date]
)
```

---

# SAMEPERIODLASTYEAR()

Returns the same dates from the previous year.

### Example

```DAX
Last Year Sales =
CALCULATE(
SUM(Sales[SalesAmount]),
SAMEPERIODLASTYEAR(Date[Date])
)
```

### Use Cases

* YOY Analysis
* Growth Reports

---

# PREVIOUSYEAR()

Returns all dates of the previous year.

```DAX
PREVIOUSYEAR(Date[Date])
```

---

# NEXTYEAR()

Returns all dates of the next year.

```DAX
NEXTYEAR(Date[Date])
```

---

# FIRSTDATE()

Returns the first date in current filter context.

```DAX
FIRSTDATE(Date[Date])
```

---

# LASTDATE()

Returns the last available date.

```DAX
LASTDATE(Date[Date])
```

---

# Mathematical Functions

---

## ABS()

Returns absolute value.

```DAX
ABS(Sales[Profit])
```

---

## ROUND()

Rounds to specified decimal places.

```DAX
ROUND(
Sales[Amount],
2
)
```

---

## INT()

Returns integer portion.

```DAX
INT(Sales[Amount])
```

---

## MOD()

Returns remainder.

```DAX
MOD(15,4)
```

Result

```text
3
```

---

## POWER()

Raises number to a power.

```DAX
POWER(5,2)
```

Result

```text
25
```

---

## SQRT()

Returns square root.

```DAX
SQRT(144)
```

Result

```text
12
```

---

# Statistical Functions

---

## MEDIAN()

Returns median value.

```DAX
MEDIAN(Sales[SalesAmount])
```

---

## MEDIANX()

Median after evaluating expression.

```DAX
MEDIANX(
Sales,
Sales[Quantity]*Sales[UnitPrice]
)
```

---

## STDEV.P()

Population Standard Deviation.

```DAX
STDEV.P(Sales[SalesAmount])
```

---

## STDEV.S()

Sample Standard Deviation.

```DAX
STDEV.S(Sales[SalesAmount])
```

---

## VAR.P()

Population Variance.

```DAX
VAR.P(Sales[SalesAmount])
```

---

## VAR.S()

Sample Variance.

```DAX
VAR.S(Sales[SalesAmount])
```

---

# Creating KPIs

A KPI (Key Performance Indicator) helps measure business performance.

Example

```text
Target Sales = ₹10,00,000

Actual Sales = ₹12,50,000
```

Status

```text
✔ Above Target
```

or

```text
✖ Below Target
```

Power Pivot allows adding KPI indicators using:

* Green
* Yellow
* Red

traffic lights.

---

# Hierarchies

Hierarchy allows drilling down data.

Example

```text
Year
 └── Quarter
      └── Month
            └── Day
```

Another Example

```text
Country
 └── State
      └── City
```

Benefits

* Easy navigation
* Drill Down
* Drill Up

---

# Performance Optimization

To improve Power Pivot performance:

* Remove unnecessary columns.
* Use integer keys instead of text.
* Avoid duplicate data.
* Use Measures instead of Calculated Columns whenever possible.
* Create proper relationships.
* Use Star Schema.
* Avoid circular dependencies.

---

# Common Mistakes

❌ No Date Table

Time Intelligence functions will not work.

---

❌ Duplicate Primary Keys

Relationships cannot be created.

---

❌ Using Calculated Columns instead of Measures

Increases model size.

---

❌ No Relationships

RELATED() and Pivot analysis will fail.

---

❌ Wrong Data Types

Date functions and aggregations may produce incorrect results.

---

# Power Pivot Best Practices

* Create a Date Table first.
* Name measures clearly.
* Keep fact tables separate.
* Keep dimensions normalized.
* Hide unnecessary columns.
* Use Diagram View frequently.
* Save the workbook regularly.
* Keep backup versions.

---

# Power Pivot Workflow

```text
Import Tables
        ↓
Create Relationships
        ↓
Star Schema
        ↓
Calculated Columns
        ↓
Measures
        ↓
DAX Functions
        ↓
Time Intelligence
        ↓
KPIs
        ↓
Hierarchies
        ↓
Pivot Table
        ↓
Dashboard
```

---

# Real-World Applications

Power Pivot is widely used for:

* Sales Dashboards
* HR Analytics
* Financial Reports
* Inventory Management
* Customer Analytics
* Marketing Reports
* Business Intelligence
* Power BI Data Models

---

# Interview Questions

### What is Power Pivot?

Excel's in-memory data modeling engine used for handling large datasets and writing DAX.

---

### Difference between Power Query and Power Pivot?

| Power Query        | Power Pivot              |
| ------------------ | ------------------------ |
| ETL Tool           | Data Modeling Tool       |
| Cleans Data        | Analyzes Data            |
| Uses M Language    | Uses DAX                 |
| Import & Transform | Relationships & Measures |

---

### What is DAX?

Data Analysis Expressions language used in Power Pivot and Power BI.

---

### Difference between Row Context and Filter Context?

**Row Context**

Works one row at a time.

Example

Calculated Columns.

**Filter Context**

Works on filtered data.

Example

Measures.

---

### Why is Star Schema preferred?

* Faster
* Easier relationships
* Better performance
* Simpler DAX

---

### Difference between Measure and Calculated Column?

Calculated Column

* Stored in memory
* Row-wise calculation

Measure

* Calculated on demand
* Better performance

---

# Key Learnings

* Learned Time Intelligence Functions.
* Understood KPIs.
* Created Hierarchies.
* Learned Mathematical Functions.
* Learned Statistical Functions.
* Improved Power Pivot performance.
* Understood common mistakes.
* Learned Power Pivot workflow.
* Prepared for interview questions.

---

# Section Summary

✔ Data Modeling

✔ Relationships

✔ Star Schema

✔ Snowflake Schema

✔ Power Pivot

✔ Calculated Columns

✔ Measures

✔ DAX Fundamentals

✔ Aggregation Functions

✔ Logical Functions

✔ Filter Functions

✔ Relationship Functions

✔ Text Functions

✔ Time Intelligence

✔ Mathematical Functions

✔ Statistical Functions

✔ KPIs

✔ Hierarchies

✔ Performance Optimization

✔ Interview Questions

---

# Section Status

✅ Section 4 Completed
