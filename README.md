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
```
- `import pandas as pd` - This imports the pandas library in the code and gives it the `pd` call name.
```ruby
import matplotlib.pyplot as plt
```
- `import matplotlib.pyplot as plt` - This imports the matplotlib library in the code and gives it the `plt` call name.
```ruby
df = pd.read_excel('board2.xlsx')
df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
df
```
- `df = pd.read_excel('board2.xlsx')` - This finds a spreadsheet file named `cars.xlsx` in the user's folder and stores the 2D table in `df`.
- `df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)` - This calculates the average grade for every student by getting the average of the values under `Math`, `Electronics`, `GEAS`, and `Communication`. It then stores this value in a new column with the name `Average`. This code calculates the average of the aforementioned values using `.mean()`, while `axis=1` makes sure that the values are being calculated horizontally each row, not every row.
-`df` - This displays the dataframe `df`.
```ruby
VisComm = df.loc[(df['Hometown']=='Visayas')&(df['Track']=='Communication'), ['Name', 'Gender', 'Math', 'Electronics','Average']].reset_index()
VisComm
```
- `VisComm = df.loc[(df['Hometown']=='Visayas')&(df['Track']=='Communication'), ['Name', 'Gender', 'Math', 'Electronics','Average']].reset_index()` - This code selects the rows whose `Hometown` and `Track` information are **ONLY** `Visayas` and `Communication` respectively. Afterwards, it retains the columns with the names `Name`, `Gender`, `Math`, `Electronics`, and `Average`. Finally, `.reset_index()` starts counting rows from 0 instead of the original row numbers.
```ruby
len(VisComm)
```
-`len(VisComm)` - This code counts the number of rows in the dataframe `VisComm`.

## B. VISAYAS FEMALE DATAFRAME

Create a second DataFrame named `VisFemale` containing students whose `Hometown` is `Visayas` and whose `Gender` is `Female`. Retain only:
```Name, Track, GEAS, Electronics, Average```<br><br>
Display `VisFemale`. Then display only the rows of `VisFemale` whose `Average` is at least 60. Do not overwrite `VisFemale` when performing this second filter.

```ruby
VisFemale = df.loc[(df['Hometown']=='Visayas')&(df['Gender']=='Female'), ['Name', 'Track', 'GEAS', 'Electronics','Average']].reset_index()
VisFemale
```
- `VisFemale = df.loc[(df['Hometown']=='Visayas')&(df['Gender']=='Female'), ['Name', 'Track', 'GEAS', 'Electronics','Average']].reset_index()` - This code selects the rows whose `Hometown` and `Gender` information are **ONLY** `Visayas` and `Female` respectively. Afterwards, it retains the columns with the names `Name`, `Track`, `GEAS`, `Electronics`, and `Average`. Finally, `.reset_index()` starts counting rows from 0 instead of the original row numbers.
- `VisFemale` - This code displays the dataframe `VisFemale`.

```ruby
VisFemaleOverSixty = VisFemale.loc[(VisFemale['Average']>60)].reset_index()
VisFemaleOverSixty
```
- `VisFemaleOverSixty = VisFemale.loc[(VisFemale['Average']>60)].reset_index()` - This code locates the rows from the dataframe `VisFemale` whose average value is strictly greater than 60 and stores them in the dataframe `VisFemaleOverSixty`. Finally, `.reset_index()` starts counting rows from 0 instead of the original row numbers.
- `VisFemaleOverSixty` - This code displays the dataframe `VisFemaleOverSixty`.

## C. CATEGORY-AVERAGE VISUALIZATION
Examine how the recorded `Average` differs across the three categorical features `Track`, `Gender`, and `Hometown`.<br>
**a.**  For each feature, compute the mean of `Average` for every category using Pandas.<br>
**b.** Display the three summary tables.<br>
**c.** Create one figure containing three bar charts: mean `Average` by `Track`, by `Gender`, and by `Hometown`.<br>
**d.** Below the figure, write three concise statements identifying the category with the highest sample mean for each feature.<br>
