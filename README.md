# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output:

## Data Cleaning      

```
import pandas as pd
r=pd.read_csv("/content/SAMPLEIDS.csv")
r
```
![image](https://github.com/user-attachments/assets/bdbdb8e6-c4bf-4a0c-b5e7-3835d0196374)

```
r.head()
```
![image](https://github.com/user-attachments/assets/e98b0d63-3c73-420a-8fd8-0872e8d8a8c4)

```
r.tail()
```
![image](https://github.com/user-attachments/assets/f71dd6bc-c07e-4397-8f5c-163a4a66ee6e)

```
r.isnull()
```
![image](https://github.com/user-attachments/assets/4b381bdd-e735-4dc1-b1db-b1c085c05bd1)

```
r.fillna(1)
```
![image](https://github.com/user-attachments/assets/cfbab384-fc03-4b85-8e20-513ee4635bd7)

```
r.dropna()
```
![image](https://github.com/user-attachments/assets/37f51f73-b23e-4ee4-9db1-042f3497450a)

```
r.notnull()
```
![image](https://github.com/user-attachments/assets/b9a2f09b-ee73-43bb-917b-ecf61c32f01b)

```
s=r[r['TOTAL']> 125]
s
```
![image](https://github.com/user-attachments/assets/4f9e7eaf-06f6-4718-afcd-93655da26885)

```
s=r[r['NAME'].str.startswith(('A','N')) & (r['TOTAL']> 100)]
s
```
![image](https://github.com/user-attachments/assets/45eeea41-134e-4b3a-86b6-b461d1c3e4b6)

```
r.iloc[:4]
```
![image](https://github.com/user-attachments/assets/8957294b-3e2c-4d84-a7c8-3cfe7a29ca3d)

```
r.iloc[2:4,1:3]
```
![image](https://github.com/user-attachments/assets/a6ace0c2-7d56-44f8-bb98-f757eba0ff33)

```
r.iloc[[1, 2, 5], [2, 3]]
```
![image](https://github.com/user-attachments/assets/fcb18064-f283-42ba-b1db-670c1f29e8b3)


```
import pandas as pd
d=pd.read_csv("/content/iris.csv")
d
```
![image](https://github.com/user-attachments/assets/9f7cd76b-b6b4-41ea-b3b6-69886b6c11aa)

```
d.head(10)
```
![image](https://github.com/user-attachments/assets/0a83034a-87a9-4bc9-a148-a4aa1e87b114)

```
d.tail(10)
```
![image](https://github.com/user-attachments/assets/9074caac-f229-422b-8e33-26d055995927)

```
d.isnull()
```
![image](https://github.com/user-attachments/assets/e8e965e3-7cd9-4d0d-b575-25e82417d39d)

```
d.fillna(0)
```
![image](https://github.com/user-attachments/assets/6b1fc560-8e7d-43e3-9b59-5f073b414bad)

```
d.shape
```
![image](https://github.com/user-attachments/assets/e75276e8-2ce2-4277-88dd-156096d8408e)

```
d.describe()
```
![image](https://github.com/user-attachments/assets/88d49a63-e89f-4a85-a344-e45420b7577b)

```
d.isnull().sum()
```
![image](https://github.com/user-attachments/assets/d32cff73-7a36-40ef-9c0d-bbc02b8b2bf6)

```
sns.boxplot(x='sepal_width',data=d)
```
![image](https://github.com/user-attachments/assets/0fa737a1-c4a8-4aca-83c4-dad9e27aa06e)
```
c1=d.sepal_width.quantile(0.25)
c3=d.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/8d3647f9-3039-45af-aa5f-4017716df509)

```
rid=d[((d.sepal_width<(c1-1.5*iq))|(d.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/146e236b-58d2-4afe-8fec-025efdec5b22)

```
delid=d[~((d.sepal_width<(c1-1.5*iq))|(d.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/0fe7d343-864f-48ab-bbcb-568b77f9e48a)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/879e004f-3142-4f41-97f5-bb4e85c97251)


```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
```
```
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/f64f336a-857b-486c-80cd-38a94fbf8abe)

```
 df = pd.read_csv("heights.csv")
 q1 = df['height'].quantile(0.25)
 q2 = df['height'].quantile(0.5)
 q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/54e25015-39f7-4358-94eb-92b0e6559be2)

```
low = q1- 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/bead2ceb-5e2e-488b-b55b-d100deae8279)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/e88a44e5-3387-4251-802b-b1c0e10e4741)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/2a3ea88d-043a-4112-a3b7-7e5494af7162)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/6dd528d5-a29d-4e71-870a-8c40eed5c359)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/9f8186db-4b97-468b-81cc-340192c2766d)



# Result
          
