# ECE 2112 Programming Assessment 4
**Ethan Joseph L. Sioson** | **2ECE-C**<br>
_This repository contains three programming problems which covers **Module 4 - Data Wrangling and Visualization.**_<br>
**Objectives:**<br>
1. Filter tabular data using several categorical and numerical conditions;
2. Construct focused DataFrames by selecting relevant features;
3. Summarize the relationship between categorical features and a numerical variable; and
4. Communicate a data comparison using clear and correctly labeled plots.

**Instructions:**<br>
Use the same **ECE Board Exam 2** dataset supplied for Experiment 4. Work in a Jupyter Notebook using Pandas and a Python plotting library used in class. Use the dataset’s existing column labels, including `Name`, `Gender`, `Track`, `Hometown`, `Math`, `GEAS`, `Electronics`, and `Average`.
- Derive all tables and plot values from the dataset. Do not manually type rows, category means, or plotted values.
- When applying more than one condition, make every condition explicit in the filtering expression.
- Keep the original DataFrame unchanged.
- Every graph must have a title, axis labels, readable category labels, and a consistent scale appropriate to the data.

1. Filter tabular data using several categorical and numerical conditions;
2. Construct focused DataFrames by selecting relevant features;
3. Summarize the relationship between categorical features and a numerical variable; and
4. Communicate a data comparison using clear and correctly labeled plots.

## A. VISAYAS COMMUNICATION DATAFRAME

Create a DataFrame named VisComm containing students whose Hometown is Visayas and whose Track is Communication. Retain only these columns, in the stated order:
```Name, Gender, Math, Electronics, Average```<br><br>
Display the resulting DataFrame and its number of rows. Both filtering conditions must be applied to the source dataset before the columns are selected.

### Code for the Problem:
```ruby
import pandas as pd

