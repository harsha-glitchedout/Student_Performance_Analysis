# Formulas

Raw data is on the sheet **Records**, rows 2 to 13.
Columns: A = Student ID, B = Name, C = Department, D = Attendance %, E = Marks, F = Result, G = Attendance Flag

## Part B: Basic functions

| Task | Formula | Result |
|---|---|---|
| Total marks | `=SUM(Records!E2:E13)` | 897 |
| Average marks | `=AVERAGE(Records!E2:E13)` | 74.75 |
| Highest marks | `=MAX(Records!E2:E13)` | 94 |
| Lowest marks | `=MIN(Records!E2:E13)` | 48 |
| Number of students | `=COUNT(Records!E2:E13)` | 12 |

## Part B: IF() flags

Column F, Result (filled down to row 13):
`=IF(E2>=50,"Pass","Fail")`

Column G, Attendance Flag:
`=IF(D2<75,"Low attendance","OK")`

## Part C: Sorting, filtering, grouping

- **Sort by marks, high to low:** select A1:G13, then Data > Sort range > advanced range sorting options > sort by Marks, Z to A.
- **Filter marks above 80:** `=FILTER(Records!A2:E13,Records!E2:E13>80)` returns 5 rows (Arun, Divya, Nisha, Meena, Vijay).
- **Group by department:** sort by Department first, or use a pivot table with Department as rows.

## Part C: Conditional formatting

- Column E (Marks), custom formula `=E2>85`, green fill.
- Column D (Attendance %), custom formula `=D2<75`, red fill.

## Part C: Department summary (tab Summary, rows 2 to 5)

| Column | Formula (row 2 shown, copy down) |
|---|---|
| Students | `=COUNTIF(Records!C2:C13,A2)` |
| Average | `=AVERAGEIF(Records!C2:C13,A2,Records!E2:E13)` |
| Highest | `=MAXIFS(Records!E2:E13,Records!C2:C13,A2)` |
| Lowest | `=MINIFS(Records!E2:E13,Records!C2:C13,A2)` |
| Pass count | `=COUNTIFS(Records!C2:C13,A2,Records!E2:E13,">=50")` |

Row 6 is the overall row, using COUNT, AVERAGE, MAX, MIN, and COUNTIF on the whole column.

## Part C and D: Histogram bins (tab Summary, rows 11 to 16)

Each bin counts students whose marks fall in the range:
`=COUNTIFS(Records!E2:E13,">="&40,Records!E2:E13,"<="&49)`
Bins used: 40-49, 50-59, 60-69, 70-79, 80-89, 90-100.

## Part D: Charts

- **Bar chart (department average):** Summary A1:A5 as categories, C1:C5 as values.
- **Pie chart (student distribution):** Summary A1:A5 as categories, B1:B5 as values.
- **Histogram (marks distribution):** column chart over the bins in Summary B10:B16, gap width set to 0 so the bars touch.

## Part D: Heat map (tab Heatmap)

Row 2 holds the lower mark bound and row 3 the upper bound for each band. Rows 4 to 7 hold departments.

`=COUNTIFS(Records!$C$2:$C$13,$A4,Records!$E$2:$E$13,">="&B$2,Records!$E$2:$E$13,"<="&B$3)`

Select B4:D7 and apply a color scale under Format > Conditional formatting. Darker cells mean more students in that band.

## Part E: Quick answers as formulas

- Students below 75% attendance: `=COUNTIF(Records!D2:D13,"<75")` gives 2
- Top 3 marks: `=LARGE(Records!E2:E13,1)`, then 2, then 3
- Top 3 names: `=INDEX(Records!B2:B13,MATCH(LARGE(Records!E2:E13,1),Records!E2:E13,0))`, same pattern for 2 and 3
- Attendance vs marks correlation: `=CORREL(Records!D2:D13,Records!E2:E13)` gives about 0.97
