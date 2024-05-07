# Python a brief introduction to Plotly

**Plotly** is a popular library for creating interactive charts and visualizations in Python

It's well-suited for use in **VSCode**, which is a powerful editor that supports Python development through **extensions** like **Python** and **Jupyter**

Below are a few simple examples to help you get started with Plotly in VSCode

## 1. Basic Line Chart

First, ensure you have Plotly installed in your Python environment. You can install it via pip:

```
pip install plotly
```

Here's a simple example of a line chart:

```python
import plotly.graph_objects as go

# Create data
x_data = [0, 1, 2, 3, 4]
y_data = [0, 1, 4, 9, 16]

# Create a figure
fig = go.Figure()

# Add line plot
fig.add_trace(go.Scatter(x=x_data, y=y_data, mode='lines+markers', name='Line plot'))

# Add title and labels
fig.update_layout(title='Simple Line Chart', xaxis_title='X Axis', yaxis_title='Y Axis')

# Show plot
fig.show()
```

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/2e8e8773-0654-46e6-b601-c8765a20e1b4)

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/3aaf8618-3998-4366-a936-24e2043006ea)

## 2. Bar Chart

Here's how to create a simple bar chart:

```python
import plotly.graph_objects as go

# Create data
categories = ['Apples', 'Oranges', 'Bananas']
values = [400, 300, 500]

# Create a figure
fig = go.Figure()

# Add bar plot
fig.add_trace(go.Bar(x=categories, y=values, name='Fruit Production'))

# Add title and labels
fig.update_layout(title='Simple Bar Chart', xaxis_title='Fruits', yaxis_title='Quantity')

# Show plot
fig.show()
```

## 3. Pie Chart

This example demonstrates how to create a pie chart:

```python
import plotly.graph_objects as go

# Create data
labels = ['Pizza', 'Burgers', 'Pasta']
values = [450, 300, 250]

# Create a figure
fig = go.Figure()

# Add pie chart
fig.add_trace(go.Pie(labels=labels, values=values, name='Food Preference'))

# Add title
fig.update_layout(title='Simple Pie Chart')

# Show plot
fig.show()
```

## 4. Setting Up VSCode for Plotly

To make the most out of using Plotly in VSCode, you might want to use the Jupyter Notebook support within VSCode

This allows you to write and execute code in cells, view plots inline, and more interactively develop your visualizations

Install the Jupyter extension: Search for the Jupyter extension in the VSCode Extensions view (Ctrl+Shift+X) and install it

Create a new notebook: Open the command palette (Ctrl+Shift+P), type and select "Jupyter: Create New Blank Notebook"

Enter and execute Plotly code: You can enter the code snippets provided above in different cells and run them to see the visualizations immediately
