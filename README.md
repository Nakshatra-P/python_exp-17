# Experiment 17: Basic Charts and Visual Encoding

## Aim:
To study and implement different types of data visualization techniques using Matplotlib and Seaborn libraries in Python for representing trends, comparisons, distributions, and relationships in data.

---

## Theory:

### 1. Importing Libraries

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
```

- `import matplotlib.pyplot as plt`
  - Imports the `pyplot` module from Matplotlib.
  - Used for creating graphs such as line charts, bar graphs, histograms, and scatter plots.
  - `plt` is an alias used to call plotting functions easily.

- `import seaborn as sns`
  - Imports the Seaborn library.
  - Seaborn is built on top of Matplotlib and provides advanced statistical visualizations with attractive themes.

- `import pandas as pd`
  - Imports the Pandas library.
  - Used for handling and analyzing tabular data using DataFrames.

---

### 2. Creating Dataset

```python
data = {
    'Days': ['Mon','Tue','Wed','Thu','Fri'],
    'Study_Hours': [2,3,2.5,4,3.5],
    'Marks':[50,60,55,70,65],
    'Attendance': [60,70,65,80,75],
    'Sleep_Hours': [6,7,6,8,7],
    'Assignments_Completed': [1,2,1,3,2]
}

df = pd.DataFrame(data)
```

- A dictionary named `data` is created to store student-related information.

- `'Days'`
  - Stores weekday names.

- `'Study_Hours'`
  - Stores number of study hours per day.

- `'Marks'`
  - Stores marks obtained by students.

- `'Attendance'`
  - Stores attendance percentage.

- `'Sleep_Hours'`
  - Stores daily sleeping hours.

- `'Assignments_Completed'`
  - Stores number of assignments completed.

- `pd.DataFrame(data)`
  - Converts the dictionary into a DataFrame.
  - A DataFrame organizes data into rows and columns for analysis.

- `df`
  - Variable used to store the DataFrame.

---

### 3. Line Chart

```python
plt.plot(df['Days'], df['Study_Hours'], marker='o')

plt.title("Nakshatra")
plt.xlabel("Days")
plt.ylabel("Study Hours")

plt.show()
```

- `plt.plot()`
  - Creates a line graph.

- `df['Days']`
  - Used as X-axis values.

- `df['Study_Hours']`
  - Used as Y-axis values.

- `marker='o'`
  - Displays circular markers on data points.

- `plt.title("Nakshatra")`
  - Adds a title to the graph.

- `plt.xlabel("Days")`
  - Labels the X-axis.

- `plt.ylabel("Study Hours")`
  - Labels the Y-axis.

- `plt.show()`
  - Displays the graph window.

Line charts are used to visualize trends over time.

---

### 4. Advanced Line Chart

```python
plt.figure(figsize=(7,4))

plt.plot(df['Days'], df['Study_Hours'],
         marker='o',
         color='green',
         label='Study Hours')

plt.plot(df['Days'], df['Marks'],
         marker='s',
         color='red',
         label='Marks')

plt.legend()

plt.show()
```

- `plt.figure(figsize=(7,4))`
  - Creates a graph window with width 7 and height 4.

- `color='green'`
  - Sets line color to green.

- `marker='o'`
  - Adds circular markers.

- `label='Study Hours'`
  - Assigns label for legend.

- `marker='s'`
  - Adds square markers.

- `color='red'`
  - Sets line color to red.

- `plt.legend()`
  - Displays legend box with labels.

This graph compares multiple datasets together.

---

### 5. Bar Graph

```python
plt.bar(df['Days'],
        df['Marks'],
        color='green',
        edgecolor='black')

plt.grid(axis='x',
         linestyle='--',
         alpha=0.5)

plt.grid(axis='y',
         linestyle='--',
         alpha=0.5)

plt.show()
```

- `plt.bar()`
  - Creates a bar graph.

- `color='green'`
  - Sets bar color.

- `edgecolor='black'`
  - Adds black border to bars.

- `plt.grid()`
  - Adds grid lines.

- `axis='x'`
  - Adds grid lines only on X-axis.

- `axis='y'`
  - Adds grid lines only on Y-axis.

- `linestyle='--'`
  - Creates dashed grid lines.

- `alpha=0.5`
  - Sets transparency of grid lines.

Bar graphs are used for comparing categorical data.

---

### 6. Advanced Bar Graph

```python
bars = plt.bar(df['Days'], df['Marks'])

for bar in bars:
    y = bar.get_height()

    plt.text(
        bar.get_x() + bar.get_width()/2,
        y,
        str(y),
        ha='center',
        va='bottom'
    )
```

- `bars = plt.bar()`
  - Stores all bars in a variable.

- `for bar in bars`
  - Loops through each bar.

- `bar.get_height()`
  - Retrieves height of the bar.

- `plt.text()`
  - Displays text on graph.

- `bar.get_x()`
  - Gets X-position of bar.

- `bar.get_width()/2`
  - Centers text horizontally.

- `str(y)`
  - Converts numeric value into string.

- `ha='center'`
  - Horizontally aligns text at center.

- `va='bottom'`
  - Vertically aligns text at bottom.

This graph displays exact values on top of bars.

---

### 7. Multiple Bar Graph

```python
import numpy as np

x = np.arange(len(df['Days']))
width = 0.40

plt.bar(x - width/2,
        df['Study_Hours'],
        width,
        label='Study Hours')

plt.bar(x + width/2,
        df['Marks'],
        width,
        label='Marks')
```

- `import numpy as np`
  - Imports NumPy library for numerical operations.

- `np.arange()`
  - Generates evenly spaced values.

- `len(df['Days'])`
  - Finds number of categories.

- `width = 0.40`
  - Sets width of bars.

- `x - width/2`
  - Shifts first bars to left.

- `x + width/2`
  - Shifts second bars to right.

This graph compares multiple datasets side by side.

---

### 8. Histogram

```python
marks = [50,60,55,70,65,75,80,85,90,45,68,72,77,82,88]

mean_value = np.mean(marks)

plt.hist(marks,
         bins=3,
         color='skyblue',
         edgecolor='black')

plt.axvline(mean_value,
            color='red',
            linestyle='--',
            linewidth=2,
            label='Mean')
```

- `plt.hist()`
  - Creates histogram.

- `bins=3`
  - Divides data into 3 intervals.

- `color='skyblue'`
  - Sets histogram color.

- `edgecolor='black'`
  - Adds border to histogram bars.

- `np.mean(marks)`
  - Calculates average value.

- `plt.axvline()`
  - Draws vertical line.

- `linewidth=2`
  - Sets line thickness.

Histograms help understand frequency distribution.

---

### 9. Scatter Plot

```python
plt.scatter(df['Study_Hours'],
            df['Marks'])
```

- `plt.scatter()`
  - Creates scatter plot.

- `df['Study_Hours']`
  - Used as X-axis values.

- `df['Marks']`
  - Used as Y-axis values.

Scatter plots help identify relationships between variables.

---

### 10. Conditional Scatter Plot

```python
df['Result'] = ['Fail', 'Pass', 'Fail', 'Pass', 'Pass']

colors = [
    'red' if r == 'Fail'
    else 'green'
    for r in df['Result']
]

plt.scatter(
    df['Study_Hours'],
    df['Marks'],
    c=colors
)
```

- `df['Result']`
  - Creates a new column.

- List comprehension
  - Assigns colors based on conditions.

- `'red' if r == 'Fail'`
  - Sets failed students to red color.

- `'green'`
  - Sets passed students to green color.

- `c=colors`
  - Assigns colors to scatter points.

This plot visually separates categories using colors.

---

### 11. Seaborn Line Plot

```python
sns.lineplot(
    x='Day',
    y='Sales',
    data=df1,
    errorbar=None
)
```

- `sns.lineplot()`
  - Creates line plot using Seaborn.

- `x='Day'`
  - Sets X-axis column.

- `y='Sales'`
  - Sets Y-axis column.

- `data=df1`
  - Specifies dataset.

- `errorbar=None`
  - Removes confidence interval bars.

---

### 12. Seaborn Bar Plot

```python
sns.barplot(
    x='Day',
    y='Sales',
    data=df1,
    errorbar=None
)
```

- `sns.barplot()`
  - Creates statistical bar graph.

- `errorbar=None`
  - Removes error bars.

---

### 13. Seaborn Histogram

```python
sns.histplot(df1['Sales'], bins=5)
```

- `sns.histplot()`
  - Creates histogram using Seaborn.

- `bins=5`
  - Divides data into 5 intervals.

---

### 14. Seaborn Scatter Plot

```python
sns.scatterplot(
    x='Sales',
    y='Profit',
    data=df1
)
```

- `sns.scatterplot()`
  - Creates scatter plot with Seaborn styling.

- `x='Sales'`
  - Defines X-axis data.

- `y='Profit'`
  - Defines Y-axis data.

---

## Conclusion:

Different types of visualizations such as line charts, bar graphs, histograms, and scatter plots were successfully implemented using Matplotlib and Seaborn. These visualizations helped in understanding trends, distributions, and relationships within datasets. The experiment demonstrated how visual encoding improves data interpretation and analysis.
