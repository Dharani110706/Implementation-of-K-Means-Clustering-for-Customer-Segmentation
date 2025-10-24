# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Data Preparation: Load data, handle missing values, and extract relevant features for clustering.

2.Determine Clusters: Use the Elbow Method to find optimal number of clusters based on WCSS.

3.K-Means Clustering: Fit the K-Means model with optimal clusters, predict cluster labels for data.

4.Visualization: Plot data points with distinct colors for each cluster to visualize clustering results.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by:DHARANI SREE P 
RegisterNumber:212224040071 
*/
```
```
import pandas as pd 
import matplotlib.pyplot as plt 
data=pd.read_csv("Mall_Customers.csv")
data.head()
```

## Output:

<img width="821" height="321" alt="image" src="https://github.com/user-attachments/assets/c7d0ee48-8246-4b2b-a82f-17d40a0c474a" />

```
data.info()
```
## Output:

<img width="642" height="276" alt="image" src="https://github.com/user-attachments/assets/0c0d5a31-4a9f-4db9-a1c9-697971a217dd" />

```
data.isnull().sum()
```

## Output:

<img width="297" height="274" alt="image" src="https://github.com/user-attachments/assets/8b6bb6c4-2d2e-4a11-9619-d6311b3799c7" />

```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No.of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
## Output:

<img width="812" height="602" alt="image" src="https://github.com/user-attachments/assets/375d25fc-4c7b-4174-9e13-40dcfd0623eb" />

```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
KMeans(n_clusters=5)
y_pred=km.predict(data.iloc[:,3:])
y_pred
```
## Output:

<img width="707" height="222" alt="image" src="https://github.com/user-attachments/assets/7bc7a44a-4915-45fb-9740-0bb3b1609e76" />

```
data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"], color = "gold")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"], color = "pink")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"], color = "green")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"], color = "blue")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"], color = "red")
plt.show()
```
## Output:

<img width="805" height="563" alt="image" src="https://github.com/user-attachments/assets/7b2c7c36-52d9-4353-8e23-240ca2f564e1" />

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
