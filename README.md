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
![Screenshot 2024-11-21 141602](https://github.com/user-attachments/assets/4a9dc9b8-c692-4f4c-b427-d9bb10ff1889)
![Screenshot 2024-11-21 141550](https://github.com/user-attachments/assets/9d625d5f-31ec-47db-83ea-d7eb70ee3664)
![Screenshot 2024-11-21 141526](https://github.com/user-attachments/assets/73582728-a738-4a33-9124-3dad9c27269e)
![Screenshot 2024-11-21 141517](https://github.com/user-attachments/assets/681dafbb-f6f3-4c9e-b513-7bb30a88213f)
![Screenshot 2024-11-21 141456](https://github.com/user-attachments/assets/2a848bb7-ee7c-4541-959a-cc5bc3fbcb23)
![Screenshot 2024-11-21 142230](https://github.com/user-attachments/assets/1f8dca54-c4ce-4733-ae8c-0a974f879eb4)
![Screenshot 2024-11-21 142225](https://github.com/user-attachments/assets/d3fff1b8-2f13-48f6-9faa-c88e8dc5a497)
![Screenshot 2024-11-21 142219](https://github.com/user-attachments/assets/e45fb6c2-e07b-4123-9a99-bd69802710fc)
![Screenshot 2024-11-21 142213](https://github.com/user-attachments/assets/5892cdeb-d84f-4984-8a39-d7eb7464638f)
![Screenshot 2024-11-21 142206](https://github.com/user-attachments/assets/2dd89869-a840-4905-9cbf-8e765a703560)
![Screenshot 2024-11-21 142159](https://github.com/user-attachments/assets/8330102d-4b83-4aa3-b057-f58f4f8f182c)
![Screenshot 2024-11-21 142148](https://github.com/user-attachments/assets/c9d66d25-1b33-4747-a6ba-83271e80c816)
![Screenshot 2024-11-21 142020](https://github.com/user-attachments/assets/7d1db144-dfb3-4e5c-ab66-5d7c2e5f80ff)
![Screenshot 2024-11-21 142014](https://github.com/user-attachments/assets/fb1455f6-15e1-44da-a0c4-ba24d97654b9)
![Screenshot 2024-11-21 142008](https://github.com/user-attachments/assets/5fdd6409-1a9c-4f69-a2ab-6185e023a26b)
![Screenshot 2024-11-21 142001](https://github.com/user-attachments/assets/acdb5786-73ab-4f8d-90ee-2b3757029519)
![Screenshot 2024-11-21 141754](https://github.com/user-attachments/assets/5f044440-41bf-4927-8eac-f6f1c2948849)
![Screenshot 2024-11-21 141748](https://github.com/user-attachments/assets/1576e42d-f69e-4442-88b8-779440d8ec9c)
![Screenshot 2024-11-21 141743](https://github.com/user-attachments/assets/7dbd5e69-dc47-4be0-b48e-29cb6f0a8551)
![Screenshot 2024-11-21 141734](https://github.com/user-attachments/assets/70ddfc58-a3b7-4be6-9e22-413c2b60e8d0)
![Screenshot 2024-11-21 141724](https://github.com/user-attachments/assets/e24ee21a-5b39-40d4-af03-ed4ef6533c11)
![Screenshot 2024-11-21 141640](https://github.com/user-attachments/assets/9e7eb354-77a4-424b-bbd3-819ad538a57f)
![Screenshot 2024-11-21 141626](https://github.com/user-attachments/assets/bd4efccd-a3e2-41e0-bf8c-e71c24ed7a51)
![Screenshot 2024-11-21 141614](https://github.com/user-attachments/assets/360dbcbb-f64c-48f2-9a15-d44af46dd6bc)

# Result
          The Data cleaning process is completed successfuly
