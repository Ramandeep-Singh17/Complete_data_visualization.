# 📊 Data Visualization in Python — Ultimate Notes

A beautifully structured, beginner-to-advanced guide covering **Matplotlib**, **Seaborn**, **Plotly**, and **Cufflinks**. Includes best practices, real-world use cases, code explanations, and when-to-use guidance.

---

## 🧰 Libraries & Best Use-Cases

| Library    | Purpose                                    | Best Use-Case                                            |
| ---------- | ------------------------------------------ | -------------------------------------------------------- |
| Matplotlib | Low-level core plotting                    | Full control over plots, static publication-ready charts |
| Seaborn    | Statistical plotting (built on Matplotlib) | Clean & complex plots with less code, great for EDA      |
| Plotly     | Interactive & animated charts              | Dashboards, web apps, responsive plots for exploration   |
| Cufflinks  | Connects Pandas with Plotly                | One-liner interactive plots from DataFrames              |

---

## 🐍 1. Matplotlib

```python
import matplotlib.pyplot as plt
```

### 🎯 Why Use It?

* Core plotting library in Python
* Gives full control over every plot element

### ✅ Example: Basic Line Plot

```python
plt.plot([1, 2, 3, 4], [10, 20, 25, 30])
plt.title('Simple Line Plot')
plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.show()
```

🔍 **Draws a simple line plot with custom axis labels and title.**

---

## 🐬 2. Seaborn

```python
import seaborn as sns
import pandas as pd
```

### 🎯 Why Use It?

* Built on Matplotlib
* Beautiful, theme-ready statistical plots
* Works smoothly with Pandas DataFrames

### ✅ Load Dataset & Basic Scatter

```python
tips = sns.load_dataset('tips')
sns.scatterplot(data=tips, x='total_bill', y='tip', hue='sex')
```

🔍 **Shows relationship between total bill and tip, colored by gender.**

### 📊 Common Plot Types with Use Cases:

| Plot Type   | Code Example                  | Use When...                                |
| ----------- | ----------------------------- | ------------------------------------------ |
| Scatter     | `sns.scatterplot(...)`        | Comparing two numeric variables            |
| Histogram   | `sns.histplot(...)`           | Checking distribution of one variable      |
| KDE Plot    | `sns.kdeplot(...)`            | Smooth distribution visualization          |
| Box Plot    | `sns.boxplot(...)`            | Show spread + detect outliers              |
| Violin Plot | `sns.violinplot(...)`         | Combo of KDE + box for deep distribution   |
| Count Plot  | `sns.countplot(x='col', ...)` | Frequency of categories                    |
| Heatmap     | `sns.heatmap(corr_matrix)`    | Visualize correlation between numeric cols |

---

## 📦 3. Plotly (Interactive Visualizations)

```python
import plotly.express as px
```

### 🎯 Why Use It?

* Create fully interactive charts
* Supports zoom, pan, hover, tooltips
* Ideal for web apps & dashboards

### ✅ Example: Interactive Scatter Plot

```python
fig = px.scatter(tips, x='total_bill', y='tip', title='Total Bill vs Tip')
fig.show()
```

🔍 **Hover, zoom, and pan enabled — great for deep exploration.**

### 📊 Plotly Chart Types & Use Cases:

| Chart Type | Code Example                      | Use When...                            |
| ---------- | --------------------------------- | -------------------------------------- |
| Line Plot  | `px.line(data, y='value')`        | Showing trends over time/sequences     |
| Bar Chart  | `px.bar(data, x='col', y='col2')` | Comparing category values              |
| Box Plot   | `px.box(data, x='col', y='col2')` | Showing spread/outliers per group      |
| Histogram  | `px.histogram(data, x='col')`     | Viewing distribution of single feature |

### ⚙️ Extra: GroupBy with Plotly

```python
avg_tips = tips.groupby('day', observed=True)['tip'].mean().reset_index()
fig = px.bar(avg_tips, x='day', y='tip', title='Average Tip per Day')
fig.show()
```

🔍 **Great for summarizing grouped data (e.g., mean tip per day).**

---

## 🔗 4. Cufflinks (Pandas + Plotly Bridge)

```python
import cufflinks as cf
from plotly.offline import iplot
cf.go_offline()
cf.set_config_file(world_readable=True, theme='pearl')
```

### 🎯 Why Use It?

* Allows direct interactive plotting from Pandas
* One-liners for quick EDA visuals

### ✅ Example: Scatter

```python
tips.iplot(kind='scatter', x='total_bill', y='tip', mode='markers')
```

🔍 **Pandas DataFrame plotted interactively without making a `fig`.**

### ✅ Box Plot from DataFrame

```python
tips[['total_bill', 'day']].iplot(kind='box', x='total_bill', y='day')
```

🔍 **Shows how total bill is spread across days.**

---

## 🧠 When to Use What?

| Goal                            | Best Tool  | Why                                                          |
| ------------------------------- | ---------- | ------------------------------------------------------------ |
| Static basic plots              | Matplotlib | Full control, great for fine-tuning & printing               |
| Quick statistical plots         | Seaborn    | Clean syntax, built-in support for DataFrames                |
| Interactive EDA & Dashboards    | Plotly     | Fully interactive, great for demos, web, and visual analysis |
| Fast interactive plotting w/ DF | Cufflinks  | Pandas + Plotly one-liner magic                              |

---

## 🏁 Capstone Project Highlights (Tips Dataset)

### ✅ Correlation Heatmap

```python
corr = tips.corr(numeric_only=True)
sns.heatmap(corr, annot=True)
```

🔍 **Great for understanding relationships between numerical columns.**

### ✅ Average Tip by Day (Plotly)

```python
avg_tips = tips.groupby('day', observed=True)['tip'].mean().reset_index()
fig = px.bar(avg_tips, x='day', y='tip', title='Average Tip per Day')
fig.show()
```

### ✅ Box Plot using Cufflinks

```python
tips[['total_bill','day']].iplot(kind='box', x='total_bill', y='day')
```

---

## ✅ Installation Notes (For Google Colab)

```python
!pip install plotly cufflinks
```

```python
import plotly.io as pio
pio.renderers.default = 'colab'  # Important for Plotly in Colab
```

---

🎉 **This guide helps you choose the right tool for the right scenario, with working examples and practical explanations. Perfect for GitHub, personal documentation, or interviews!**
