#### Pandas is built on NumPy and Matplotlib 
where Numpy provides multi dimensional array objects = easy data manipulation
and matplotlib = for data visualization

```
df.head() - to quickly explore contents
df.info() - names, data types, missing vals or not of columns
df.describe() - summary statistics - where count is number of non missing values
df.values - gives all values in a 2d numpy array
df.columns - gives column names
df.index - row numbers, row names
df.shape - returns number of rows and columns of the dataframe
```

Zen of Python:
there should only be one obvious solution.

Sorting and subsetting:

sort by one col:
```df.sort_values("col_name", ascending=False); - default - ascending```

sort by multiple vars: by passing list of vars
```df.sort_values(["col1","col2"], ascending = [True, False]);```

subset to see just one col: 
```df["col_name"]```

to subset multiple cols, pass a list of vars:
//outer [] to subset the dataframe
//inner [] to send a list of vars

```df[['breed','height']]```

(or)

```
list_to_subset=['col1','col2']
df[list_to_subset]
```

conditional subsetting:
```df[df['height']>50]```

text based subsetting:
```df[df['breed']=='Labrador']```

date based subsetting: yyyy/mm/dd
```df[df['dob'] > "2015-10-10"]```

based on multiple conditions

```is_lab = df['breed'] == 'lab'
is_brown= df['color'] == 'brown'

df[is_lab && is_brown]
```

subsetting using .isin():
```
is_black_or_brown = df['color'].isin(['Black','Brown'])
df[is_black_or_brown]
```
New columns from existing columns:
```
df['new_col'] = df['old_col']/100

df['bmi'] = df['weight']/df['height'] ** 2
```

Summary Statistics:
```
df['col'].mean()
df['col'].min()
df['col'].max()
```
.agg() method:
```
def pct30(col):
  return col.quantile(0.3)

df['weight_kg'].agg(pct30)

```

agg for multiple summaries:
```
def pct40(col):
  return col.quantile(0.4)
  
df['weight_kg'].agg([pct30,pct40])
```

cumulative sum:
```
df['col'].cumsum()
.cummin()
.cumprod()
```
