# Pandas
## Getting started
### Import
```python
import pandas as pd
```
### Create DataFrame
1) Pass in dictionary and pass in list of index to index
```python
df = pd.DataFrame({'Column A': [1,2,3,4], 'Column B':[5,6,7,8]}, index= ['2019 sales', '2020 sales', '2021 sales'])
```
### Create Series
Series will have no column, you can use name to name your series.
```python
ingredients_df = pd.Series(['4 cups', '1 cup', '2 large', '1 can'], index = ['Flour', 'Milk', 'Eggs', 'Spam'], name = 'Dinner')
```
### Read CSV file
use index_col if there is predefined index in CSV file. 
```python
reviews_df = pd.read_csv(<path_to_csv_file>, index_col=0)
```
### Save to CSV
use to_csv with your df.
```python
reviews_df.to_csv('reviews.csv')
```
