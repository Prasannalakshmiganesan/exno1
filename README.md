# Exno:1  Data Cleaning Process

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

# Coding and Output
```
NAME: VARSHINI S A
REGNO: 212222100059
```
### DATA CLEANING
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/9b7277b9-d81d-429a-a4ae-8857adc5bfde)


```
df.tail(5)
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/6013156a-abaa-462a-89b7-11f1340c4321)

```
df.info()
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/255de48d-3de0-488a-9e7e-8fd396d52097)

```
df.describe()
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/2a711358-2dec-4e57-ad25-d85a4c7dfb90)

```
df.isnull()
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/7844d1be-4a82-483d-a670-400467d2c971)

```
df.isnotnull()
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/b43b7b1c-28aa-48e1-993d-f172e015ac72)

```
df.dropna(axis=1)
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/c9fb651e-9556-4c13-a724-006c01bebdc7)

```
df.sropna(axis=0)
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/a3b7f55e-44b9-43d1-9b3e-5d242b3a5528)

```
dfs=df[df['num_episodes']>20]
dfs
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/da9df13b-a077-461d-9f38-6ac288cdc138)

```
dfs = df[df['show_name'].str.startswith(('A','C'))&(df['num_episodes']>20)]
dfs
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/370c97a9-28e9-43b4-8eda-1f3f8c5a8ec6)

```
df.iloc[:4]
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/9c2f288f-6d63-4d93-87f7-14bbedaf2750)

### IQR

```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```

![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/463a388d-f7fc-49b3-931e-6baeabc925a9)

```
ir.describe()
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/59541e03-224b-4ade-b2d6-12788f594151)

```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/225999cc-b26e-4c1a-8dc2-9d396429fb14)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/73e38aca-82dc-412c-a190-adff11aabcc5)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/0f155fa8-e20e-4757-9353-4050a7d3cc93)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/7aa2c415-a407-458d-859c-14bc5e62763e)
```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/2d6cdad6-d734-45a7-8129-4d69835f0449)

### Z SCORE
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/2a76d30f-036a-49f5-9764-99dd2e5410a1)

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
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/abd34004-f936-4ac1-8d0f-f7390f459771)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/fb9c6f0e-ff7c-4c72-8119-3d8b75b64673)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/fba2ca9d-90b1-4ed1-a6fc-d1a1d5682a68)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/48630c8d-186d-4e4c-b8fa-518d63c0f3f1)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/VARSHINI22009118/exno1/assets/119401150/7064433b-2251-44c4-8dae-748ea09c4b14)


# Result

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
