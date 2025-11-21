# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load and preprocess data: Import data, inspect it, and handle missing values if any.
2. Determine optimal clusters: Use the Elbow Method to identify the number of clusters by plotting WCSS against cluster numbers.
3. Fit the K-Means model: Apply K-Means with the chosen number of clusters to the selected features.
4. Assign cluster labels to each data point.
5. Plot data points in a scatter plot, color-coded by cluster assignments for interpretation.
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: DINESH S
RegisterNumber: 212224230069
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
```
```
data.head()
```
```
data.info()
```
```
data.isnull().sum()
```
```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++",n_init=10)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
```
```
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
```
km = KMeans(n_clusters=5, n_init=10)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred
```
```
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
```
```
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster2")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster4")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster5")
plt.legend()
plt.title("Customer Segments")
```

## Output:


<img width="570" height="237" alt="image" src="https://github.com/user-attachments/assets/e89b94ef-11a6-4b4f-95bd-0307ccaec597" />


<img width="566" height="280" alt="image" src="https://github.com/user-attachments/assets/fff1fd7a-4540-4a7c-b20e-1a2ae61e280b" />

,
<img width="279" height="174" alt="image" src="https://github.com/user-attachments/assets/94fb8cc4-3eb6-4b07-91a4-e74457d2e4b8" />





<img width="732" height="761" alt="image" src="https://github.com/user-attachments/assets/eca0831d-fff5-4c08-af94-7040e51ebc9d" />


<img width="732" height="402" alt="image" src="https://github.com/user-attachments/assets/584ff8ea-c8ee-45ed-9b27-0850cc71cfe1" />


<img width="866" height="777" alt="image" src="https://github.com/user-attachments/assets/c3af2332-f5e2-4b96-8185-acb3c99edfd7" />

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
