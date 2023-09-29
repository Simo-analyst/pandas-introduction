# importing the necesary modules

import pandas as pd
import seaborn as sns
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
import warnings
warnings.filterwarnings('ignore')

# reading our file using pandas module and asigning it to a variable
df=pd.read_excel(r"C:\Users\User\Downloads\sample_-_superstore.xls")
df

# having a look at the shape of our data
# our data has 9994 rows and 21 columns
print(df.shape)

# having a look at the columns
df.columns

# selecting data based whether it is numerical or categorical
cat_data=df.select_dtypes(include='object').columns
num_data=df.select_dtypes(include=np.number).columns.tolist()
print('categorical:')
print(cat_data)
print('numerical:')
print(num_data)

# checking data types of our data frame
df.dtypes

# having a look at descriptive statistics
df.describe()

# Brief description of the statistics above

1.maximum profit is 8399 while minimum profit is a negative 6599 indicating there were some loss
2.interquatile range of profit is (29.4-1.7)=27.7
3.profit is positively skewed since the median is cross to lower quatile and mean > median

# in support of point 3
df['Profit'].skew()

# cumulative sum of Sales
df['Sales'].cumsum()

# having a look at top five records of our dataframe
df.head()

# looking at the last five records
df.tail()

# setting index as Row ID
df.set_index('Row ID',inplace=True)
df.head()

# resetting the index
df.reset_index(inplace=True)
df.head()

# checking for null values in our dataset
df.isnull().sum()

# brief info about our data
df.info()

df.head()

# renaming columns
df=df.rename(columns={'Country':'Homeland'}).copy()

df.head(1)

df.head(1)

# having a look at numerical data
df1=df[[ 'Sales', 'Quantity', 'Discount', 'Profit']]
df1.head()

# checking for correlation
df1.corr()

# plotting a heatmap
sns.heatmap(df1.corr(),annot=True)
plt.show()

sns.set_style('darkgrid')
sns.scatterplot(x='Discount',y='Sales',data=df,hue='Ship Mode')
plt.show()


