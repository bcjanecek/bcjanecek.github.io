---
layout: post
title:      "Four Cool Pandas Tricks"
date:       2020-01-27 17:08:32 +0000
permalink:  four_cool_pandas_tricks
---


A common saying goes that data scientists typically spend 60-80% of their time gathering, cleaning, and exploring data. For these tasks, the Pandas library has proven to be a very useful and robust library being built on top of Matplotlib and Numpy. I hope you find these neat tricks to be as useful in cleaning and exploring data in Pandas as they have been for me. 

1. Often in machine learning, seemingly strong features are in a categorical data format. This can be an issue for many machine learning algorithms which require numerical input. A useful technique for handling this is to create a new column which assigns a numerical code to each category as shown below using the famous Iris flower database.

```
iris['species'] = iris['species'].astype('category')
iris['species_code'] = iris['species'].cat.codes
```

This code requires two parts. In the first line it is necessary to change the column you wish to decode into a Python 'category' datatype. Second, you create a new column for the decoded category and call the cat.codes method on the column you wish to decode. This column (with coded values 0, 1, 2, etc.) is numerical and may be used as a feature in your machine learning algorithms. 

2. When first getting to know a dataset it can be helpful to have a quick, "shotgun" style visual peak at your data to get a feel for the distribution of variables and to see if you can spot any potential correlations. You can do this quickly using Seaborn's pairplot method. Matplotlib has a similar scatter_matrix method, however, I prefer Seaborn's method for it's ability to color code plots, the beatiful color schemes, and the use of kernel density plots rather than histograms. The following code allows you to accomplish this with the Iris database. 

```
import seaborn as sns
sns.set(style="ticks")
sns.pairplot(iris, hue="species")

```

3. Using tabula-py (https://tabula-py.readthedocs.io/en/latest/) it is possible to convert any PDF table into a Pandas dataframe. Note that Java 8+ must be installed in your environment in order to use this method. 

```
pip install tabula-py
import tabula
df = tabula.read_pdf("example.pdf")
```

4. When cleaning data it is easy enough to find and deal with Pandas designated Nan null values. However, depending on the data, Pandas isna() method may not pick up on all datapoints (e.g. 0, -999) which were intended to be represented as null values. A quick few lines of code to check for repeat values accross all columns in your dataframe is as follows.

```
for col in df.columns:
		  print(col, '\n', df[col].value_counts(normalize=True).head())

```

These lines of code will return the name of each column followed by the value counts of each variable in the series in a normalized (0-1) fashion. This will make it easy to see if a common, erroneous value was often used to designate null values so that these rows / columns may be dealt with accordingly. 

Pandas is a very powerful tool for cleaning, visualizing, and exploring data and there are many quick tricks which can make these jobs easier. The wealth of knowledge available online is worth exploring often. 
