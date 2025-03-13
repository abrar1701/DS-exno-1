# Exno:1
<br/>
 **Name : Mohamed Abrar M** 
 <br/>
 **Reg no: 212223040111**
 <br/><br/>
 **Data Cleaning Process** 
 <br/>

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
## READ CSV FILE

```py
import pandas as pd
from google.colab import drive
drive.mount('/content/drive')
```
![image](https://github.com/user-attachments/assets/10f4bb53-1287-4e48-8be8-36eb15a91609)
```py
ls 'drive/MyDrive/Colab Notebooks'
```
![image](https://github.com/user-attachments/assets/e25ba3aa-4249-4b63-b4ad-e0a1c26fbb82)
```py
df = pd.read_csv('drive/MyDrive/Colab Notebooks/Loan_data.csv')
df
```
![image](https://github.com/user-attachments/assets/d3d6d56f-2f76-4811-ac2c-b117994c9888)
## DISPLAY THE INFORMATION ABOUT CSV AND RUN THE BASIC DATA ANALYSIS FUNCTIONS

```py
df.head()
```
![image](https://github.com/user-attachments/assets/58329aed-335a-40fb-a79f-aba506d7579b)

```py
df.tail()
```
![image](https://github.com/user-attachments/assets/0ebe2254-8493-47bc-aef3-b01ef8f3af59)

```py
df.info()
```
![image](https://github.com/user-attachments/assets/b2fd7b5a-8cac-4fa8-8914-aa75759a5e54)

```py
df.describe()
```
![image](https://github.com/user-attachments/assets/c70676d4-4069-44dc-b2be-a375f8491ed7)

## CHECK OUT NULL VALUES IN DATA SET USING FUNCTION

```py
isnull = df.isnull()
isnull
```
![image](https://github.com/user-attachments/assets/1f25411f-a1df-4029-b5e6-cae4a6e9bc38)

## DISPLAY THE SUM ON NULL VALUES IN EACH ROWS

```py
sum_of_null = df.isnull().sum()
sum_of_null
```
![image](https://github.com/user-attachments/assets/ae3eb68c-118b-4e87-b7b2-dcec37922dc5)

## DROP NULL VALUES
```py
drop_null = df.dropna()
drop_null
```
![image](https://github.com/user-attachments/assets/f0aa8883-a070-427e-bcb5-82b456fbebd0)

## FILL NULL VALUES WITH CONSTANT VALUE "O"
```py
fill_0 = df.fillna("o")
fill_0
```
![image](https://github.com/user-attachments/assets/f6cae714-5a19-454d-b769-0391dba253dd)

## FILL NULL VALUES WITH ffill or bfill METHOD
```py
ffill = df.fillna(method='ffill')
ffill
```
![image](https://github.com/user-attachments/assets/b30c2908-a5b5-4e9a-8b4c-7200daf6e30d)

```py
bfill = df.fillna(method='bfill')
bfill
```

## CALCULATE MEAN VALUE OF A COLUMN AND FILL IT WITH NULL VALUES
```py
columns_to_fill = ['Credit_History', 'LoanAmount', 'Loan_Amount_Term']
df[columns_to_fill] = df[columns_to_fill].apply(lambda col: col.fillna(col.mean()))
df
```
![image](https://github.com/user-attachments/assets/099b2925-d274-4b1e-8092-84bb01a2e304)

## DROP NULL VALUES
```py
df.dropna()
df
```
![image](https://github.com/user-attachments/assets/3a95f944-5ba5-46de-9cfc-d6cb04cf3a86)

<br/>
<br/>

```py
import pandas as pd
import seaborn as sns
import numpy as np

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/user-attachments/assets/93fea405-dbe6-4212-8b79-4aec02fdff22)

## USE BOXPLOT FUNCTION HERE TO DETECT OUTLIER
```py
sns.boxplot(data = af)
```
![image](https://github.com/user-attachments/assets/54eac1e9-7d53-4188-a90e-ddc165fa9f4f)

## PERFORM IQR METHOD AND DETECT OUTLIER VALUES
```py
Q1 = np.percentile(af, 25)
Q3 = np.percentile(af, 75)
IQR = Q3 - Q1
IQR
```
![image](https://github.com/user-attachments/assets/3fb7a95a-70d6-49df-8a4a-095e7575fda4)

```py
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
lower_bound
```
![image](https://github.com/user-attachments/assets/33526a47-cc67-45b8-bc27-68ef96ccae85)
```py
upper_bound
```
![image](https://github.com/user-attachments/assets/af99486d-daa4-4b61-aed4-22650efb2127)

## REMOVE OUTLIERS
```py
outliers = [x for x in age if x < lower_bound or x > upper_bound]
outliers
```
![image](https://github.com/user-attachments/assets/4a09bd8f-f9d3-45da-a598-0a12e57b5ee9)

```py
af = af[((af >= lower_bound) & (af <= upper_bound))]
af
```
![image](https://github.com/user-attachments/assets/9eea273e-8299-4f6c-9e66-a7fad01f5947)

```py
af.dropna()
```
![image](https://github.com/user-attachments/assets/9316020e-1451-445b-8765-9311d1df4a6d)

## USE BOXPLOT FUNCTION HERE TO CHECK OUTLIER IS REMOVED
```py
sns.boxplot(data = af)
```
![image](https://github.com/user-attachments/assets/8ab9e29c-f4f2-48ad-9a3c-412a3a9b5500)

<br/>
<br/>

```py
from scipy import stats
import matplotlib.pyplot as plt

data = [1, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60, 63, 66, 69, 72, 75, 78, 81, 84, 87, 90, 93, 96, 99, 158]
df = pd.DataFrame(data, columns=['Data'])
df
```
![image](https://github.com/user-attachments/assets/2ab07cfe-4efb-4a8c-a970-7fb60f704403)

## USE BOXPLOT FUNCTION HERE TO DETECT OUTLIER
```py
sns.boxplot(data=df, y='Data')
plt.show()
```
![image](https://github.com/user-attachments/assets/c9000f85-955b-4cb4-839c-a93b61e755d1)

## PERFORM Z SCORE METHOD AND DETECT OUTLIER VALUES
```py
z_scores = stats.zscore(df['Data'])
outliers_z = df[(z_scores > 3) | (z_scores < -3)]
outliers_z
```
![image](https://github.com/user-attachments/assets/2dd0d0ed-16eb-4ec2-adaa-3220633765c8)

## REMOVE OUTLIERS
```py
threshold = 3
df_clean = df[(z_scores < threshold) & (z_scores > -threshold)]
```
## USE BOXPLOT FUNCTION HERE TO CHECK OUTLIER IS REMOVED
```py
sns.boxplot(data=df_clean, y='Data')
```

![image](https://github.com/user-attachments/assets/2eb371b3-589a-4b59-8b7c-808ad184f503)


# Result
Thus, we have read the given data, performed data cleaning, and saved the cleaned data to a file.
