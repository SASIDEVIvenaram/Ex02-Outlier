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
## STEP 1
Read the given Data.

## STEP 2
Get the information about the data.

## STEP 3
Detect the Outliers using IQR method and Z score.

## STEP 4
Remove the outliers.

## STEP 5
Plot the datas using Box Plot.

# PROGRAM:
DEVELOPED BY: SASIDEVI.V, REGISTER NUMBER: 212222230136
```
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

#removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


#removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

#Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


#Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```

# OUTPUT:
# bhp.csv
## IQR METHOD
## df.head()
![E21](https://user-images.githubusercontent.com/118707332/227220952-9b6f2470-ca66-4644-9109-55311029af01.png)

## df.describe()
![E22](https://user-images.githubusercontent.com/118707332/227221413-88d34115-6622-4456-a49f-3d4fc98db205.png)

## df.info()
![E23](https://user-images.githubusercontent.com/118707332/227221448-d44be9ab-4e86-4ffc-a7fe-29966b33304b.png)

## df.shape
![E24](https://user-images.githubusercontent.com/118707332/227221490-8b7ceae5-f8bc-458d-b30d-6fe22637e654.png)
## BOXPLOT BEFORE REMOVING OUTLIERS 

![E25](https://user-images.githubusercontent.com/118707332/227222328-0291041c-2b4f-4803-8b4b-c77d2d8dbfc3.png)

## NEWDATA USING IQR
![E26](https://user-images.githubusercontent.com/118707332/227222646-588d171b-3581-40e3-9ea8-4411c3c89485.png)
## OUTLIERS
![E27](https://user-images.githubusercontent.com/118707332/227222741-787e4ed9-c7fd-49de-9404-647b59e34748.png)
## newdata.shape
![E29](https://user-images.githubusercontent.com/118707332/227222905-a77277b1-76cc-4c64-bd0d-de2c38181176.png)
## BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![E210](https://user-images.githubusercontent.com/118707332/227223048-3c81578f-a0ab-480d-a101-5e15df32eb93.png)

## Zscore of 3
## NEWDATA USING Zscore
![E211](https://user-images.githubusercontent.com/118707332/227224343-fba65d3d-2fa6-4358-80e3-229c80b98d38.png)
## OUTLIERS
![E212](https://user-images.githubusercontent.com/118707332/227224448-22c40795-e092-4cb9-96da-825ff0a96ed9.png)
## newdata2.shape
![E213](https://user-images.githubusercontent.com/118707332/227224705-9245515f-014c-4f85-b1a0-8bf083e56c81.png)
## BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![E214](https://user-images.githubusercontent.com/118707332/227225303-17917475-4f87-4a19-af44-1fe93be40df7.png)

# height_weight.csv
## dataset.shape
![E215](https://user-images.githubusercontent.com/118707332/227226689-96c5a248-335b-4d04-897f-bbe7d5c3af40.png)

## dataset.describe()
![E216](https://user-images.githubusercontent.com/118707332/227226721-4e324a73-84bb-43e6-9847-012d1aaa11f0.png)

## dataset.info()
![E217](https://user-images.githubusercontent.com/118707332/227226836-927055e2-063d-417b-978f-7243fc94deb3.png)

## BOXPLOT BEFORE REMOVING OUTLIERS 
![E218](https://user-images.githubusercontent.com/118707332/227227287-f90f1f2b-c46c-4975-b466-b4fb6ff2c966.png)

## HEIGHT OUTLIERS
![E219](https://user-images.githubusercontent.com/118707332/227227564-a6523763-cf23-4a23-bf19-8c5f1da16fbf.png)

## DATASET AFTER REMOVING HEIGHT OUTLIERS
![E220](https://user-images.githubusercontent.com/118707332/227227690-65153c1d-924d-44fa-be16-4fc8e86218d8.png)

## BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![E221](https://user-images.githubusercontent.com/118707332/227227887-807c3599-5c8e-41b6-9726-38c66af6e074.png)

## WEIGHT OUTLIERS
![E222](https://user-images.githubusercontent.com/118707332/227228465-add663f8-3f35-4601-9d72-466dc6ec9bcb.png)

## DATASET AFTER REMOVING WEIGHT OUTLIERS
![E223](https://user-images.githubusercontent.com/118707332/227228528-99c7b842-7ede-48c1-9dd9-fd18705c2fcc.png)

## BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![E224](https://user-images.githubusercontent.com/118707332/227228549-6a3c2a93-2f44-4e32-af17-46a12a188d08.png)

# RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.




