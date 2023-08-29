# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Remove outliers using IQR
### STEP 3
After removing outliers in step 1, you get a new dataframe.
### STEP 4
Use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result
### STEP 5
For the data set height_weight.csv to find the following;
(i) Using IQR detect weight outliers and print them
(ii) Using IQR, detect height outliers and print them

# PROGRAM
```
import pandas as pd
import seaborn as sns

age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af = pd.DataFrame(age)
af
sns.boxplot(data = af)
sns.scatterplot(data = af)

q1 = af.quantile(0.25)
q2 = af.quantile(0.5)
q3 = af.quantile(0.75)
iqr = q3 - q1
iqr

low = q1 - 1.5*iqr
low

high = q3 + 1.5*iqr
high

aq = af[((af>=low) & (af<=high))]
aq.dropna()

sns.boxplot(data = af)

af = af[((af>=low) & (af<=high))]
af.dropna()

sns.boxplot(data = af)

sns.scatterplot(data = af)

sns.scatterplot(data = af)

import pandas as pd
import numpy as np
from scipy import stats
import seaborn as sns

data = {'weight':[12,15,18,21,24,27,30,33,36,39,42,45,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df = pd.DataFrame(data)
df

sns.boxplot(data = df)

z = np.abs(stats.zscore(df))
print(df[z['weight']>3])

val = [12,15,18,21,24,27,30,33,36,39,42,45,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]

out = []
def d_o(val):
  ts = 3
  n = np.mean(val)
  sd = np.std(val)
  for i in val:
    z = (i-n)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out

op = d_o(val)
op

id = pd.read_csv("iris.csv")
id

sns.boxplot(x = 'sepal_width',data = id)

c1 = id.sepal_width.quantile(0.25)
c3 = id.sepal_width.quantile(0.75)
iq = c3-c1
iq

rid = id[((id.sepal_width<(c1-1.5*iq)) | (id.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

delid = id[~((id.sepal_width<(c1-1.5*iq)) | (id.sepal_width>(c3+1.5*iq)))]
delid

sns.boxplot(x='sepal_width',data = delid)
```

# OUTPUT:
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/5cfadac2-4cf2-4619-b0b9-27803d2f64c1)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/939c364d-fe73-4bb6-91c8-68bac69c5c0e)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/67ea1cdb-3812-4be6-873c-7564e981d6b8)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/2665cd96-2268-464a-b305-6786328b3d52)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/5c48f61c-28ba-4742-981e-805b6d7d950a)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/6506543c-4795-4f75-aa39-304026fe81c6)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/4ce19043-9500-4fef-a871-0318297af769)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/0e391fe4-4405-4536-ada5-4362d417ef80)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/c3a02353-e146-4933-bd2f-fc40a4004e48)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/995eec4a-8dc7-4ed8-b6e1-f131d9ad20a9)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/a6a88214-f01f-42bf-a65d-24534ad13b38)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/1fe40cc1-baed-4f36-96b0-3f3b5808a79a)
![image](https://github.com/Anbuselvan04/ODD2023---Datascience---Ex-02/assets/119410896/053fd045-ff07-423b-8565-0276467e2bab)
