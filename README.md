# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Data Loading and Preprocessing
2. Determine Optimal Clusters (Elbow Method)
3. Train Final K-Means Model and Assign Clusters
4. Visualize and Interpret Segmentation

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Elfreeda Jesusha J
RegisterNumber: 212224040084 
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("/content/drive/MyDrive/Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
    kmeans=KMeans(n_clusters=i,init="k-means++", random_state=42)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No_of_Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
plt.show()

km=KMeans(n_clusters=5, random_state=42) 
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
print(y_pred)
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="blue",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="yellow",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="violet",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="orange",label="cluster4")
plt.legend()
plt.title("Customer Segment")

```

## Output:

head() function

<img width="410" height="147" alt="exp10ml1" src="https://github.com/user-attachments/assets/d2bf8ffe-65fe-4bf6-b00f-a8d2fb1e00a5" />

info() function

<img width="569" height="164" alt="exp10ml2" src="https://github.com/user-attachments/assets/377990df-40bf-4637-b962-81fb4453cb8b" />

Checking for non null values

<img width="148" height="175" alt="exp10ml3" src="https://github.com/user-attachments/assets/3a671e7b-f58a-49d9-84fa-7fb981ce2a40" />

Plotting using elbow method

<img width="597" height="455" alt="download" src="https://github.com/user-attachments/assets/1b1592a7-41af-4021-88ff-bb4714d00638" />

Final Result

<img width="553" height="435" alt="download" src="https://github.com/user-attachments/assets/190b28bf-3b05-469f-9cdc-ad75e14f8524" />

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
