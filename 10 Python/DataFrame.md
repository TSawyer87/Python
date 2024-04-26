#Pandas 
# Getting started[](https://www.kaggle.com/code/residentmario/creating-reading-and-writing#Getting-started)

To use pandas, you'll typically start with the following line of code.

import pandas as pd

# Creating data[](https://www.kaggle.com/code/residentmario/creating-reading-and-writing#Creating-data)

There are two core objects in pandas: the **DataFrame** and the **Series**.

### DataFrame[](https://www.kaggle.com/code/residentmario/creating-reading-and-writing#DataFrame)

A DataFrame is a table. It contains an array of individual _entries_, each of which has a certain _value_. Each entry corresponds to a row (or _record_) and a _column_.

For example, consider the following simple DataFrame:

pd.DataFrame({'Yes': [50, 21], 'No': [131, 2]})

||Yes|No|
|---|---|---|
|0|50|131|
|1|21|2|

In this example, the "0, No" entry has the value of 131. The "0, Yes" entry has a value of 50, and so on.

DataFrame entries are not limited to integers. For instance, here's a DataFrame whose values are strings:

pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'], 'Sue': ['Pretty good.', 'Bland.']})

||Bob|Sue|
|---|---|---|
|0|I liked it.|Pretty good.|
|1|It was awful.|Bland.|

We are using the `pd.DataFrame()` constructor to generate these DataFrame objects. The syntax for declaring a new one is a dictionary whose keys are the column names (`Bob` and `Sue` in this example), and whose values are a list of entries. This is the standard way of constructing a new DataFrame, and the one you are most likely to encounter.

The dictionary-list constructor assigns values to the _column labels_, but just uses an ascending count from 0 (0, 1, 2, 3, ...) for the _row labels_. Sometimes this is OK, but oftentimes we will want to assign these labels ourselves.

The list of row labels used in a DataFrame is known as an **Index**. We can assign values to it by using an `index` parameter in our constructor:

pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'], 
              'Sue': ['Pretty good.', 'Bland.']},
             index=['Product A', 'Product B'])

||Bob|Sue|
|---|---|---|
|Product A|I liked it.|Pretty good.|
|Product B|It was awful.|Bland.|