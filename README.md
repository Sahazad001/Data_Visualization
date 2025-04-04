# Data Visualization Assignment

## Overview
This repository contains a data visualization assignment that focuses on using Python and popular visualization libraries like Matplotlib, Seaborn, and Plotly to represent different datasets graphically.

## Tasks
Below are the tasks included in this assignment:

### 1. 3D Scatter Plot
**Objective:** Using the given dataset, generate a 3D scatter plot to visualize the distribution of data points in a three-dimensional space.

```python
import numpy as np
import pandas as pd
import plotly.express as px

# Set seed for reproducibility
np.random.seed(30)

# Create dataset
data = {
    'X': np.random.uniform(-10, 10, 300),
    'Y': np.random.uniform(-10, 10, 300),
    'Z': np.random.uniform(-10, 10, 300)
}

# Convert to DataFrame
df = pd.DataFrame(data)

# Create 3D scatter plot using Plotly
fig_3d_scatter = px.scatter_3d(df, x='X', y='Y', z='Z', color='Z',
                               title="3D Scatter Plot of Random Data Distribution",
                               labels={'X': 'X Axis', 'Y': 'Y Axis', 'Z': 'Z Axis'},
                               color_continuous_scale=px.colors.sequential.Viridis)

# Show the plot
fig_3d_scatter.show()
```

### 2. Violin Plot for Student Grades
**Objective:** Using the student grades dataset, create a violin plot to display the distribution of scores across different grade categories.

```python
import seaborn as sns
import matplotlib.pyplot as plt

np.random.seed(15)

data_grades = {
    'Grade': np.random.choice(['A', 'B', 'C', 'D', 'F'], 200),
    'Score': np.random.randint(50, 100, 200)
}

df_grades = pd.DataFrame(data_grades)

fig_violin = px.violin(df_grades, x='Grade', y='Score', box=True, points='all',
                        title="Distribution of Scores Across Grade Categories", color='Grade')
fig_violin.show()
```

### 3. Heatmap for Sales Data
**Objective:** Using the sales data, generate a heatmap to visualize the variation in sales across different months and days.

```python
np.random.seed(20)

data_sales = {
    'Month': np.random.choice(['Jan', 'Feb', 'Mar', 'Apr', 'May'], 100),
    'Day': np.random.choice(range(1, 31), 100),
    'Sales': np.random.randint(1000, 5000, 100)
}

df_sales = pd.DataFrame(data_sales)

# Pivot data for heatmap
sales_pivot = df_sales.pivot_table(index='Day', columns='Month', values='Sales', aggfunc='mean')

# Heatmap for sales variation using Plotly
import plotly.graph_objects as go

fig_heatmap = go.Figure(data=go.Heatmap(
    z=sales_pivot.values,
    x=sales_pivot.columns,
    y=sales_pivot.index,
    colorscale=px.colors.sequential.Viridis,
    colorbar=dict(title="Sales")
))

fig_heatmap.update_layout(
    title="Sales Variation Across Months and Days",
    xaxis_title="Month",
    yaxis_title="Day"
)

fig_heatmap.show()
```

## Requirements
To run the visualizations, make sure you have the following Python libraries installed:

```sh
pip install numpy pandas plotly seaborn matplotlib
```

## Usage
Clone the repository and run the scripts in a Jupyter Notebook or a Python environment that supports Plotly visualization.

```sh
git clone https://github.com/your-username/data-visualization-assignment.git
cd data-visualization-assignment
python visualization_script.py  # Replace with the actual script name
```


