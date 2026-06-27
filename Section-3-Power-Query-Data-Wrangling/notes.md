# Section 3: Power Query Based Wrangling

## Overview

Power Query is Excel's ETL (Extract, Transform, Load) tool used to import, clean, transform, and prepare data before analysis. It automates repetitive data-cleaning tasks and can refresh transformations whenever the source data changes.

---

# 1. Importing Data

Power Query can import data from multiple sources.

## Supported Sources

* Excel Workbook
* CSV / Text Files
* SQL Server
* Access Database
* Folder
* Web
* SharePoint
* JSON / XML

### Steps

```text
Data → Get Data
```

### Use Cases

* Import monthly reports
* Connect to databases
* Load CSV datasets

---

# 2. Cleaning Raw Data

## Remove Null Values

### Steps

```text
Home → Remove Rows → Remove Blank Rows
```

### Use Case

Remove incomplete records.

---

## Trim

Removes leading and trailing spaces.

### Steps

```text
Transform → Format → Trim
```

Example

Before

```text
"   John Doe   "
```

After

```text
"John Doe"
```

---

## Clean

Removes non-printable characters.

### Steps

```text
Transform → Format → Clean
```

### Use Case

Cleaning imported system-generated data.

---

## Replace Errors

### Steps

```text
Transform → Replace Errors
```

### Use Case

Replace errors with:

```text
0
Unknown
Blank
```

instead of showing:

```text
Error
```

---

## Change Data Types

### Available Types

* Whole Number
* Decimal Number
* Text
* Date
* Time
* Date/Time
* Currency
* Boolean

### Steps

```text
Transform → Data Type
```

### Importance

Correct data types improve calculations and analysis.

---

## Fill Down

Copies the value from the cell above into blank cells.

### Steps

```text
Transform → Fill → Down
```

### Example

Before

```text
HR
(blank)
(blank)
IT
(blank)
```

After

```text
HR
HR
HR
IT
IT
```

---

# 3. Transforming Data

## Split Column

### Options

* By Delimiter
* By Number of Characters
* By Positions

### Steps

```text
Transform → Split Column
```

---

## Rename Column

Double-click the column header or

```text
Right Click → Rename
```

---

## Extract

Extract parts of text.

Examples

* First Characters
* Last Characters
* Text Before Delimiter
* Text After Delimiter

### Steps

```text
Transform → Extract
```

---

## Transpose

Converts rows into columns and columns into rows.

### Steps

```text
Transform → Transpose
```

---

## Pivot Column

Converts row values into columns.

### Example

Before

```text
Department
IT
HR
Finance
```

After

```text
IT | HR | Finance
```

### Steps

```text
Transform → Pivot Column
```

---

## Unpivot Columns

Converts columns into rows.

Useful when preparing data for Pivot Tables or Power BI.

### Steps

```text
Transform → Unpivot Columns
```

---

# 4. Adding Columns

## Custom Column

Create a new column using formulas.

### Steps

```text
Add Column → Custom Column
```

### Example

```text
Salary * 12
```

to calculate annual salary.

---

## Index Column

Adds sequential numbers.

### Steps

```text
Add Column → Index Column
```

Options

* From 0
* From 1

### Use Cases

* Unique IDs
* Ranking
* Record Numbers

---

# 5. Merge Queries

### Purpose

Combine two tables using a common key.

Similar to:

```text
SQL JOIN
VLOOKUP
XLOOKUP
```

### Types

* Left Outer
* Right Outer
* Inner
* Full Outer
* Left Anti
* Right Anti

### Steps

```text
Home → Merge Queries
```

### Example

Employee Table

*

Department Table

↓

Employee with Department Details

---

# 6. Append Queries

### Purpose

Stack one table below another.

Example

January Sales

*

February Sales

↓

Combined Sales Table

### Steps

```text
Home → Append Queries
```

### Use Cases

* Monthly reports
* Yearly reports
* Multiple CSV files

---

# 7. Query Steps (Applied Steps)

Every transformation is recorded in the **Applied Steps** pane.

Example

```text
Source
Navigation
Changed Type
Removed Columns
Filtered Rows
Split Column
Renamed Columns
```

### Benefits

* Automatic refresh
* Easy debugging
* Repeatable transformations

---

# Refresh Query

Whenever source data changes:

```text
Right Click Query → Refresh
```

or

```text
Data → Refresh All
```

Power Query automatically applies every saved transformation.

---

# Advantages of Power Query

* No manual repetitive work
* Easy to refresh
* Handles large datasets efficiently
* No formulas required for many transformations
* Excellent integration with Power BI

---

# Power Query vs Excel Formulas

| Power Query                | Excel Formulas              |
| -------------------------- | --------------------------- |
| ETL Tool                   | Cell-based calculations     |
| Refreshable                | Manual updates              |
| Handles large datasets     | Better for smaller datasets |
| Step-based transformations | Formula-based calculations  |
| Ideal for data cleaning    | Ideal for analysis          |

---

# Best Practices

* Keep raw data unchanged.
* Always assign correct data types.
* Rename columns with meaningful names.
* Remove unnecessary columns early.
* Use Merge instead of repeated VLOOKUPs when combining tables.
* Use Append for combining similar datasets.
* Refresh queries instead of repeating manual work.

---

# Key Learnings

* Import data from multiple sources.
* Clean and transform raw datasets.
* Create custom and index columns.
* Merge and append datasets efficiently.
* Understand Applied Steps and query refresh.
* Build reusable data-cleaning workflows.

---

# Section Status

✅ Completed