# Getting started
## Import
```python
import pandas as pd
```
## Create DataFrame
Ways to create DataFrame
1) Pass in dictionary and pass in list of index name to `index`
```python
sales_df = pd.DataFrame({'Column A': [1,2,3,4], 'Column B':[5,6,7,8]}, index= ['2019 sales', '2020 sales', '2021 sales'])
```
2) Pass in list and `columns`
```python
fruits_df = pd.DataFrame([[30, 21]], columns=['Apples', 'Bananas'])
```
## Create Series
Series will have no column name, you can use `name` to name your series.
```python
ingredients_df = pd.Series(['4 cups', '1 cup', '2 large', '1 can'], index = ['Flour', 'Milk', 'Eggs', 'Spam'], name = 'Dinner')
```
## Read CSV file
use `index_col` if there is predefined index in CSV file. 
```python
reviews_df = pd.read_csv(<path_to_csv_file>, index_col=0)
```
check DataFrame shape using `.shape`
```python
reviews_df.shape
```
look at some of the data using `.head()`
```python
reviews_df.head()
```
## Save to CSV
use `to_csv()` to save to .csv file.
```python
reviews_df.to_csv('reviews.csv')
```

# Indexing, Selecting & Assigning
## Accessing Series
```python
reviews_df['column_name'] 
```
Access to elements using index
```python
reviews_df['column_name'][0]
```
## Indexing in Pandas
row-first, column-second (contrast to native python)
### Index-based selection `.iloc`
select first row of the df
```python
reviews_df.iloc[0]
```
select all rows in the first column
```python
reviews_df.iloc[:,0]
```
select first 3 rows in the first column
```python
reviews_df.iloc[:3,0]
```
pass a list to select 
```python
reviews_df.iloc[[0, 1, 2], 0]
```
select the last 5 rows
```python
reviews_df.iloc[-5:]
```
### Label-based selection  `.loc`
select the first row in 'country' column.

This case the first row has indax value = 0, so passing 0 will return the first row. 0 here is not index itself but it is the index's value
```python
reviews_df.loc[0]['country']
```
In some case, using `.loc` will be a lot easier coz no need to look at index
- select all rows from list of column names using `.loc`
```python
reviews_df.loc[:, ['taster_name', 'taster_twitter_handle', 'points']]
```
`.iloc` and `.loc` deals with index a bit differently. `.iloc` use standard python indexing while `.loc` deals with index inclusively.

This is particularly confusing when the DataFrame index is a simple numerical list, e.g. 0,...,1000. 

In this case df.iloc[0:1000] will return 1000 entries, while df.loc[0:1000] return 1001 of them! 

To get 1000 elements using loc, you will need to go one lower and ask for df.loc[0:999].

### Manipulating the index
The `set_index()` method can be used to do the job. Here is what happens when we set_index to the title field:
```python
reviews_df.set_index("title")
```
### Conditional selection
To do interesting things with the data, however, we often need to ask questions based on conditions.

To select rows only where country are Italy, Use this condition as a mask.
```python
reviews_df.country == 'Italy'
```
We can pass the mask to `.loc` to select rows with the condition.
```python
reviews_df.loc[reviews_df.country == 'Italy']
```

