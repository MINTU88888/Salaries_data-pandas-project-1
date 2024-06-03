# Salaries_data-pandas-project-1

1.  Display Top 10 Rows of The Dataset
2. Check Last 10 Rows of The Dataset
3. Find Shape of Our Dataset (Number of Rows And Number of Columns)
4.  Getting Information About Our Dataset Like Total Number Rows, Total Number of Columns, Datatypes of Each Column And Memory Requirement
5. Check Null Values In The Dataset
6. Drop ID, Notes, Agency, and Status Columns
7. Get Overall Statistics About The Dataframe
8. Find Occurrence of The Employee Names  (Top 5)
9. Find The Number of Unique Job Titles
10.Total Number of Job Titles Contain Captain
11. Display All the Employee Names From Fire Department
12. Find Minimum, Maximum, and Average BasePay
13. Replace 'Not Provided' in EmployeeName' Column to NaN 
14. Drop The Rows Having 5 Missing Values
15. Find Job Title of ALBERT PARDINI
16. How Much ALBERT PARDINI Make (Include Benefits)?
17. Find Average BasePay of Employee Having Job Title ACCOUNTANT  
18. Find Top 5 Most Common Jobs

import pandas as pd
import numpy as np
data = pd.read_csv("Salaries.csv")
print(data)

# Display Top 10 Rows of The Dataset
print(data.head(10))

# Check Last 10 Rows of The Dataset
print(data.tail(10))

# Find Shape of Our Dataset (Number of Rows And Number of Columns)
#(shape is not a method it is a attribute in pandas dataframe)
print(data.shape)
print("number of Rows",data.shape[0])
print("number of Columns",data.shape[1])

# Getting Information About Our Dataset Like Total Number Rows, Total Number of Columns, Datatypes of Each Column And Memory Requirement
print(data.info())

# Check Null Values In The Dataset
print(data.isnull().sum())

# Drop ID, Notes, Agency, and Status Columns
print(data.columns)
data1 = data.drop(["Id","Status","Notes","Agency"],axis=1)
print(data1.head())

# Get Overall Statistics About The Dataframe
print(data1.describe(include = "all"))

# Find Occurrence of The Employee Names  (Top 5)
print(data1['EmployeeName'].value_counts().head())

# Find The Number of Unique Job Titles
print(data1['JobTitle'].nunique())

## Total Number of Job Titles Contain Captain
print(len(data1["JobTitle"].str.contains("CAPTAIN",case = False)))

# Display All the Employee Names From Fire Department
print(data1[data1["JobTitle"].str.contains('fire',case=False)]["EmployeeName"])

# Find Minimum, Maximum, and Average BasePay
print(data1["BasePay"].describe())

# Replace 'Not Provided' in EmployeeName' Column to NaN 
print(data1["EmployeeName"].replace("Not provided", np.nan))

# Drop The Rows Having 5 Missing Values
print(data1.isnull().sum(axis=1))

# Find Job Title of ALBERT PARDINI
print(data1[data1["EmployeeName"] == 'ALBERT PARDINI']['JobTitle'])

# How Much ALBERT PARDINI Make (Include Benefits)?
print(data1[data1["EmployeeName"]== "ALBERT PARDINI"]["TotalPayBenefits"])

#Find Average BasePay of Employee Having Job Title ACCOUNTANT  
print(data1[data1["JobTitle"] =='ACCOUNTANT']["BasePay"].mean())

# Find Top 5 Most Common Jobs
print(data1["JobTitle"].value_counts().head())
