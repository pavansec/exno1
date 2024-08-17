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

# Coding and Output
```

 import pandas as pd
 sam=pd.read_csv("SAMPLEIDS.csv")

```
![image](https://github.com/user-attachments/assets/fd918a72-771f-4b0c-964b-b0864cf59a59)
```
 sam.head(6)
```
![image](https://github.com/user-attachments/assets/0a78b725-d282-44cb-a1f5-7cbbb560582f)
```
 sam.isnull()
```
![image](https://github.com/user-attachments/assets/4a870bbd-d70c-466e-a303-a0b6e93438f7)
```
 sam.fillna(0)
```
![image](https://github.com/user-attachments/assets/8fb6b88c-f7e2-4a6a-8334-0510138272a6)
```
  sam.describe()
```
![image](https://github.com/user-attachments/assets/7fcb1756-44d4-4f24-893d-c8e833a6e879)
```
 import pandas as pd
 import seaborn as sns
 import matplotlib.pyplot as plt
 import numpy as np
 iris=pd.read_csv("iris.csv")
 iris
```
![image](https://github.com/user-attachments/assets/252c8bf8-3c09-46e0-8a70-6edf6619f91c)
```
 iris.describe()
```
![image](https://github.com/user-attachments/assets/68b83847-3060-4b05-bfbe-82405eff310c)
```
 sns.boxplot(x='sepal_width',data=iris)
```
![image](https://github.com/user-attachments/assets/dc115928-9627-4da7-8a3b-7acbb7cbb1be)
```
 c1=iris.sepal_width.quantile(0.25)
 c3=iris.sepal_width.quantile(0.75)
 iq=c3-c1
 print(c3)

```
![image](https://github.com/user-attachments/assets/7a1ef457-b533-413c-9dea-086e8f2a9757)
```
 delid=iris[~((iris.sepal_width<(c1-1.5*iq))|(iris.sepal_width>(c3+1.5*iq)))]
 delid
```
![image](https://github.com/user-attachments/assets/052716b9-3d99-4613-8855-9be4790b14ce)
```
 import seaborn as sns
 sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/user-attachments/assets/074354ed-50c1-4375-b9f4-c41c212b4a0b)
```
 Z-SCORE
 import matplotlib.pyplot as plt
 import pandas as pd
 import numpy as np
 import scipy.stats as stats
 dataset=pd.read_csv("heights.csv")
 dataset

```
![image](https://github.com/user-attachments/assets/ee4363e4-325c-4b47-8051-d654941e8da8)
```
 df = pd.read_csv("heights.csv")
 q1 = df['height'].quantile(0.25)
 q2 = df['height'].quantile(0.5)
 q3 = df['height'].quantile(0.75)

 iqr = q3-q1
 iqr
```
![image](https://github.com/user-attachments/assets/ba7b3cb8-98c2-44c5-ae28-ca2217f8ae25)
```
 low = q1- 1.5*iqr
 low
```
![image](https://github.com/user-attachments/assets/19d064b8-aca5-4098-a595-1cf31eb34cfa)
```
 high = q3 + 1.5*iqr
 high
 df1 = df[((df['height'] >=low)& (df['height'] <=high))]
 df1

```
![image](https://github.com/user-attachments/assets/a5b1bfa9-7e00-484b-96c2-01df4b21b305)
```
 z = np.abs(stats.zscore(df['height']))
 z
```
![image](https://github.com/user-attachments/assets/791f2abb-0528-49af-9626-d4427bc93d5b)
```
 df1 = df[z<3]
 df
```
![image](https://github.com/user-attachments/assets/b82e3946-1ee5-450a-9f9a-e5445e894073)


# Result
          <<include your Result here>

![image](https://github.com/user-attachments/assets/33213eac-43f9-4fdc-b059-f42056bc25de)

![image](https://github.com/user-attachments/assets/071bd377-8dce-48ed-a874-b52d9225345c)
