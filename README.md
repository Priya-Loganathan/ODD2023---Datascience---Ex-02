# Ex02-Outlier

# AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM:
### STEP 1:
Read the given Data.
### STEP 2:
Get the information about the data.
### STEP 3:
Detect the Outliers using IQR method and Z score.
### STEP 4:
Remove the outliers:
### STEP 5:
Plot the datas using box plot.

# PROGRAM:
Develpoed by : DELLI PRIYA L
Register no. : 212222230029
```
import pandas as pd
import seaborn as sns
age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/7b00053f-8891-4737-b2c0-04bb04a6ef6d)

```
sns.boxplot(data=af)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/98c92c73-3212-4b50-be0f-d071b165dcdb)

```
sns.scatterplot(data=af)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/c1998818-aead-4c8b-83ec-b3deb0d1a8ac)

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
irq=af.quantile(0.5)
```
```
low=q1-1.5*iqr
low
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/9f5a1285-eabf-47f4-824f-586b3b92cc2c)

```
high=q3+1.5*iqr
high
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/85756c0d-0cf4-4ade-9afb-36ad96fa9808)

```
aq=af[((af>=low)&(af<=high))]
aq.dropna()
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/9eba62c6-6d4f-49d3-97bd-a31294cedf31)

```
sns.boxplot(data=af)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/85860220-bb95-4868-8e46-d01a4814c790)

```
af=af[((af>=low)&(af<=high))]
af.dropna()
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/5f0a5b0f-5985-4742-94fb-ca4bb90e99c6)

```
sns.boxplot(data=af)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/cb24bb39-505a-490a-a28c-3cd8c8d9797d)

```
sns.scatterplot(data=af)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/403c3f54-6e26-4fc4-8b58-7975d2dd28b4)

```
import pandas as pd
import numpy as np
import seaborn as sns
import pandas as pd
from scipy import stats
```
```
data = {'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/ce22bb18-a199-450c-9b02-1fda265f23b7)

```
sns.boxplot(data=df)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/7877ae08-4e81-4fe6-9546-831ba6860ee0)

```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/7f56bdb9-d8e1-41df-8659-3f3f43c6372a)

```
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,69,202,72,75,78,81,84,232,87,90,93,96,99,258]
df=pd.DataFrame(data)
```
```
out=[]
def d_o(val):
  ts=3
  m=np.mean(val)
  sd=np.std(val)
  for i in val:
    z=(i-m)/sd
    if np.abs(z)>ts:
      out.append(i)
  return out
```
```
op=d_o(val)
op
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
```
```
id=pd.read_csv("iris.csv")
id
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/4bbf41a2-5d5c-42b3-8b10-1fbeb139f5e9)

```
sns.boxplot(x='sepal_width',data=id)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/f3516d7c-033b-44a2-b259-a52305fba325)

```
c1=id.sepal_width.quantile(0.25)
c3=id.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/16750451-ccd4-40ac-8548-f248e23e69d5)

```
rid=id[((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/53ecb7b7-60d9-4eea-836a-c75e6f65ab9c)

```
delid=id[~((id.sepal_width<(c1-1.5*iq))|(id.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/81748533-4712-4089-aa57-5d4ffaadeb45)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/Priya-Loganathan/ODD2023---Datascience---Ex-02/assets/121166075/827de53b-8085-41c4-ae71-55b9ee5ef893)

# RESULT:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.
