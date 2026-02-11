### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 06.02.2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program 1:
```python
import pandas as pd
df = pd.read_csv("C:\\Users\\admin\\Downloads\\clustervisitor.csv")
df
cluster={"Young":(df['Age']<=30),"Middle":((df['Age']>30)&(df['Age']<=50)),"Old": (df['Age']>50)}
count=[]
for group,condition in cluster.items():
    visitors=df[condition]
    count.append(len(visitors))
    print(f"The visitors on {group} age are")
    print(visitors)
    print("count=",len(visitors))
```
### Output:

<img width="1047" height="847" alt="Screenshot 2026-02-11 112543" src="https://github.com/user-attachments/assets/0b1bdbe8-ba34-4c90-89f0-4acb6aa60caf" />

### Visualization:
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(['Young','Middle','Old'],count,color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:
<img width="1047" height="688" alt="image" src="https://github.com/user-attachments/assets/d995ef9e-9fb1-420d-bc35-ce1ce8856591" />


### Program 2:
```python
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=3,random_state=55)
df3['cluster']=k.fit_predict(newdf)
df3
```
### Output:
<img width="1126" height="899" alt="Screenshot 2026-02-11 122736" src="https://github.com/user-attachments/assets/60766422-7401-4128-9c61-4e52e11005b6" />

<img width="1126" height="382" alt="image" src="https://github.com/user-attachments/assets/5947cfe6-3e7c-4190-81a0-f7d6f5a040cc" />


### Visualization:
```python
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.scatter(x=df3['Age'],y=df3['Income'], c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('Visitor Distribution in Different Clusters')
plt.show()
```

### Output:
<img width="1118" height="697" alt="image" src="https://github.com/user-attachments/assets/d8b293bf-6d35-4315-9733-d4fd6450f92d" />




### Result:
The implement Cluster and Visitor Segmentation for Navigation patterns in python is execute successfully.
