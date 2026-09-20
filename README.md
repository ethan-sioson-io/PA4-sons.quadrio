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

### Code for the Problem:
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

### Code for the Problem:
```ruby
TrackAverage = df.groupby('Track')['Average'].mean().reset_index()
TrackAverage
```
- `TrackAverage = df.groupby('Track')['Average'].mean().reset_index()` - This code takes the dataframe and groups it under the categories under the `Track` column. It then only reads the `Average` column and calculates the average for each group (`Communication`, `Instrumentation`, `Microelectronics`) and stores all of this in `TrackAverage`. Finally, `.reset_index()` starts counting rows from 0 instead of the original row numbers.
- `TrackAverage` - This displays the dataframe `TrackAverage`.

```ruby
GenderAverage = df.groupby('Gender')['Average'].mean().reset_index()
GenderAverage
```
- `GenderAverage = df.groupby('Gender')['Average'].mean().reset_index()` - This code takes the dataframe and groups it under the categories under the `Gender` column. It then only reads the `Average` column and calculates the average for each group (`Female`, `Male`) and stores all of this in `GenderAverage`. Finally, `.reset_index()` starts counting rows from 0 instead of the original row numbers.
- `GenderAverage` - This displays the dataframe `GenderAverage`.

```ruby
HometownAverage = df.groupby('Hometown')['Average'].mean().reset_index()
HometownAverage
```
- `HometownAverage = df.groupby('Hometown')['Average'].mean().reset_index()` - This code takes the dataframe and groups it under the categories under the `Hometown` column. It then only reads the `Average` column and calculates the average for each group (`Luzon`, `Mindanao`, `Visayas`) and stores all of this in `HometownAverage`. Finally, `.reset_index()` starts counting rows from 0 instead of the original row numbers.

```ruby
fig, axes = plt.subplots(1,3,figsize=(16,5))

axes[0].bar(TrackAverage['Track'], TrackAverage['Average'])
axes[0].set_title('Mean Average by Track')
axes[0].set_xlabel('Track Names')
axes[0].set_ylabel('Mean Scores')

axes[1].bar(GenderAverage['Gender'], GenderAverage['Average'])
axes[1].set_title('Mean Average by Gender')
axes[1].set_xlabel('Genders')

axes[2].bar(HometownAverage['Hometown'], HometownAverage['Average'])
axes[2].set_title('Mean Average by Hometown')
axes[2].set_xlabel('Hometown Names')

plt.tight_layout(rect=[0, 0.25, 1, 1])

findings = (
    "1. For the Track feature, the [Insert Track] category achieved the highest sample mean Average.\n"
    "2. For the Gender feature, the [Insert Gender] category recorded the highest sample mean Average.\n"
    "3. For the Hometown feature, students from [Insert Hometown] had the highest sample mean Average."
)

fig.text(0.5, 0.05, findings, ha='center', fontsize=12)

plt.show()
```
The explanation for this code will be separated into: **Chart Preparation** and **Findings Code**.
### Chart Preparation Code:
```ruby
fig, axes = plt.subplots(1,3,figsize=(16,5))

axes[0].bar(TrackAverage['Track'], TrackAverage['Average'])
axes[0].set_title('Mean Average by Track')
axes[0].set_xlabel('Track Names')
axes[0].set_ylabel('Mean Scores')

axes[1].bar(GenderAverage['Gender'], GenderAverage['Average'])
axes[1].set_title('Mean Average by Gender')
axes[1].set_xlabel('Genders')

axes[2].bar(HometownAverage['Hometown'], HometownAverage['Average'])
axes[2].set_title('Mean Average by Hometown')
axes[2].set_xlabel('Hometown Names')

plt.tight_layout(rect=[0, 0.25, 1, 1])
```

- `fig, axes = plt.subplots(1,3,figsize=(16,5))` - This code initializes fig and axes, the white background and the arrays respectively. `1,3` tells the code to create 1 row containing 3 columns, which translates to three charts. `figsize=(16,5)` dictates the size of the figure itself, with it being 16 inches wide and 5 inches tall.

- `axes[0].bar(TrackAverage['Track'], TrackAverage['Average'])` - `axes[0].bar` tells the code to start at the first chart to the left. Changing the value to 1 or 2 changes which chart to focus one to either the second or third chart respectively. It also creates a bar chart. `TrackAverage['Track']` provides the labels for the X-axis while `TrackAverage['Average']` provides the values for the Y-axis from the `TrackAverage` dataframe.<br>

- **Several alterations to this line of code includes:**
   - Changing which axes to focus on (`axes[1]` or `axes[2]`).
   - Changing the X-axis labels according to `GenderAverage['Gender']` or `HometownAverage['Hometown']`.
   - Changing Y-axis labels according to `GenderAverage['Average']` or `HometownAverage['Average']`


- `axes[0].set_title('Mean Average by Track')` - This code adds text to the main title and sets it to "Mean Average by Track". The other charts have the titles "Mean Average by Gender" and "Mean Average by Hometown".
- `axes[0].set_xlabel('Track Names')` - This code adds text to the xlabel and sets it to "Track Names". The other charts have the titles "Genders" and "Hometown Names".
- `axes[0].set_ylabel('Mean Scores')` - This code adds text to the ylabel and sets it to "Mean Scores".
- `plt.tight_layout(rect=[0, 0.25, 1, 1])` - This code adjusts the spacing between the charts. `rect=[0, 0.25, 1, 1]` follows the format `rect=[left, bottom, right, top]`. For this figure, 0 means the charts start at the left edge, 0.25 means the charts start 25% higher than the canvas, 1 means it extends the charts to the right and top edges.

### Findings Code:
```ruby
findings = (
    "1. For the Track feature, the [Insert Track] category achieved the highest sample mean Average.\n"
    "2. For the Gender feature, the [Insert Gender] category recorded the highest sample mean Average.\n"
    "3. For the Hometown feature, students from [Insert Hometown] had the highest sample mean Average."
)

fig.text(0.5, 0.05, findings, ha='center', fontsize=12)

plt.show()
```
- `findings = ("1. For the ...")` - This code creates a string of the three sentences and stores them in `findings`. 
- `fig.text(0.5, 0.05, findings, ha='center', fontsize=12)` - This code places the string of text based on the conditions set inside the parenthesis. 0.5 and 0.05 are the X and Y coordinates according to the canvas. It sets the text 50% across while setting the Y 5% from the bottom edge of the canvas. `ha=center` sets the horizontal alignment of the text to center. While `fontsize=12` sets the size of the font to 12.
- `plt.show()` - This code displays the figure according to the code set above.
