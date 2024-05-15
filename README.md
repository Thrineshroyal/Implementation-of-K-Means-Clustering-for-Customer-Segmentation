# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1.Import the necessary packages using import statement.

2.Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().

3.Import KMeans and use for loop to cluster the data.

4.Predict the cluster and plot data graphs.

5.Print the outputs and end the program

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Thrinesh Royal.T
RegisterNumber:  212223230226
*/
```
<br>
<br>

```python
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv(r'Mall_Customers.csv')

data.head()
data.info()
data.isnull().sum()
```
## Output:
![image](https://github.com/SANTHAN-2006/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/80164014/efe6ddbc-866d-491d-8ed7-794d5ce98464)

<br>
<br>

```python
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```

## Output :
![image](https://github.com/SANTHAN-2006/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/80164014/432f2d21-087c-459e-963c-c4589023a848)

<br>
<br>

```python
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred
```

## Output :
![image](https://github.com/SANTHAN-2006/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/80164014/f53bca8f-1780-4783-b5ea-e52c82f3cc8e)


<br>
<br>

```python
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```
## Output :
![image](https://github.com/SANTHAN-2006/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/80164014/504b4365-3fb9-4b6e-8a21-519facbc2397)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
