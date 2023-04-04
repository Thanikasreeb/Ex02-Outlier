# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
## Aim:
TO detect and remove the outliers in the given data set and save the final data.
     
### ALGORITHM :

### Step 1:

Import the required packages(pandas,numpy,scipy)

### step 2 :
Read the given csv file

### Step3:
Convert the file into a dataframe and get information of the data.

### Step 4:
Remove the non numerical data columns using drop() method.

### Step 5:
Detect the outliers in the data set using z scores method.

### Step 6:
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)

### Step 7:
Check if the outliersare removed from data set using graphical methods.

### Step 8:
Save the final data set into the file.

### code :
### bhp.csv
```
import numpy as np
import pandas as pd
from scipy import stats
a = pd.read_csv('bhp.csv')
df = pd.DataFrame(a['price_per_sqft'])
median = df.quantile(0.5)
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
low = Q1 - 1.5 * IQR
high = Q3 + 1.5 * IQR
df1 = df[((df >= Q1 - 1.5 * IQR) & (df <= Q3 + 1.5 * IQR))]
print(df1)
z = np.abs(stats.zscore(df))
df1 = df1[(z < 3)]
print(df1)
```
### height_weight.csv
```
import numpy as np
import pandas as pd
from scipy import stats
a = pd.read_csv('height_weight.csv')
df = pd.DataFrame(a['height'])
print(df)
median = df.quantile(0.5)
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
low = Q1 - 1.5 * IQR
high = Q3 + 1.5 * IQR
df1 = df[((df >= Q1 - 1.5 * IQR) & (df <= Q3 + 1.5 * IQR))]
print(df1)
df2 = pd.DataFrame(a['weight'])
print(df2)
q1 = df2.quantile(0.25)
q3 = df2.quantile(0.75)
IQR = q3 - q1
df2_new = df2[((df2 >= q1 - 1.5 * IQR) & (df2 <= q3 + 1.5 * IQR))]
print(df2_new)
```

### OUTPUT :
## bhp.csv
![image](https://user-images.githubusercontent.com/119557910/229702624-309add0a-95f2-44b9-9f25-d94b6843268b.png)
![image](https://user-images.githubusercontent.com/119557910/229702667-ea90c610-e93d-4653-9955-89a88489b0ca.png)
![image](https://user-images.githubusercontent.com/119557910/229702706-589837d4-50d0-4321-b933-0d959c01fad7.png)

### height_weight.csv
![image](https://user-images.githubusercontent.com/119557910/229702786-a22bd745-0cd4-41be-8223-7aaced74f112.png)
![image](https://user-images.githubusercontent.com/119557910/229702806-22a52aed-4e44-4f55-a78c-b0ec2b656ac7.png)
![image](https://user-images.githubusercontent.com/119557910/229702828-c174b261-01e6-4b97-8511-767dd7ef0001.png)

### RESULT :
Thus the required output is displayed.



