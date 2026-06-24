# Section 1: Excel Fundamentals Notes

## 1. Excel Layout

### Workbook

A workbook is an Excel file that can contain multiple worksheets.

### Worksheet

A worksheet is a single spreadsheet page inside a workbook.

### Rows and Columns

* Rows are horizontal and numbered (1, 2, 3...)
* Columns are vertical and labeled (A, B, C...)

### Cell

The intersection of a row and column.

Example:

```text
A1
B5
D10
```

---

## 2. Navigation Shortcuts

| Shortcut         | Purpose              |
| ---------------- | -------------------- |
| Ctrl + Arrow Key | Move to edge of data |
| Ctrl + Home      | Go to A1             |
| Ctrl + End       | Go to last used cell |
| Ctrl + Page Up   | Previous sheet       |
| Ctrl + Page Down | Next sheet           |

### Use Case

Useful when working with large datasets containing thousands of rows.

---

## 3. Selecting Data

### Select Entire Row

```text
Shift + Space
```

### Select Entire Column

```text
Ctrl + Space
```

### Select Continuous Range

```text
Shift + Click
```

### Select Non-Adjacent Cells

```text
Ctrl + Click
```

---

## 4. Copy and Paste

### Copy

```text
Ctrl + C
```

### Paste

```text
Ctrl + V
```

### Paste Special

```text
Ctrl + Alt + V
```

### Use Case

Paste only:

* Values
* Formulas
* Formatting

---

## 5. Fill Handle

Small square at the bottom-right corner of a selected cell.

### Uses

* Copy formulas
* Continue series
* Fill dates
* Fill numbers

Example:

```text
1
2
```

Drag down:

```text
1
2
3
4
5
```

---

## 6. Basic Arithmetic Operations

### Addition

```excel
=A1+B1
```

### Subtraction

```excel
=A1-B1
```

### Multiplication

```excel
=A1*B1
```

### Division

```excel
=A1/B1
```

### Use Case

Basic calculations for sales, salaries, expenses, and profits.

---

## 7. Built-in Functions

### SUM

```excel
=SUM(A1:A10)
```

Adds all numbers.

### AVERAGE

```excel
=AVERAGE(A1:A10)
```

Calculates average value.

### MIN

```excel
=MIN(A1:A10)
```

Returns smallest value.

### MAX

```excel
=MAX(A1:A10)
```

Returns largest value.

### COUNT

```excel
=COUNT(A1:A10)
```

Counts numeric values.

---

## 8. Cell Referencing

### Relative Reference

```excel
=A1
```

Changes automatically when copied.

Example:

```excel
=A1+B1
```

Dragged down becomes:

```excel
=A2+B2
```

### Absolute Reference

```excel
=$A$1
```

Does not change when copied.

### Mixed Reference

Column Fixed:

```excel
=$A1
```

Row Fixed:

```excel
=A$1
```

### Use Case

Tax calculations, commission rates, fixed constants, lookup tables.

---

## 9. AutoFill Techniques

### Fill Numbers

```text
1
2
```

Drag to generate sequence.

### Fill Dates

```text
01-Jan-2025
```

Drag to continue dates.

### Fill Months

```text
January
```

Drag to generate months.

---

## 10. Saving Workbook

### Save

```text
Ctrl + S
```

### Save As

```text
F12
```

### Important

Use:

```text
.xlsx
```

for Excel work.

Avoid:

```text
.csv
```

when using:

* Formatting
* Grouping
* Charts
* Pivot Tables
* Multiple Sheets

CSV only stores raw data.

---

## Key Learnings

* Understand Excel interface and navigation.
* Use formulas for calculations.
* Master cell references.
* Use Fill Handle efficiently.
* Save workbooks as .xlsx for advanced Excel features.

---

## Common Mistakes

1. Using CSV instead of XLSX.
2. Forgetting Absolute References ($).
3. Dragging formulas from the wrong row.
4. Confusing Workbook and Worksheet.
5. Editing formula results instead of source cells.
6. Assuming RANDBETWEEN values remain fixed.
7. Not saving the workbook after changes.

---

## Section Status

✅ Completed
