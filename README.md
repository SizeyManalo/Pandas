# Pandas
Data Analysis with Pandas This code provides an example of data analysis using the Python libraries Pandas and NumPy. It begins by importing the necessary packages and loading data from a CSV file. The data is then manipulated and analyzed in various ways.

Data Analysis with Pandas
This code provides an example of data analysis using the Python libraries Pandas and NumPy. It begins by importing the necessary packages and loading data from a CSV file. The data is then manipulated and analyzed in various ways.

The code demonstrates key data analysis operations such as:

Loading and exploring a dataset from a URL.
Accessing specific rows and columns in the dataset.
Describing the statistical distribution of the data.
Creating Pandas Series from columns.
Finding minimum, maximum, mean, and median values.
Adding new columns to the DataFrame.
Sorting the data by specified columns.
Visualizing data using plots.
Exporting the data to a CSV file.
Overall, this code serves as a practical example of using Pandas and NumPy for data analysis and manipulation, making it a valuable reference for those working with data in Python.v

[ ]
# CSV files
# import the packages
import pandas as pd
import numpy as np
[ ]
url = "http://bit.ly/w-data"
data = pd.read_csv(url)
print("Data loaded successfully")
account_circle
Data loaded successfully
[ ]
data = pd.read_csv(url,index_col = "Hours")
row_val = data.loc[3.2]
print(row_val)
account_circle
Scores    27
Name: 3.2, dtype: int64
[ ]
# To load the top 5 records
data.head(3)
account_circle

[ ]
#Last rows of dataframe
data.tail()
account_circle

[ ]
# distribution of data
data.describe()
account_circle

[ ]
#series - one dimension array 
s = pd.Series(data['Hours'])
print(s)
account_circle
0     2.5
1     5.1
2     3.2
3     8.5
4     3.5
5     1.5
6     9.2
7     5.5
8     8.3
9     2.7
10    7.7
11    5.9
12    4.5
13    3.3
14    1.1
15    8.9
16    2.5
17    1.9
18    6.1
19    7.4
20    2.7
21    4.8
22    3.8
23    6.9
24    7.8
Name: Hours, dtype: float64
[ ]
s = pd.Series(data['Scores'])
print(s)
account_circle
0     21
1     47
2     27
3     75
4     30
5     20
6     88
7     60
8     81
9     25
10    85
11    62
12    41
13    42
14    17
15    95
16    30
17    24
18    67
19    69
20    30
21    54
22    35
23    76
24    86
Name: Scores, dtype: int64
[ ]
s.index
account_circle
RangeIndex(start=0, stop=25, step=1)
[ ]
s.values
account_circle
array([21, 47, 27, 75, 30, 20, 88, 60, 81, 25, 85, 62, 41, 42, 17, 95, 30,
       24, 67, 69, 30, 54, 35, 76, 86])
[ ]
s[2]
account_circle
27
[ ]
type(data['Hours'])
account_circle
pandas.core.series.Series
[ ]
print(data)
account_circle
       Scores
Hours        
2.5        21
5.1        47
3.2        27
8.5        75
3.5        30
1.5        20
9.2        88
5.5        60
8.3        81
2.7        25
7.7        85
5.9        62
4.5        41
3.3        42
1.1        17
8.9        95
2.5        30
1.9        24
6.1        67
7.4        69
2.7        30
4.8        54
3.8        35
6.9        76
7.8        86
[ ]
data.columns
account_circle
Index(['Hours', 'Scores'], dtype='object')
[ ]
type(data)
account_circle
pandas.core.frame.DataFrame
[ ]
# If you want to find datatypes for individual columns
data.dtypes
account_circle
Hours     float64
Scores      int64
dtype: object
[ ]
# To overview the information of our file
data.info()
account_circle
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 25 entries, 0 to 24
Data columns (total 2 columns):
 #   Column  Non-Null Count  Dtype  
---  ------  --------------  -----  
 0   Hours   25 non-null     float64
 1   Scores  25 non-null     int64  
dtypes: float64(1), int64(1)
memory usage: 528.0 bytes
[ ]
data.values
account_circle
array([[ 2.5, 21. ],
       [ 5.1, 47. ],
       [ 3.2, 27. ],
       [ 8.5, 75. ],
       [ 3.5, 30. ],
       [ 1.5, 20. ],
       [ 9.2, 88. ],
       [ 5.5, 60. ],
       [ 8.3, 81. ],
       [ 2.7, 25. ],
       [ 7.7, 85. ],
       [ 5.9, 62. ],
       [ 4.5, 41. ],
       [ 3.3, 42. ],
       [ 1.1, 17. ],
       [ 8.9, 95. ],
       [ 2.5, 30. ],
       [ 1.9, 24. ],
       [ 6.1, 67. ],
       [ 7.4, 69. ],
       [ 2.7, 30. ],
       [ 4.8, 54. ],
       [ 3.8, 35. ],
       [ 6.9, 76. ],
       [ 7.8, 86. ]])
[ ]
# If we don't want index, if we want to reset it to any column
data_index = data.set_index("Scores")
print(data_index)
account_circle
        Hours
Scores       
21        2.5
47        5.1
27        3.2
75        8.5
30        3.5
20        1.5
88        9.2
60        5.5
81        8.3
25        2.7
85        7.7
62        5.9
41        4.5
42        3.3
17        1.1
95        8.9
30        2.5
24        1.9
67        6.1
69        7.4
30        2.7
54        4.8
35        3.8
76        6.9
86        7.8
Basic Operations
[ ]
# bets calculate the hours studied in a week for weekdays
hours_studied = pd.Series(data['Hours'])
print(hours_studied*5)
account_circle
0     12.5
1     25.5
2     16.0
3     42.5
4     17.5
5      7.5
6     46.0
7     27.5
8     41.5
9     13.5
10    38.5
11    29.5
12    22.5
13    16.5
14     5.5
15    44.5
16    12.5
17     9.5
18    30.5
19    37.0
20    13.5
21    24.0
22    19.0
23    34.5
24    39.0
Name: Hours, dtype: float64
[ ]
# Mean Hours Studied
hours_studied.mean()
account_circle
5.012
[ ]
data['Scores'].min()
account_circle
17
[ ]
data['Scores'].max()
account_circle
95
[ ]
data['Scores'].median()
account_circle
47.0
[ ]
data.median()
account_circle
Hours      4.8
Scores    47.0
dtype: float64
[ ]
# If you want toi add new column. Let's add 'weekly_hours' to our data.
data['weekly_hours'] = hours_studied*5
print(data)
account_circle
    Hours  Scores  weekly_hours
0     2.5      21          12.5
1     5.1      47          25.5
2     3.2      27          16.0
3     8.5      75          42.5
4     3.5      30          17.5
5     1.5      20           7.5
6     9.2      88          46.0
7     5.5      60          27.5
8     8.3      81          41.5
9     2.7      25          13.5
10    7.7      85          38.5
11    5.9      62          29.5
12    4.5      41          22.5
13    3.3      42          16.5
14    1.1      17           5.5
15    8.9      95          44.5
16    2.5      30          12.5
17    1.9      24           9.5
18    6.1      67          30.5
19    7.4      69          37.0
20    2.7      30          13.5
21    4.8      54          24.0
22    3.8      35          19.0
23    6.9      76          34.5
24    7.8      86          39.0
[ ]
data.sort_values('Scores',ascending = True)
account_circle

[ ]
data.sort_values('Scores',ascending = False)
account_circle

[ ]
data.sort_values(by=['Scores','Hours'],ascending = False)
account_circle

[ ]
data.plot()
account_circle

[ ]
data['Scores'].plot(kind='bar')
account_circle

[ ]
# export the data to csv file.
data.to_csv('scores.csv')
[ ]

