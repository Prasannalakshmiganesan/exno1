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
df = pd.read_csv("heights.csv")
df.head()
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/505fb4f2-a4e1-4305-bc94-66f0ec7286a0)

```
sns.boxplot(data=df)
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/e60d8a26-2e8f-4f70-b76b-957461597c00)

```
sns.scatterplot(data=df)
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/40f75695-6059-4663-8668-60fcac94727d)

```
max=df['height'].quantile(0.75)
min=df['height'].quantile(0.25)
iqr=max-min
max
min
iqr
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/d94d870a-4f29-4d14-88a4-29a3bfa4921d)

```
low = min-1.5*iqr
low
high = max+1.5*iqr
high
qm = df[((df['height']>=low)&(df['height']<=high))]
qm
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/3003a8d0-4aca-4373-99f9-e3ba2d859f69)

### Z SCORE
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/Prasannalakshmiganesan/exno1/assets/118610231/1ac9750a-993d-43c9-9e2e-a79efe547cf5)


# Result

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
