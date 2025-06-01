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
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/b24784c7-92aa-4d14-a545-dfeea8eac50e)

```
print(df.head(7))
```
![image](https://github.com/user-attachments/assets/9ca17a11-6725-4b43-ac4d-85f0deda33c8)

```
print(df.tail(2))
```
![image](https://github.com/user-attachments/assets/6febf6c0-12f9-4f02-a4d1-591f4b444048)

```
df.info()
```
![image](https://github.com/user-attachments/assets/16eda727-e9ee-4691-9806-0872a4fe0095)

```
print(df.describe())
```
![image](https://github.com/user-attachments/assets/5f8c9584-f9a5-48db-a083-6929058c615f)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/999079e0-f742-4e49-bea1-dbae9beda6af)

```
df.nunique()

```
![image](https://github.com/user-attachments/assets/74a0a42a-a1f6-42c3-a9a9-4b2e65a8de5b)

```
mn=df.TOTAL.mean()
mn
```
![image](https://github.com/user-attachments/assets/00739d8c-4823-4309-bda6-08587b667402)

```
df.TOTAL.fillna(mn,inplace=True)
df
```
![image](https://github.com/user-attachments/assets/4af0b795-c1c0-40e6-a107-8684dff7b5e3)

```
min=df.M4.min()
min
```

![image](https://github.com/user-attachments/assets/270f7d3e-52e4-4340-8f14-71dde08d5abc)

```
df.M4.fillna(min,inplace=True)
df
```
![image](https://github.com/user-attachments/assets/319e826f-a41c-4af2-8a8e-0e5650d482e0)

```
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```

![image](https://github.com/user-attachments/assets/2752d3ba-76fa-4354-b3f4-7f2c341147f6)

```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/0fef85cc-b2d1-4f5b-a848-06cb9d7fc499)

```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/09fcc7c6-c1a0-4cd8-baad-60c8a3edd1fd)

```
q1=af.quantile(0.25)
q2=af.quantile(0.50)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
low=q1-1.5*iqr
low
high=q3+1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/b4e317b2-f01e-421f-b811-f6e3c2879bc5)

```
af=af[((af>=low)&(af<=high))]
af
```
![image](https://github.com/user-attachments/assets/04553979-429a-4fbd-97bb-2cd9b933c389)

```
af.dropna()
```
![image](https://github.com/user-attachments/assets/6ea23c6f-6e41-405d-a938-9451d8945a60)

```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/e4a590c3-911d-4ef5-8da3-763b15c45e8c)

```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/bb3424e5-ef84-46fc-bd07-660a93040391)

```
data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,102,105]
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/1b601ab1-e8ae-47d0-a0e7-66ab5878f580)

```
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
z
```
![image](https://github.com/user-attachments/assets/455cfa23-e9a1-4f9e-ba3b-6b2c64ab5d79)

# Result
Hence the data was cleaned , outliers were detected and removed.
