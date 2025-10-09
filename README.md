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
df=pd.read_csv("data_set.csv")
df

<img width="1389" height="627" alt="image" src="https://github.com/user-attachments/assets/742332ec-7f26-4b1d-99d0-1e995eca4950" />

<img width="865" height="603" alt="image" src="https://github.com/user-attachments/assets/1b4c6cba-0655-4a36-b9f5-5a7b22a9137e" />


df.isnull()

<img width="1389" height="520" alt="image" src="https://github.com/user-attachments/assets/56e21034-f6fa-4b2c-ba52-f41e341b186e" />

<img width="861" height="514" alt="image" src="https://github.com/user-attachments/assets/3cbc5045-299e-4089-a998-9ee8c199759c" />


df.isnull().sum()

<img width="253" height="267" alt="image" src="https://github.com/user-attachments/assets/269f6dba-479e-4f1e-a636-c949505bb672" />

df.notnull()

<img width="1331" height="512" alt="image" src="https://github.com/user-attachments/assets/4df3ce44-4028-4888-ae1b-ac2c36b2f897" />

<img width="863" height="531" alt="image" src="https://github.com/user-attachments/assets/206245a9-8015-4304-94c2-2b56a7f3fe75" />

df.dropna(axis=0)
df

<img width="1335" height="633" alt="image" src="https://github.com/user-attachments/assets/dd32beb9-4a9d-48a4-94b2-8b899106aa0a" />

<img width="855" height="616" alt="image" src="https://github.com/user-attachments/assets/5962f2c6-d6ca-4e9a-80a1-bf1a948682c9" />

df.dropna(axis=1)
df

<img width="1338" height="636" alt="image" src="https://github.com/user-attachments/assets/e1426450-e84c-4412-b67d-3ba9a93d23c5" />

<img width="845" height="626" alt="image" src="https://github.com/user-attachments/assets/ca2c2c2a-639f-4fa9-acd0-1debccfe38f4" />

dfs=df[df['num_episodes']>20]
dfs


<img width="1363" height="780" alt="image" src="https://github.com/user-attachments/assets/8d4709f8-7ca3-4171-bd81-82a1fa82d77b" />


<img width="864" height="781" alt="image" src="https://github.com/user-attachments/assets/5b1a3f13-db94-4339-a8fe-77b1ceebe0e1" />


<img width="1376" height="389" alt="image" src="https://github.com/user-attachments/assets/49ede154-71d0-4a6d-a63c-ea96baeec523" />


<img width="829" height="534" alt="image" src="https://github.com/user-attachments/assets/2921d263-6533-47d5-853a-e95f2fa70ef5" />

df.iloc[:4]


<img width="1331" height="329" alt="image" src="https://github.com/user-attachments/assets/3cb5706d-1d60-4242-a512-544d01e4b514" />


<img width="849" height="330" alt="image" src="https://github.com/user-attachments/assets/1defa794-2820-497e-8e0a-4b66ebb8cb86" />

df.iloc[[1,3,5],[1,3]]


<img width="318" height="162" alt="image" src="https://github.com/user-attachments/assets/e9e64771-7c80-4fc9-a405-1eee0fba5ef1" />

df.iloc[0:4,1:4]


<img width="473" height="201" alt="image" src="https://github.com/user-attachments/assets/8c30c8a6-7717-4669-b7f9-e14fd318ba3c" />

dff=df.fillna(0)
dff


<img width="1350" height="631" alt="image" src="https://github.com/user-attachments/assets/7c650b0e-24e8-4e3d-9d12-14a7301401c8" />


<img width="855" height="624" alt="image" src="https://github.com/user-attachments/assets/57a11a9c-3343-43d3-be0f-e0361d1de72a" />

df.fillna(method='ffill')


<img width="1340" height="751" alt="image" src="https://github.com/user-attachments/assets/c4c01fb2-03ce-4ba2-9f52-1bdafef236a1" />


<img width="862" height="715" alt="image" src="https://github.com/user-attachments/assets/45f8a4e0-41db-41b5-84d1-55f1c1592548" />

df.fillna(method='bfill')


<img width="1345" height="653" alt="image" src="https://github.com/user-attachments/assets/c3aef5af-ed65-425f-be90-d7788437f329" />


<img width="857" height="601" alt="image" src="https://github.com/user-attachments/assets/c879ee8f-e086-4383-b902-16041026fddd" />

df['num_episodes'].fillna(value=df['num_episodes'].mean())


<img width="444" height="263" alt="image" src="https://github.com/user-attachments/assets/28fc2397-fdd8-4e0b-8ed0-3da3ad081625" />

df['num_episodes'].fillna(value=df['num_episodes'].mean(),inplace=False)


<img width="458" height="262" alt="image" src="https://github.com/user-attachments/assets/ea033c2b-187b-4148-8a57-32bba70cde28" />

df["num_episodes"]=df["num_episodes"].astype('Int64')
df["num_episodes"]

<img width="531" height="268" alt="image" src="https://github.com/user-attachments/assets/d35b34cc-3bc9-490e-aeed-5038c2109e4f" />

df['country']=df['country'].astype(object)
df['country']


<img width="414" height="269" alt="image" src="https://github.com/user-attachments/assets/c0200328-a718-4e74-a15d-53a80164780d" />

import matplotlib.pyplot as plt
df_cleaned=df.dropna(subset=['country'])
df_cleaned=df.dropna(subset=["num_episodes"])
plt.bar(df_cleaned['country'],df_cleaned["num_episodes"])
plt.show()


<img width="713" height="517" alt="image" src="https://github.com/user-attachments/assets/2cfa6e29-8e63-4177-9a73-7eea89864bd8" />

plt.barh(df["num_episodes"],df['country'])
plt.show()


<img width="691" height="517" alt="image" src="https://github.com/user-attachments/assets/503a1b35-031c-4a34-8f19-522c7647003b" />

plt.plot(df["num_episodes"],df['country'])
plt.show()


<img width="797" height="509" alt="image" src="https://github.com/user-attachments/assets/84564a9b-97ad-4b57-a6d3-23d65be4b4dd" />

plt.scatter(df["num_episodes"],df['country'])
plt.show()


<img width="791" height="529" alt="image" src="https://github.com/user-attachments/assets/3a42fa42-a629-410c-8dfe-bc0987c9a67f" />


# Result
          The Data cleaning process is completed successfuly
