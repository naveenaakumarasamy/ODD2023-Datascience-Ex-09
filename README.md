# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

## Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

## ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.

## CODE
```
Developed by : Naveenaa A K
Reg no: 212222230094
```
### Importing packages and Load Data    
```
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
df=sns.load_dataset("tips")
df.head()
df.isnull().sum()
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/365e58ed-3c8b-4018-bd97-590232e63c2a)
### #ANALYZING OUTLIERS
```
plt.title("Data with Outliners")
sns.boxplot(data=df)
plt.show()
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/922e9556-e254-4e04-b2e8-d4d3a8d04c18)

### REMOVINF OUTLIERS 
```
cols=["size","tip","total_bill"]
q1=df[cols].quantile(0.25)
q3=df[cols].quantile(0.75)
iqr=q3-q1
df=df[~((df[cols]<(q1-1.5*iqr))|
(df[cols]>(q3+1.5*iqr))).any(axis=1)]
plt.title("Outliers Removed")
sns.boxplot(data=df)
plt.show()
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/c66712e7-946c-4227-a553-e4547ac02d7b)
### 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x=df["day"],y=df["total_bill"],hue=df["day"])
plt.legend(loc="center")
plt.title("highest total bill amount by day of the week")
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/8b39ac4f-70c2-418d-88ae-f62e2ffdf2bb)

### 2.What is the average tip amount given by smokers and non-smokers?
```
plt.figure(figsize=(6,3))
sns.boxplot(x=df["smoker"],y=df["tip"],hue=df["smoker"])
plt.title("Tip amount given by Smokers and Non-Smokers")
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/986b6107-9ea1-4357-955e-f9dc20a0aafb)

### 3.How does the tip percentage vary based on the size of the dining party?
```
df["tip_percent"]=df["tip"]/df["total_bill"]
sns.scatterplot(x=df['size'],y=df['tip_percent'],data=df)
plt.title("Tip Percentage by Dining Party Size")
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/4a21d136-f8d4-43ca-860e-8837c62ef5ec)

### 4.Which gender tends to leave higher tips?
```
sns.scatterplot(x=df["day"],y=df["total_bill"],
          hue=df["day"])
plt.legend(loc="best")
plt.title("Relation Between Total Bill Amount by Day
            of the Week")
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/a178ab9d-412d-487e-a6a0-5aff4a1203ef)

### 5.Is there any relationship between the total bill amount and the day of the week?
```
sns.scatterplot(x=df["day"],y=df["total_bill"],
          hue=df["day"])
plt.legend(loc="best")
plt.title("Relation Between Total Bill Amount by Day
            of the Week")
```

![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/f7a5dca7-5d71-4b23-b791-da43b7480330)

###  6.How does distribution of total bill amounts vary across different time periods(lunch vs dinner)?

```
sns.histplot(data=df,x="total_bill",hue="time",
                 lement="step",stat="density")
plt.title("Total Bill Amounts by Time of Day")
plt.show()
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/5c432a02-4827-4cc4-8edf-ca050fe457e5)

### 7. Which dining party size group tends to have the highest average total bill amount?

```
plt.figure(figsize=(6,3))
sns.barplot(x=df["size"],y=df["total_bill"],hue
                =df["size"])
plt.title("Highrst Average Total Bill Amount by Dining
             Party Size")
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/372e6b5e-e107-4d92-a2a2-3fa934ceaec1)

### 8. What is the distribution of tip amounts for each day of the week?
```
sns.boxplot(x="day", y="tip", data=df)
plt.title("Distribution of Tip Amount by Day \
           of Week")
plt.show()
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/400010d5-10bb-4108-9325-98597ffaae6a)
### 9.How does the tip amount vary based on type of service(lunch vs dinner)?
```
plt.figure(figsize=(6,3))
sns.violinplot(x="time",y="tip",data=df)
plt.title("Tip Amount Based on Type of Service")
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/79bb7c74-9f88-49b7-b6ba-ef22426674fd)

### 10.Is there any correlation between the total bill amount and the tip amount?
```
sns.scatterplot(x="total_bill",y="tip",data=df)
plt.title("Correlation between Total Bill Amount and
           Tip Amount")
plt.show()
```
![image](https://github.com/naveenaakumarasamy/ODD2023-Datascience-Ex-09/assets/113497406/a09b65f7-db45-4580-9985-2fdb7dd2de60)

## RESULT:
Thus, Data Visualization on a complex dataset and save the data to a file has been performed successfully.
