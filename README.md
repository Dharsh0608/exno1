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
   ~~~
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
~~~

<img width="1071" height="892" alt="image" src="https://github.com/user-attachments/assets/30fae8f0-d7ba-4087-b1f6-bddc5475a11d" />

~~~
df.head()
~~~

<img width="1038" height="253" alt="image" src="https://github.com/user-attachments/assets/ac1889fb-0a5b-4da0-be7b-1609bdb97521" />

~~~
df.tail()
~~~

<img width="1058" height="248" alt="image" src="https://github.com/user-attachments/assets/267e717f-3f75-4be4-8d5f-bdbe9975765f" />


~~~
df.isnull()
~~~


<img width="875" height="868" alt="image" src="https://github.com/user-attachments/assets/d3a16714-3e12-4164-b320-189028bc4618" />

~~~
df.notnull()
~~~


<img width="1056" height="868" alt="image" src="https://github.com/user-attachments/assets/02197e0d-ea25-4a42-865c-000e0839b07d" />

~~~
df.isnull().sum()
~~~

<img width="322" height="568" alt="image" src="https://github.com/user-attachments/assets/53200212-e7e0-480d-a591-dc9ea0a1cb2a" />

~~~
df.isnull().any()
~~~


<img width="323" height="573" alt="image" src="https://github.com/user-attachments/assets/03ab2d1a-7b0a-4aba-bf9c-ec21034aeeb5" />

~~~
df.dropna(axis=0)
~~~


<img width="1099" height="559" alt="image" src="https://github.com/user-attachments/assets/c1ce2fe7-f0d1-46db-8b1d-d5c384aff914" />

~~~
df.dropna(axis=1)
~~~


<img width="461" height="870" alt="image" src="https://github.com/user-attachments/assets/a1e09922-5dff-461f-bf53-b47655f1c84e" />

~~~
df.fillna({'GENDER' : 'MALE' ,'ADDRESS': 'KANCHIPURAM'})
~~~


<img width="1101" height="867" alt="image" src="https://github.com/user-attachments/assets/7c51e123-04cc-4599-abe3-473f6f2acd4d" />

~~~
ir=pd.read_csv("/content/iris.csv")
ir
~~~


<img width="778" height="525" alt="image" src="https://github.com/user-attachments/assets/1558f09f-d9aa-483d-8542-1bc5c3c00baf" />

~~~
import seaborn as sns
sns.boxplot (x='sepal_width',data=ir)
~~~


<img width="914" height="582" alt="image" src="https://github.com/user-attachments/assets/11a4734d-cb85-4993-926d-458a48702809" />

~~~
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
IQR=Q3-Q1
print(IQR)
~~~


<img width="61" height="48" alt="image" src="https://github.com/user-attachments/assets/87e82664-fbf3-448e-b318-6bddf0fe8bfc" />

~~~
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
~~~


<img width="286" height="264" alt="image" src="https://github.com/user-attachments/assets/7da1a5a3-3458-4747-8a73-9b53ee4ae3b1" />

~~~
ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
~~~


<img width="403" height="562" alt="image" src="https://github.com/user-attachments/assets/c5b2fb10-05b0-4b2d-9c77-acb1bb07eade" />

~~~
sns.boxplot(x='sepal_width',data=ran)
~~~


<img width="805" height="583" alt="image" src="https://github.com/user-attachments/assets/fa2abd4b-fb61-4c0a-8efe-621ce7bee553" />

~~~
import numpy as np
import scipy.stats as stats
~~~

~~~
z=np.abs(stats.zscore(ir['petal_length']))
z
~~~


<img width="756" height="672" alt="image" src="https://github.com/user-attachments/assets/8e94091b-bc6f-4099-8227-ec4952b20e49" />

~~~
ir1=ir[z<3]
ir1
~~~


<img width="873" height="556" alt="image" src="https://github.com/user-attachments/assets/9016da35-11c7-44d8-b97b-053c8a84d6e1" />





# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
