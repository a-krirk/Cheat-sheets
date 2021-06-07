# Pandas
## Getting started
### Import
```python
import pandas as pd
```
### Create DataFrame
```python
df = pd.DataFrame({'Column A': [1,2,3,4], 'Column B':[5,6,7,8]}, index= ['2019 sales', '2020 sales', '2021 sales'])
```
### Create Series
```python
ingredients = pd.Series(['4 cups', '1 cup', '2 large', '1 can'], index = ['Flour', 'Milk', 'Eggs', 'Spam'], name = 'Dinner')
```
### Read & Save CSV
