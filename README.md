# Student Performance Analysis

Analysis of 12 student records from an engineering college: attendance, marks, and department-wise performance. Built as a Google Sheets style workbook with formulas, conditional formatting, and charts.

## What it covers

- Marks statistics with SUM, AVERAGE, MAX, MIN, COUNT
- Pass/fail and low-attendance flags with IF()
- Sorting, filtering, and department grouping
- Conditional formatting for marks above 85 and attendance below 75%
- Department summary table
- Charts: department average (bar), student distribution (pie), marks histogram, and a performance heat map
- Answers to the interpretation questions in `docs/answers.md`

## Files

- `Student_Performance_Analysis.xlsx`: the workbook. Tabs are Records (raw data plus flag columns), Summary (department table and histogram bins), and Heatmap.
- `data/student_records.csv`: the raw dataset.
- `docs/formulas.md`: every formula used and what it does.
- `docs/answers.md`: answers to Part E.

## Quick results

- Total marks 897, average 74.75, from 12 students
- Highest 94 (Divya), lowest 48 (Anitha)
- 11 pass, 1 fail
- 2 students below 75% attendance
- IT has the highest department average (78.00)
- Attendance and marks correlation is about 0.97

## Notes

<!-- Write your own notes here: what was hard, what you'd change, which chart took the longest. -->
