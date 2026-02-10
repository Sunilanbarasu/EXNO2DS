# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```   
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt=pd.read_csv("/content/titanic_dataset.csv")
dt
```
<img width="1050" height="405" alt="image" src="https://github.com/user-attachments/assets/bf2ed7da-2c10-4865-acd9-8caadb0f002e" />

```
dt.info()
```
<img width="646" height="293" alt="image" src="https://github.com/user-attachments/assets/894735d5-dd04-4b94-b857-6f7ce1515896" />


```
dt.shape
```
<img width="210" height="175" alt="image" src="https://github.com/user-attachments/assets/dcd68c8d-54a5-4985-b27a-f6894e858a55" />

```
dt.set_index("PassengerId",inplace=True)
dt.describe()
```
<img width="221" height="173" alt="image" src="https://github.com/user-attachments/assets/8ccc5f42-de16-42d8-8e71-cef5f9c6ad47" />


```
dt.nunique()
```
<img width="167" height="404" alt="image" src="https://github.com/user-attachments/assets/502da499-e64e-4385-95c6-dac5f00a825a" />


```
dt["Survived"].value_counts()
```

<img width="732" height="447" alt="image" src="https://github.com/user-attachments/assets/dbf7e595-cf8e-440a-8b83-6f42ea938adf" />

```
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```
<img width="1079" height="427" alt="image" src="https://github.com/user-attachments/assets/bf7cd078-ba58-4f01-afe4-9553639830ef" />


```
sns.countplot(data=dt,x="Survived")
```
<img width="160" height="33" alt="image" src="https://github.com/user-attachments/assets/5df8b512-aa74-4a1c-891c-70a5ddbadf40" />


```
dt
```
<img width="1104" height="459" alt="image" src="https://github.com/user-attachments/assets/93b4f860-9d06-4628-8950-23501543c398" />


```
dt.Pclass.unique()
```
<img width="759" height="501" alt="image" src="https://github.com/user-attachments/assets/da9bdc18-1b32-4cc6-8665-a3584e7f7e49" />


```
dt.rename(columns={'Sex':'Gender'}, inplace=True)
dt
```
<img width="616" height="468" alt="image" src="https://github.com/user-attachments/assets/5174a62f-9fc7-4767-b043-d884ac944156" />


```
sns.catplot(x="Gender", col="Survived", kind="count", data=dt, height=5, aspect=.7)
```
<img width="627" height="457" alt="image" src="https://github.com/user-attachments/assets/84e7cf8d-d430-43d7-88fe-6300bdfbca17" />


```
sns.catplot(x='Survived',hue="Gender", data=dt, kind='count')
```
<img width="614" height="451" alt="image" src="https://github.com/user-attachments/assets/c86d879f-e645-49f3-8b73-8f28ecc39254" />


```
dt.boxplot(column="Age",by="Survived")
```
<img width="645" height="594" alt="image" src="https://github.com/user-attachments/assets/62ca6220-4a56-4837-a02c-97564c5f1ff0" />


```
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```
<img width="762" height="437" alt="image" src="https://github.com/user-attachments/assets/45264397-5c78-4eb9-8e30-10586a4a2986" />


```
sns.jointplot(x="Age",y="Fare",data=dt)
```
<img width="1104" height="484" alt="image" src="https://github.com/user-attachments/assets/153d74b6-05f3-4411-b6b9-466ce7a6ab2e" />


```
fig,ax1=plt.subplots(figsize=(8,5))
sns.boxplot(ax=ax1,x="Pclass",y="Age",hue="Gender",data=dt)
```
<img width="859" height="484" alt="image" src="https://github.com/user-attachments/assets/d5dc92fc-c1e4-4fb7-b290-5fb8777112ff" />


```
sns.catplot(data=dt, col="Survived", x="Gender", hue="Pclass", kind="count")
```
<img width="754" height="336" alt="image" src="https://github.com/user-attachments/assets/f985172f-598e-4bae-8886-f8ad400ffc54" />


```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

dt = pd.read_csv("titanic_dataset.csv")
dt_numeric = dt.select_dtypes(include='number')
corr = dt_numeric.corr()
plt.figure(figsize=(10,6))
sns.heatmap(corr, annot=True, cmap='coolwarm')
plt.show()
```
<img width="652" height="330" alt="image" src="https://github.com/user-attachments/assets/1b1fce6b-1a0e-4777-ad8a-c60403e9ecdc" />


```
sns.pairplot(dt)
```
<img width="1091" height="652" alt="image" src="https://github.com/user-attachments/assets/776f7517-7fbb-4b2d-ae4c-f7df6b08f65d" />

# RESULT
  Thus, the Exploratory Data Analysis on the given data set was performed successfully.
