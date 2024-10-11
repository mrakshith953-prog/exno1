# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
            from google.colab import drive
drive.mount('/content/drive')

ls drive/MyDrive/'Colab Notebooks'/DATA/

# **DATA CLEANING**




import pandas as pd
import numpy as np

df=pd.read_csv('drive/MyDrive/Data Science/Data_set.csv')

# CHECK OUT NULL VALUES IN DATA SET USING FUNCTION
df_null=df.isnull()
print(df_null)

# DISPLAY THE SUM ON NULL VALUES IN EACH ROWS
df_sum=df.isnull().sum()
print(df_sum)

# DROP NULL VALUES
df_drop=df.isnull().dropna()
print(df_drop)

# FILL NULL VALUES WITH CONSTANT VALUE "O"
df_null_0=df.fillna(0)
print(df_null_0)

# FILL NULL VALUES WITH ffill METHOD
df_null_ffill=df.ffill()
print(df_null_ffill)

# FILL NULL VALUES WITH bfill METHOD
df_bfill=df.bfill()
print(df_bfill)

 #CALCULATE MEAN VALUE OF A COLUMN AND FILL IT WITH NULL VALUES
 df_mean1=df['num_episodes'].fillna(df['num_episodes'].mean())
print(df_mean1)

df_mean2=df['rating'].fillna(df['rating'].mean())
print(df_mean2)

df_mean3=df['current_overall_rank'].fillna(df['current_overall_rank'].mean())
print(df_mean3)

df_mean4=df['lifetime_popularity_rank'].fillna(df['lifetime_popularity_rank'].mean())
print(df_mean4)

df_mean5=df['watchers'].fillna(df['watchers'].mean())
print(df_mean5)

# DROP NULL VALUES
df_dropna=df.dropna()
print(df_dropna)

# **Outlier Detection and Removal - IQR**


import seaborn as sns

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
print(af)

# USE BOXPLOT FUNCTION HERE TO DETECT OUTLIER
sns.boxplot(af)

sns.scatterplot(af)

q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)

iqr=q3-q1
print(iqr)

Q1=np.percentile(af,25)
Q2=np.percentile(af,50)
Q3=np.percentile(af,75)

IQR=Q3-Q1

lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR

outliers = [x for x in age if x < lower_bound or x > upper_bound]

print('Q1:',Q1)
print('Q3:',Q3)
print('IQR:',IQR)
print('Lower bound:',lower_bound)
print('Upper bound:',upper_bound)
print('Outliers:',outliers)

af=af[((af>=lower_bound)&(af<=upper_bound))]
print(af)

af.dropna()

sns.boxplot(af)

sns.scatterplot(af)

# **Z Score**

from scipy import stats

data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93]
df=pd.DataFrame(data)

sns.boxplot(df)

mean=np.mean(data)
print(mean)

std=np.std(data)
print(std)

z=np.abs(stats.zscore(df))
print(z)

threshold=3
outliers = df[abs(df) > 3]
print("Outliers:")
print(outliers)

df_cleaned = df[(z <= threshold)]
print(df_cleaned)

sns.boxplot(df_cleaned)

sns.scatterplot(df_cleaned)
# Result
          <<include your Result here>>
