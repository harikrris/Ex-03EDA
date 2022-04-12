# Ex-03EDA

## AIM
To perform EDA on the given data set. 

# Explanation
The primary aim with exploratory analysis is to examine the data for distribution, outliers and 
anomalies to direct specific testing of your hypothesis.
 

# ALGORITHM
### STEP 1

### STEP 2

### STEP 3

### STEP 4



# CODE
import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("titanic_dataset.csv")
df.info()
df.head()
df.isnull().sum()
df.drop("Cabin",axis=1,inplace=True)
df.info()
df.isnull().sum()
df["Age"]=df["Age"].fillna(df["Age"].median())
df.boxplot()
df.isnull().sum()
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df.isnull().sum()
df.boxplot()
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
print(IQR)
df_out = df[~((df < (Q1 - 1.5 * IQR)) |(df > (Q3 + 1.5 * IQR))).any(axis=1)]
print(df_out.shape)
df_out.boxplot()
df_out.info()
df["Embarked"].value_counts()
df_out["Embarked"].value_counts()
df["Pclass"].value_counts()
df_out["Pclass"].value_counts()
df["Survived"].value_counts()
df_out["Survived"].value_counts()
df["Sex"].value_counts()
df_out["Sex"].value_counts()
df["SibSp"].value_counts()
df_out["SibSp"].value_counts()
sns.countplot(x="Survived",data=df_out)
sns.countplot(x="Pclass",data=df_out)
sns.countplot(x="Sex",data=df_out)
sns.countplot(x="Embarked",data=df_out)
sns.countplot(x="SibSp",data=df_out)
df_out.info()
sns.displot(df_out["Fare"])
sns.displot(df_out["Age"])
sns.countplot(x="Pclass",hue="Survived",data=df_out)
sns.countplot(x="Sex",hue="Survived",data=df_out)
sns.countplot(x="SibSp",hue="Sex",data=df_out)
sns.countplot(x="Embarked",hue="Pclass",data=df_out)
sns.countplot(x="Survived",hue="Embarked",data=df_out)
sns.displot(df_out[df_out["Survived"]==0]["Age"])
sns.displot(df_out[df_out["Survived"]==1]["Age"])
sns.displot(df_out[df_out["SibSp"]==0]["Embarked"])
sns.displot(df_out[df_out["SibSp"]==1]["Embarked"])
pd.crosstab(df_out["Pclass"],df_out["Survived"])
pd.crosstab(df_out["Sex"],df_out["Survived"])
pd.crosstab(df_out["Pclass"],df_out["Sex"])
pd.crosstab(df_out["Sex"],df_out["Embarked"])
df.corr()
df_out.corr()
sns.heatmap(df.corr(),annot=True)
sns.heatmap(df_out.corr(),annot=True)
# OUPUT

[G32.ex3 - Jupyter Notebook (1).pdf](https://github.com/harikrris/Ex-03EDA/files/8469243/G32.ex3.-.Jupyter.Notebook.1.pdf)
