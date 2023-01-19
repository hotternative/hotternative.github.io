---
title: "Sum Columns Based on Conditions in Pandas"
date: 2022-12-08
---
Use the following syntax to sum the values of a column in a pandas DataFrame based on a condition:
```python
df.loc[df['column_to_filter'] == some_value, 'column_to_sum'].sum()
```

`df['column_to_filter'] == some_value` will generate a boolean array. In 
[pandas doc](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html
), this is known as an "align-able boolean Series".

`df.loc[df['column_to_filter'] == some_value]` will filter for the values where the boolean value is `True`, 
and `column_to_sum` will then select the specific column to sum on.

`df.loc` is a powerful tool. It also works on row label. 
See [pandas doc](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html
) for more examples.

