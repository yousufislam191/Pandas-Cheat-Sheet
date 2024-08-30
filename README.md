<h1 align="center">Pandas Cheat Sheet</h1>

## Table of Contents

- [Data Structures in Pandas](#data-structures-in-pandas)
- [Command Execution](#command-execution)
- [Pandas Read and Write to CSV](#pandas-read-and-write-to-csv)
- [Create Pandas Series and DataFrame](#create-pandas-series-and-dataframe)
- [Pandas Dataframe](#pandas-dataframe)
- [Pandas Sorting, Reindexing, Renaming, Reshaping, Dropping](#pandas-sorting-reindexing-renaming-reshaping-dropping)
- [DataFrame Retrieving Series/DataFrame Information and Slicing](#dataframe-retrieving-seriesdataframe-information-and-slicing)
- [Combine Two Data Sets](#combine-two-data-sets)
- [Data Analysis](#data-analysis)
- [Data Visualization](#data-visualization)
- [Additional Data Wrangling](#additional-data-wrangling)

## Data Structures in Pandas

| **Data Structure** | **Description**                                                                 |
| ------------------ | ------------------------------------------------------------------------------- |
| **Series**         | A one-dimensional labelled array capable of holding any data type.              |
| **DataFrame**      | A two-dimensional tabular data structure with labelled axes (rows and columns). |

## Command Execution

| **Command**           | **Description**                                        |
| --------------------- | ------------------------------------------------------ |
| `import pandas as pd` | Load the Pandas library as a custom defined name `pd`. |
| `pd.__version__`      | Check the Pandas version.                              |

## Pandas Read and Write to CSV

| **Command**                                    | **Description**                                               |
| ---------------------------------------------- | ------------------------------------------------------------- |
| `pd.read_csv('xyz.csv')`                       | Read the `.csv` file.                                         |
| `df.to_csv('xyz.csv')`                         | Save the Pandas DataFrame as "xyz.csv" in the current folder. |
| `pd.ExcelFile('xyz.xls')`                      | Read the Excel file 'xyz.xls'.                                |
| `pd.read_excel(file, 'Sheet1')`                | Read the 'Sheet1' of the Excel file 'xyz.xls'.                |
| `df.to_excel('xyz.xlsx', sheet_name='Sheet1')` | Save the dataset to 'xyz.xlsx' as Sheet1.                     |
| `pd.read_json('xyz.json')`                     | Read the 'xyz.json' file.                                     |
| `pd.read_sql('xyz.sql')`                       | Read the 'xyz.sql' file.                                      |
| `pd.read_html('xyz.html')`                     | Read the 'xyz.html' file.                                     |

## Create Pandas Series and DataFrame

| **Command**                                                        | **Description**                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `pd.Series(data=Data)`                                             | Create a Pandas Series with data like `{10: 'DSA', 20: 'ML', 30: 'DS'}`.                                                                                 |
| `pd.Series(data=['Geeks', 'for', 'geeks'], index=['A', 'B', 'C'])` | Create a Pandas Series and add custom defined index.                                                                                                     |
| `pd.DataFrame(data)`                                               | Create Pandas DataFrame with data like `{ 'Fruits': ['Mango', 'Apple', 'Banana', 'Orange'], 'Quantity': [40, 20, 25, 10], 'Price': [80, 100, 50, 70] }`. |
| `df.dtypes`                                                        | Give data types.                                                                                                                                         |
| `df.shape`                                                         | Give the shape of the data.                                                                                                                              |
| `df['Column_Name'].astype('int32')`                                | Change the data type to integer 32-bit.                                                                                                                  |
| `df['Column_Name'].astype('str')`                                  | Change the data type to string.                                                                                                                          |
| `df['Column_Name'].astype('float')`                                | Change the data type to float.                                                                                                                           |
| `df.info()`                                                        | Check the data information.                                                                                                                              |
| `df.values`                                                        | Give the data into the NumPy array.                                                                                                                      |

## Pandas Dataframe

|     | **Fruits** | **Quantity** | **Price** |
| --- | ---------- | ------------ | --------- |
| 1   | Mango      | 40           | 80        |
| 2   | Apple      | 20           | 100       |
| 3   | Banana     | 25           | 50        |
| 4   | Orange     | 10           | 70        |

## Pandas Sorting, Reindexing, Renaming, Reshaping, Dropping

| **Action**            | **Command**                                                                                       | **Description**                                  |
| --------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| **Sorting by Values** | `df.sort_values('Price', ascending=True)`                                                         | Sort the values of 'Price' in ascending order.   |
|                       | `df.sort_values('Price', ascending=False)`                                                        | Sort the values of 'Price' in descending order.  |
| **Sorting by Index**  | `df.sort_index(ascending=False)`                                                                  | Sort the index of DataFrame in descending order. |
| **Reindexing**        | `df.reset_index(drop=True, inplace=True)`                                                         | Reset the indexes to default.                    |
| **Renaming**          | `df.rename(columns={'Fruits': 'FRUITS', 'Quantity': 'QUANTITY', 'Price': 'PRICE'}, inplace=True)` | Rename the column names.                         |
| **Reshaping**         | `pd.melt(df)`                                                                                     | Gather columns into rows.                        |
|                       | `pivot = df.pivot(columns='FRUITS', values=['PRICE', 'QUANTITY'])`                                | Create a Pivot Table.                            |
| **Dropping**          | `df1 = df.drop(columns=['QUANTITY'], axis=1)`                                                     | Drop a column.                                   |
|                       | `df2 = df.drop([1, 3], axis=0)`                                                                   | Drop rows.                                       |

## DataFrame Retrieving Series/DataFrame Information and Slicing

| **Action**                             | **Command**                                     | **Description**                                                                                                                                                    |
| -------------------------------------- | ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Observation**                        | `df.head()`                                     | Print the first 5 rows.                                                                                                                                            |
|                                        | `df.tail()`                                     | Print the last 5 rows.                                                                                                                                             |
|                                        | `df.sample(n)`                                  | Select randomly `n` rows from the DataFrame.                                                                                                                       |
| **Selection Column Data**              | `df['FRUITS']`                                  | Select a single column value with the name of the column.                                                                                                          |
|                                        | `df[['FRUITS', 'PRICE']]`                       | Select more than one column with its name.                                                                                                                         |
|                                        | `df.filter(regex='F \| Q')`                     | Select the column whose names match the patterns of the respective regular expression i.e `‘FRUITS’ & ‘QUANTITY’`                                                  |
| **Getting Subsets of Rows or Columns** | `df.loc[:, 'FRUITS':'PRICE']`                   | Select all the columns between 'Fruits' and 'Price'.                                                                                                               |
|                                        | `df.loc[df['PRICE'] < 70, ['FRUITS', 'PRICE']]` | Select 'FRUITS' name having 'PRICE' < 70.                                                                                                                          |
|                                        | `df.iloc[2:5]`                                  | Select 2 to 5 rows.                                                                                                                                                |
|                                        | `df.iloc[:, [0, 2]]`                            | Select the columns having 0th & 2nd positions.                                                                                                                     |
|                                        | `df.at[1, 'PRICE']`                             | Select a single 'PRICE' value at the 2nd row of the 'PRICE' column.                                                                                                |
|                                        | `df.iat[1, 2]`                                  | Select the single values by their position.                                                                                                                        |
| **Filter**                             | `df.filter(items=['FRUITS', 'PRICE'])`          | Filter by column name. Select the ‘FRUITS’ and ‘PRICE’ column of the data frame                                                                                    |
|                                        | `df.filter(items=[3], axis=0)`                  | Filter by row index. Select the 3rd row of the data frame. Here axis = 0 is for row                                                                                |
|                                        | `df['PRICE'].where(df['PRICE'] > 50)`           | Returns a new Series object with the same length as the original 'PRICE' column. Replaces values where the condition is False with NaN or another specified value. |
|                                        | `df.query('PRICE > 70')`                        | Filter a DataFrame based on a specified condition. Return the rows having PRICE > 70.                                                                              |

## Combine Two Data Sets

| **Action**               | **Command**                                                   | **Description**            |
| ------------------------ | ------------------------------------------------------------- | -------------------------- |
| **Merge Two DataFrames** | `pd.merge(df1, df2, how='left', on='Fruits')`                 | Left Join.                 |
|                          | `pd.merge(df1, df2, how='right', on='Fruits')`                | Right Join.                |
|                          | `pd.merge(df1, df2, how='inner', on='Fruits')`                | Inner Join.                |
|                          | `pd.merge(df1, df2, how='outer', on='Fruits')`                | Outer Join.                |
| **Concatenation**        | `concat_df = pd.concat([df, df1], axis=0, ignore_index=True)` | Row-Wise Concatenation.    |
|                          | `concat_df = pd.concat([df, df2], axis=1)`                    | Column-Wise Concatenation. |

## Data Analysis

| **Action**           | **Command**                           | **Description**                                              |
| -------------------- | ------------------------------------- | ------------------------------------------------------------ |
| **Describe Dataset** | `df.describe()`                       | Descriptive statistics of a DataFrame.                       |
|                      | `df.describe(include=['O'])`          | Descriptive statistics of Object data types.                 |
|                      | `df.FRUITS.unique()`                  | Check the unique values of 'FRUITS' column.                  |
|                      | `df.FRUITS.value_counts()`            | Frequency of the unique values in 'FRUITS' column.           |
|                      | `df['PRICE'].sum()`                   | Return the sum of 'PRICE'.                                   |
|                      | `df['PRICE'].cumsum()`                | Return the cumulative sum of 'PRICE'.                        |
|                      | `df['PRICE'].min()`                   | Return the minimum value of 'PRICE' column.                  |
|                      | `df['PRICE'].max()`                   | Return the maximum value of 'PRICE' column.                  |
|                      | `df['PRICE'].mean()`                  | Return the mean value of 'PRICE' column.                     |
|                      | `df['PRICE'].median()`                | Return the median value of 'PRICE' column.                   |
|                      | `df['PRICE'].var()`                   | Return the variance of 'PRICE' column.                       |
|                      | `df['PRICE'].std()`                   | Return the standard deviation of 'PRICE' column.             |
|                      | `df['PRICE'].quantile([0.25, 0.75])`  | Return the 25th and 75th percentile value of 'PRICE' column. |
| **Groupby**          | `df.groupby('FRUITS')['PRICE'].sum()` | Group by 'FRUITS' and get the sum of 'PRICE' for each group. |
| **Correlation**      | `df.corr()`                           | Return the correlation matrix for the DataFrame.             |
| **Missing Values**   | `df.isnull().sum()`                   | Return the number of missing values for each column.         |
|                      | `df.dropna()`                         | Drop rows with missing values.                               |
|                      | `df.fillna(value=0)`                  | Fill missing values with a specified value.                  |

## Data Visualization

| **Action**    | **Command**                           | **Description**                          |
| ------------- | ------------------------------------- | ---------------------------------------- |
| **Bar Chart** | `df.plot.bar(x='FRUITS', y='PRICE')`  | Plot a bar chart of 'FRUITS' vs 'PRICE'. |
| **Line Plot** | `df.plot.line(x='FRUITS', y='PRICE')` | Plot a line plot of 'FRUITS' vs 'PRICE'. |
| **Histogram** | `df.plot.hist(y='PRICE', bins=20)`    | Plot a histogram of 'PRICE'.             |
| **Box Plot**  | `df.boxplot()`                        | Plot a box plot of the DataFrame.        |
| **Area Plot** | `df.plot.area()`                      | Plot an area chart of the DataFrame.     |

## Additional Data Wrangling

| **Action**             | **Command**                                                 | **Description**                                |
| ---------------------- | ----------------------------------------------------------- | ---------------------------------------------- |
| **Reshape DataFrames** | `df.pivot(index='ID', columns='DATE', values='VALUE')`      | Pivot a DataFrame.                             |
|                        | `df.melt(id_vars=['ID'], value_vars=['JAN', 'FEB', 'MAR'])` | Unpivot a DataFrame.                           |
| **Window Functions**   | `df.rolling(window=3).mean()`                               | Calculate the rolling mean with a window of 3. |
|                        | `df.expanding().mean()`                                     | Calculate the expanding mean.                  |
|                        | `df.ewm(span=3).mean()`                                     | Calculate the exponentially weighted mean.     |
| **Apply and Map**      | `df['COL_NAME'].apply(summation)`                           | Apply a function to a DataFrame column.        |
|                        | `df['COL_NAME'].map(lambda x: x * 2)`                       | Apply a lambda function to a DataFrame column. |

---

**Note:** This cheat sheet covers common commands and techniques in Pandas, a powerful library for data analysis and manipulation in Python. For detailed explanations and examples, please refer to the official [Pandas documentation](https://pandas.pydata.org/pandas-docs/stable/).
