# Section 2: Data Wrangling

## Overview

Data Wrangling is the process of cleaning, transforming, organizing, and preparing raw data for analysis.

---

# 1. Data Cleaning

## TRIM()

Removes extra spaces from text.

### Syntax

```excel
=TRIM(A2)
```

### Example

Before:

```
John     Doe
```

After:

```
John Doe
```

### Use Case

Cleaning imported employee or customer records.

---

## Remove Duplicates

### Steps

```
Data → Remove Duplicates
```

### Use Case

* Remove repeated employee records
* Remove duplicate customer entries

---

## Find & Replace

### Shortcut

```
Ctrl + H
```

### Example

Replace:

```
HR
```

With:

```
Human Resources
```

### Use Case

Standardizing values across datasets.

---

# 2. Case Transformation

## UPPER()

```excel
=UPPER(A2)
```

Converts text to uppercase.

---

## LOWER()

```excel
=LOWER(A2)
```

Converts text to lowercase.

---

## PROPER()

```excel
=PROPER(A2)
```

Converts text to Proper Case.

Example:

```
john doe → John Doe
```

---

# 3. Data Extraction Functions

## LEFT()

```excel
=LEFT(A2,4)
```

Returns characters from the left side.

---

## RIGHT()

```excel
=RIGHT(A2,4)
```

Returns characters from the right side.

---

## MID()

```excel
=MID(A2,start_position,num_characters)
```

Extracts characters from the middle.

---

## LEN()

```excel
=LEN(A2)
```

Returns the number of characters.

---

# 4. Combining Data

## Ampersand (&)

```excel
=A2 & " " & B2
```

---

## CONCAT()

```excel
=CONCAT(A2," ",B2)
```

---

## TEXTJOIN()

```excel
=TEXTJOIN(" ",TRUE,A2:C2)
```

### Advantage

Allows custom delimiters and ignores blanks.

---

# 5. Splitting Columns

## Text to Columns

```
Data → Text to Columns
```

### Delimited

Separates data using:

* Comma
* Space
* Tab
* Custom symbols

### Fixed Width

Separates data based on character positions.

---

# 6. Flash Fill

### Shortcut

```
Ctrl + E
```

### Example

Input:

```
John Doe
Jane Smith
```

Type:

```
John
```

Press:

```
Ctrl + E
```

Excel automatically extracts remaining first names.

---

# 7. Merge, Consolidate & Append

## Merge

Combine columns.

```excel
=A2&B2
```

---

## Consolidate

```
Data → Consolidate
```

Combine data from multiple worksheets.

---

## Append

Add records from one table below another table.

Use Case:
Monthly sales reports.

---

# 8. Date & Time Functions

## TODAY()

```excel
=TODAY()
```

Returns current date.

---

## Yesterday

```excel
=TODAY()-1
```

---

## Tomorrow

```excel
=TODAY()+1
```

---

## NOW()

```excel
=NOW()
```

Returns current date and time.

---

## YEAR()

```excel
=YEAR(A2)
```

---

## MONTH()

```excel
=MONTH(A2)
```

---

## DAY()

```excel
=DAY(A2)
```

---

## DATEDIF()

### Years

```excel
=DATEDIF(A2,B2,"Y")
```

### Months

```excel
=DATEDIF(A2,B2,"M")
```

### Days

```excel
=DATEDIF(A2,B2,"D")
```

### Use Case

* Age Calculation
* Employee Tenure

---

## NETWORKDAYS()

```excel
=NETWORKDAYS(A2,B2)
```

Counts working days.

### Use Case

Project duration and payroll.

---

## WORKDAY()

```excel
=WORKDAY(A2,30)
```

Returns date after 30 working days.

### Use Case

Deadline calculation.

---

## Gantt Chart Tracking

Uses:

* Start Date
* End Date
* Conditional Formatting

Useful for project planning and task tracking.

---

# 9. Logical Functions

## IF()

```excel
=IF(A2>50000,"High","Low")
```

---

## IFS()

```excel
=IFS(
A2>90,"A",
A2>80,"B",
A2>70,"C"
)
```

---

## SWITCH()

```excel
=SWITCH(A2,
"IT","Technology",
"HR","Human Resources",
"Unknown")
```

---

## AND()

```excel
=AND(A2>50000,B2="IT")
```

---

## OR()

```excel
=OR(A2>50000,B2="IT")
```

---

# 10. Arithmetic Functions

## SUM()

```excel
=SUM(A2:A10)
```

Returns total.

---

## AVERAGE()

```excel
=AVERAGE(A2:A10)
```

Returns mean.

---

## PRODUCT()

```excel
=PRODUCT(A2:A10)
```

Multiplies all values.

---

# 11. Lookup Functions

## VLOOKUP()

```excel
=VLOOKUP(1001,A2:E100,5,FALSE)
```

Searches vertically.

---

## HLOOKUP()

```excel
=HLOOKUP(1001,A1:E5,5,FALSE)
```

Searches horizontally.

---

## INDEX + MATCH()

```excel
=INDEX(E2:E100,MATCH(1001,A2:A100,0))
```

Industry preferred approach.

---

## XLOOKUP()

```excel
=XLOOKUP(1001,A2:A100,E2:E100)
```

Modern replacement for VLOOKUP.

---

## LOOKUP()

```excel
=LOOKUP(1001,A2:A20,B2:B20)
```

Legacy lookup function.

---

# 12. Error Handling

## IFERROR()

```excel
=IFERROR(A2/B2,"Error")
```

Prevents Excel errors from appearing in reports.

Common Errors:

* #DIV/0!
* #N/A
* #VALUE!
* #REF!

---

# 13. Sorting, Filtering & Grouping

## Sorting

```
Data → Sort
```

Examples:

* Salary High to Low
* Name A to Z

---

## Filter

### Shortcut

```
Ctrl + Shift + L
```

Filter records based on conditions.

---

## Advanced Filter

```
Data → Advanced Filter
```

Allows filtering using a criteria range.

---

## Group / Ungroup

### Group

```
Data → Group
```

### Shortcut

```
Alt + Shift + Right Arrow
```

### Ungroup

```
Alt + Shift + Left Arrow
```

Use Case:
Department-wise record organization.

---

## Subtotal

### Steps

1. Sort by Department
2. Data → Subtotal

Settings:

```
At each change in: Department
Function: Sum
Add subtotal to: Salary
```

### Benefits

* Department Totals
* Grand Total
* Outline Levels

---

# Key Learnings

* Clean raw data efficiently.
* Extract and transform text.
* Work with dates and deadlines.
* Apply logical decision-making formulas.
* Perform lookups and error handling.
* Organize data using sorting, filtering, grouping, and subtotals.

---

# Section Status

✅ Completed
