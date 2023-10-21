# ODD2023-Datascience-Ex-04
# Ex-04-Multivariate-Analysis
# AIM
To perform Multivariate EDA on the given data set.

# Explanation:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

# ALGORITHM:
## STEP 1
Import the built libraries required to perform EDA and outlier removal.

## STEP 2
Read the given csv file

## STEP 3
Convert the file into a dataframe and get information of the data.

## STEP 4
Return the objects containing counts of unique values using (value_counts()).

## STEP 5
Plot the counts in the form of Histogram or Bar Graph.

## STEP 6
Use seaborn the bar graph comparison of data can be viewed.

## STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

## STEP 8
Save the final data set into the file

# PROGRAM
```
import pandas as pd
from scipy import stats
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/a07fdf19-ca29-4200-8ec0-a286d8061f3f)
```
df = pd.read_csv('diabetes.csv')
df
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/faf71084-cf93-4c1e-b142-7e70d171d6c8)
```
df.isnull().sum()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/2affd9c3-d59e-434a-8c76-b4cedd8b7f2b)
```
q1 = df.quantile(0.25)
q3 = df.quantile(0.75)
iqr = q3 - q1
iqr
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/8b8513da-051e-4e48-81b3-63d4fdfe44df)
```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
df = df[(df >= low) & (df <= high)]
df
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/da32058b-e2c8-45a0-8908-fbeabafcd09e)
```
sns.boxplot(df)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/27e686de-2a0a-4154-b79a-0114e55e6e42)
```
plt.figure(figsize = (14,6))
sns.scatterplot(x = 'Glucose',y='BloodPressure',data = df)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/e78b92dd-4838-477f-a51d-a0ae58809866)
```
sns.scatterplot(x = 'Glucose',y='Insulin',data = df)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/8204f208-648f-4e21-9c68-3a120fc6340c)
```
sns.scatterplot(x = 'Glucose',y='DiabetesPedigreeFunction',data = df)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/b94bfbfe-890e-4b2b-a115-07071a15215d)
```
sns.scatterplot(x = 'Glucose',y='Age',data = df)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/7a37dd0b-4135-4c11-aa7d-f542d15c85fb)
```
sns.heatmap(df.corr(),annot = True)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/5d259270-3f40-4248-8396-16e50d802e1a)
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/c268733c-9ecd-43b7-af4e-65ba8c7305d3)
```
df = pd.read_csv('employeesal.csv')
df
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/85ebd93a-c7cd-4988-91e9-e06421bae3a8)
```
df.isnull().sum()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/3f55e22b-6727-4186-aba4-5b6c26f4d26b)
```
numeric_cols = df.select_dtypes(include=[int, float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/068fbe57-9746-49c4-914a-cd6dd493bdc5)
```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
numeric_cols.dropna()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/13346234-b0de-485f-b797-d8a004b0d143)
```
sns.boxplot(numeric_cols)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/0acd7727-65e4-444c-b381-7293c3e5b6ea)
```
sns.scatterplot(x = 'Salary',y='Age',data = numeric_cols)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/f7da1867-b516-4510-9932-225c51115dd9)
```
sns.scatterplot(x = 'Experience_Years',y='Salary',data = numeric_cols)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/af974d01-c80a-45c1-a905-ea406942e8e4)
```
sns.scatterplot(x = 'Experience_Years',y='Age',data = numeric_cols)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/96bc08f2-654b-45d2-bf03-7526f8c4315c)
```
sns.heatmap(numeric_cols.corr(),annot = True)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/3bca0faf-7295-4a30-86e2-4cb6eb237abf)
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/62762635-6767-4ab9-a73e-5d27c78693c1)
```
df = pd.read_csv('SuperStore.csv')
df
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/321c116e-8893-49af-bbfa-f6c20c97298a)
```
df.isnull().sum()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/9218bed6-deea-4f4b-8633-bdfec40dabe3)
```
df.dropna()
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/d16b3daf-7204-4a83-afa9-eb9075c25725)
```
df.dtypes
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/b4b2839c-51af-4d67-9727-f9234d945d18)
```
numeric_cols = df.select_dtypes(include=[int,float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/aebaa37d-5353-4583-a0ef-fd1acea6b58d)
```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
```
```
sns.boxplot(numeric_cols)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/f5623ba8-2bd2-4d69-ba8b-5770b45e23b6)
```
sns.heatmap(numeric_cols.corr(),annot = True)
```
![image](https://github.com/Sudhar2303/ODD2023-Datascience-Ex-04/assets/133684710/3a781f1d-d427-4d64-945f-114c71441c01)

# RESULT
Thus we have read the given data and performed the multivariate analysis with different types of plots
