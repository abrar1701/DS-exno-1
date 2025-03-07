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
## #DISPLAY THE INFORMATION ABOUT CSV AND RUN THE BASIC DATA ANALYSIS FUNCTIONS



# Result
          <<include your Result here>>
