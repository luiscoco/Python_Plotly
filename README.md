# Python a brief introduction to Plotly

https://plotly.com/

https://www.youtube.com/watch?v=j0wvKWb337A&list=PLE50-dh6JzC4onX-qkv9H3HtPbBVA8M94

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

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/a675076e-f778-4f04-a7c3-de3b9a1e620f)

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/b3fe6e7e-eb3c-4da8-ba3a-f1cbec4c13cf)

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

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/edb79fac-d15c-4b81-8b37-092e28dda00d)

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/2a1abfd6-2889-4e6e-a775-05b4a267d10e)

Let's delve into some **more advanced and complex Plotly examples** that showcase its capabilities for creating interactive and sophisticated visualizations

These examples will demonstrate a 3D surface plot, a contour plot, and an animated scatter plot

## 4. 3D Surface Plot

This example will create a 3D surface plot, which can be useful for visualizing complex mathematical functions or geographic data

```python
import plotly.graph_objects as go
import numpy as np

# Generate data
x = np.linspace(-5, 5, 50)
y = np.linspace(-5, 5, 50)
x, y = np.meshgrid(x, y)
z = np.sin(np.sqrt(x**2 + y**2))

# Create a figure
fig = go.Figure(data=[go.Surface(z=z, x=x, y=y)])

# Update the layout
fig.update_layout(title='3D Surface Plot', autosize=False,
                  width=800, height=800,
                  margin=dict(l=65, r=50, b=65, t=90))

# Show plot
fig.show()
```

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/2046f932-5ba5-4723-893d-3b34d4ffabb9)

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/51cf5315-68db-4bff-8d7e-a14f6f455d2e)

## 5. Contour Plot

Contour plots are great for displaying the potential distribution or level curves of a function

Here's how to create a contour plot:

```python
import plotly.graph_objects as go
import numpy as np

# Generate data
x = np.linspace(-2, 2, 200)
y = np.linspace(-2, 2, 200)
x, y = np.meshgrid(x, y)
z = x * np.exp(-x**2 - y**2)

# Create a figure
fig = go.Figure(data=[go.Contour(z=z, x=x[0], y=y[:, 0])])

# Update the layout
fig.update_layout(title='Contour Plot', width=800, height=800)

# Show plot
fig.show()
```

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/d088b531-9319-4a46-8265-3b9adde6f4a3)

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/9538cbf9-8bc9-413f-bbb3-2b95379dde86)

## 6. Animated Scatter Plot

This example showcases how to create an animated scatter plot, which can be particularly useful for visualizing data changes over time

```python
import plotly.graph_objects as go
import numpy as np

# Time steps
t = np.linspace(0, 2 * np.pi, 100)

# Coordinates based on time
x = np.sin(t)
y = np.cos(t)

# Creating the initial scatter plot
fig = go.Figure(
    data=[go.Scatter(x=[x[0]], y=[y[0]], mode='markers')],
    layout=go.Layout(
        xaxis=dict(range=[-1.5, 1.5], autorange=False),
        yaxis=dict(range=[-1.5, 1.5], autorange=False),
        title="Animated Scatter Plot"
    )
)

# Adding frames to the animation
frames = [go.Frame(data=[go.Scatter(x=[x[k]], y=[y[k]])])
          for k in range(len(t))]

fig.frames = frames

# Add a slider and play/pause button to control the animation
fig.update_layout(
    updatemenus=[
        {
            "buttons": [
                {
                    "args": [None, {"frame": {"duration": 50, "redraw": True}, "fromcurrent": True}],
                    "label": "Play",
                    "method": "animate"
                },
                {
                    "args": [[None], {"frame": {"duration": 0, "redraw": True}, "mode": "immediate", "transition": {"duration": 0}}],
                    "label": "Pause",
                    "method": "animate"
                }
            ],
            "direction": "left",
            "pad": {"r": 10, "t": 87},
            "showactive": False,
            "type": "buttons",
            "x": 0.1,
            "xanchor": "right",
            "y": 0,
            "yanchor": "top"
        }
    ],
    sliders=[{
        "currentvalue": {
            "prefix": "Time: ",
            "visible": True,
            "xanchor": "right"
        },
        "transition": {"duration": 300, "easing": "cubic-in-out"},
        "pad": {"b": 10, "t": 50},
        "len": 0.9,
        "x": 0.1,
        "y": 0,
        "steps": [{"args": [[f.name], {"frame": {"duration": 300, "redraw": True}, "mode": "immediate", "transition": {"duration": 300}}],
                  "label": str(k), "method": "animate"} for k, f in enumerate(fig.frames)]
    }]
)

# Show the plot
fig.show()
```

![image](https://github.com/luiscoco/Python_Plotly/assets/32194879/7585b8dd-774b-413e-98b2-c9f662d5ffa3)

## 7. Setting Up VSCode for Plotly

To make the most out of using Plotly in VSCode, you might want to use the Jupyter Notebook support within VSCode

This allows you to write and execute code in cells, view plots inline, and more interactively develop your visualizations

Install the Jupyter extension: Search for the Jupyter extension in the VSCode Extensions view (Ctrl+Shift+X) and install it

Create a new notebook: Open the command palette (Ctrl+Shift+P), type and select "Jupyter: Create New Blank Notebook"

Enter and execute Plotly code: You can enter the code snippets provided above in different cells and run them to see the visualizations immediately
