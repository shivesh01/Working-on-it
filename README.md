---
name: 'Make a 3D Mountain'
description: 'Created San Bruno Mountain with the help of Python'
author: '@shivesh01'
image: 'https://cloud-a08hob7s0.vercel.app/0workshop1.gif'
---

# 3D Mountain


Hey, do you know where San Bruno Mountain is? Let's take a roller coaster ride and see where it is in Google Map.

![Mount san bruno](https://cloud-8at1ve02p.vercel.app/0ezgif.com-gif-maker.gif)    

The reason why I am showing you this, because You are going to make a Mountain with Python. You read it correctly will make a Mountain!!!

![amaze g.i.f](https://media.giphy.com/media/5p2wQFyu8GsFO/giphy.gif)


[Click here to see a working demo of today's project.](https://repl.it/@ShiveshSingh/Mtbrunoplot)

Now here is a step by step guide for how to prepare the setup for our project.


## Getting started

Today, you'll be using repl.it to write code. It is an online, instant development environment to learn, build, collaborate, and host your project. So you don’t have to waste time while setting up a development environment.

- [Sign up and then create a repl here.](https://repl.it/signup)

![repl website](https://cloud-73h0sldam.vercel.app/0screenshot_2020-12-25_at_23.03.53.png)

- To help get you started, you can fork our repl which contains a mountain.csv file. Click [here](https://repl.it/@ShiveshSingh/3DHeatmapWorkshop) to load up that repl for forking.

![](https://cloud-kben0mdmg.vercel.app/0screenshot_2021-01-08_at_09.43.56.png)

- The setup is complete.

---
Here are the libraries we'll be using today:

I hope you are excited! Let's start the coding part. First, we need to import libraries, and I know, you will think what those are, they are sweet and simple pieces of reusable codes containing modules, and modules containing functions, and we're able to easily import them using the `import` function with the library name into our project and use them.


```python
import pandas as pd
```

'pandas' is one of the popular libraries. It allows importing data from various file formats such as comma-separated-values(CSV), JSON, SQL, Microsoft Excel. It also allows various data manipulation operations such as merging, reshaping, selecting, as well as data cleaning, and much more with data-sets.


Wondering what are data-sets? examples of some kind the data-sets are:

**Image Dataset**

How cute is Pomeranian? 

![Dog Data-set](https://cloud-ht9owe43d.vercel.app/01_ccfehepblmqkqtb4erfesw.jpeg)


**CSV Dataset**
![Apple CSV](https://cloud-ht9owe43d.vercel.app/3screenshot-file.png)

```python
import numpy as np
```

The `numpy` is used to work with arrays. An array is a data-type consisting of a collection of elements, each identified by at least one array index or key.

![Arrays](https://cloud-okzc7z797.vercel.app/0array.png)

```python
import matplotlib.pyplot as plt
```

The `matplotlib` is used for data visualization like to make a histogram, scatter plot and bar-graph e.t.c. 

![Graphs](https://cloud-cb3n3b4td.vercel.app/0download.png)

```python
from mpl_toolkits.mplot3d import Axes3D
```

The `mpl_toolkits` are collections of functions that extend the `matplotlib` application. Which will enable us to work with 3D Plane.

```python
DataFrame = pd.read_csv('mountain.csv')
```
Created a variable `DataFrame` to read the `mountain.csv` with the help of the `pandas` library. Now we need to make rearrangements in `DataFrame` in order to make a plot.

```python
DataFrame = DataFrame.unstack()
```

The `unstack()` function in the data frame unstacks the row to columns. Hence it makes changes to your `Dataframe`. Let's see with an example.

![unstack img](https://cloud-5sfh036gn.vercel.app/0reshaping_unstack.png)

```python
DataFrame = DataFrame.reset_index()
```
When you concatenate, sort, join or do some rearrangements with your `DataFrame`, the index gets shuffled or out of order. To reset the index of a `DataFrame`, You can use `reset_index()` to sort indexes.

![reset index](https://cloud-8p15tas3t.vercel.app/0reshaping_unstack_.png)

```python
DataFrame.columns = ['X', 'Y', 'Z']
```
Our CSV contains three columns without names, so you need to assign names to columns, and using DataFrame.columns assign the first column to be X, the second column to be Y, and the third column to be Z I know you might be wondering what these are, these are coordinates of the point of the Mountain like longitude, latitude, and altitude. 

Fun Fact: We got exactly 552 coordinates

```python
DataFrame['X'] = pd.Categorical(DataFrame['X'])
```
`Categorical` is a `pandas` data type, using for the unique categorization of the categories. In short, you are changing the data. 

```python
DataFrame['X'] = DataFrame['X'].cat.codes
```
By using `cat.codes` we get unique values for each value of `X` in  an array even if the value is none then also returns a unique numeric value.

```python
fig = plt.figure(figsize=(6, 8))
```

To create a figure window You can use this function `plt.figure()`, even we can set the figure size by using the `figsize=(x,y)` where x(inches), y(inches) is the width and height of the figure window and stored in `fig`.

```python
ax = fig.gca(projection='3d')
```
`fig.gca()` with argument `projection=`3d`` returns the three-dimensional axes associated with the figure window and stored in the `ax` variable. 

```python
ax.plot_trisurf(DataFrame['X'], DataFrame['Y'], DataFrame['Z'], cmap=plt.cm.jet, linewidth=0.2)
```

You're almost there! creating a three-dimensional plot with plotting function `ax.plot_trisurf` takes in `x`, `y,` and `z` values, cmap, and linewidth. where `cmap` defines the colormap of the plot, and linewidth makes the curves smoother.
`cmap=plt.cm.jet` used jet colormap, even you can use another colormap from below list, you need to replace the `jet` with colormap you want to use.

```python
plt.show()
```
`plt.show` opens interactive windows that display your figure.

---
**Source Code**

```python
import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

from mpl_toolkits.mplot3d import Axes3D

DataFrame = pd.read_csv('mountain.csv')

DataFrame = DataFrame.unstack()

DataFrame = DataFrame.reset_index()

DataFrame.columns = ['X', 'Y', 'Z']

DataFrame['X'] = pd.Categorical(DataFrame['X'])

DataFrame['X'] = DataFrame['X'].cat.codes

fig = plt.figure()

ax = fig.gca(projection='3d')

ax.plot_trisurf(DataFrame['X'], DataFrame['Y'], DataFrame['Z'], cmap=plt.cm.jet, linewidth=0.2)

plt.show()
```

![Demo](https://cloud-a08hob7s0.vercel.app/0workshop1.gif)

You have completed the workshop, share with everyone, and Congratulations!!!


### Hacking!

![congratulations g.i.f](https://cloud-1th3ydnib.vercel.app/2workshop_happy.gif)


There are so many exciting things you can make now. For example, visualize datasets, and build things like 3D models. Now your turn to apply what you know to make more projects. Here's some inspiration on ways you can try new projects even cool!

- Example 1, using a CSV from Kaggle to make a 3D Volcano.    
[Demo img](https://cloud-94iqxy8lo.vercel.app/0volcano.gif),
[Code](https://repl.it/@ShiveshSingh/Volcano-3D-Heatmap)

- Example 2, using Array, and Cos function to make a Surface plot.  
[Demo img](https://cloud-iwpkargvc.vercel.app/0screenshot_2021-01-10_at_15.24.00.png),
[Code](https://repl.it/@ShiveshSingh/Surface-Plot-3D#main.py)


- Example 3, using Loops, List, and Sin function to make the contour plot.	
[Demo img](https://cloud-iwpkargvc.vercel.app/1screenshot_2021-01-10_at_15.25.30.png),
[Code](https://repl.it/@ShiveshSingh/3D-Contour-Plot#main.py)
