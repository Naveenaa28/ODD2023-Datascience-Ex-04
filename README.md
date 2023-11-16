## EX-04-MULTIVARIATE-ANALYSIS
## AIM:
To perform Multivariate EDA on the given data set.

## EXPLANATION:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
Step1:Import the built libraries required to perform EDA and outlier removal.

Step2:Read the given csv file.

Step3:Convert the file into a dataframe and get information of the data.

Step4:Return the objects containing counts of unique values using (value_counts()).

Step5:Plot the counts in the form of Histogram or Bar Graph.

Step6:Use seaborn the bar graph comparison of data can be viewed.

Step7:Find the pairwise correlation of all columns in the dataframe.corr()

Step8:Save the final data set into the file.

## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt = pd.read_csv('/content/titanic_dataset.csv')

dt

dt.info()

dt.set_index("PassengerId",inplace=True)

dt.shape

dt.describe()

dt.nunique()

dt["Survived"].value_counts()

per = (dt["Survived"].value_counts()/dt.shape[0]*100).round(2)

per

sns.countplot(data=dt,x="Survived")

dt

dt.Pclass.unique()

dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt

sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5, aspect=.7)

sns.catplot(x='Survived',hue = "Gender",data = dt,kind = "count")

fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(ax=ax1,data=dt,x="Survived",hue="Pclass",palette="rainbow")
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
  height = p.get_height()
  graph.text(p.get_x()+p.get_width()/2, height + 20.8,height,ha="left")

dt.boxplot(column="Age",by="Survived")

sns.scatterplot(x = dt["Age"],y = dt["Fare"])

fig, ax1 = plt.subplots(figsize = (8,5))
pt = sns.boxplot(ax = ax1,x = 'Pclass',y = 'Age', hue='Gender',data=dt)

sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count")

g = sns.catplot(data=dt,col="Survived",x="Gender",hue ="Pclass",kind = "count",legend=True)
g.fig.set_size_inches(8,5)
g.fig.subplots_adjust(top=0.81,right=0.86)
ax = g.facet_axis(0,0)
for p in ax.patches:
  ax.text(p.get_x()- 0.01,p.get_height() * 1.02,'{0:.1f}'.format(p.get_height()),color='red',rotation='horizontal',size='small')

## Co-relation
corr = dt.corr()
sns.heatmap(corr,annot=True)

sns.pairplot(dt)
```
## OUTPUT:
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/52d1e40e-f3f3-482a-8835-0a0baa2279e4)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/99fb0ad7-0f4f-45af-a230-97e438a364f8)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/a48e7e55-e71c-46e8-ae9d-0061925284ea)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/8000d512-5438-4ad1-b84c-5e5b27eefa89)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/16345b4b-3bca-443e-b724-8c270828df48)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/8d8193fe-a3eb-4d91-aee4-7fff67fce160)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/c57db0dd-772e-412e-a42b-f5e37390ba57)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/c56f4bf7-470f-41d5-a6f2-8f6dcfa00f8b)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/d3d833c8-297b-42a8-9bf9-582acce02668)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/de543944-8b9d-428e-8d99-6204cf932dba)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/65bfcc32-9ead-440f-90bd-efedb618a762)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/f82300dc-d53f-42ea-9016-4fa215f3e7b9)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/eb3ad7d4-7826-458a-8f7b-1b724921d13b)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/95cc75d9-dd93-46a1-9486-3c6344bed552)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/7ed189b8-c257-4f7a-9087-461728e26aec)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/a094855b-e5cf-4a47-9e3d-bd9be9b4105d)
![image](https://github.com/Naveenaa28/ODD2023-Datascience-Ex-04/assets/131433133/11d91f9a-0882-4da2-8151-07df40d71ef5)
## RESULT:
Thus the program to perform EDA on the given data set is successfully executed.
