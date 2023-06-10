# Ex02-Outlier

# AIM
 To detect and remove the outliers in the given data set and save the final data.
 
# EXPLANATION
 Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM
## STEP 1
Import the required packages(pandas,numpy,scipy)
## STEP 2
Read the given csv file
## STEP 3
Convert the file into a dataframe and get information of the data.
## STEP 4
Remove the non numerical data columns using drop() method.
## STEP 5
Detect the outliers in the data set using z scores method.
## STEP 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
## STEP 7
Check if the outliers are removed from data set using graphical methods.
## STEP 8
Save the final data set into the file
    
# CODE
# (1). Remove outliers using IQ.

import pandas as pd

df = pd.read_csv("/content/bhp.csv")

q1 = df['price_per_sqft'].quantile(0.25)

q3 = df['price_per_sqft'].quantile(0.75)

IQR = q3-q1

df_new=df['price_per_sqft'][((df['price_per_sqft']>=q1-1.5IQR)&(df['price_per_sqft']<=q3+1.5IQR))]


![image](https://github.com/Rajasree-321/Ex02-Outlier/assets/96918911/07beeae1-b1ad-4758-910d-1fac86a17b9f)

# (2) After removing outliers in step 1, you get a new data frame.

import pandas as pd

df = pd.read_csv("/content/bhp.csv")

q1 = df['price_per_sqft'].quantile(0.25)

q3 = df['price_per_sqft'].quantile(0.75)

IQR = q3-q1

df_new=df['price_per_sqft'][((df['price_per_sqft']>=q1-1.5IQR)&(df['price_per_sqft']<=q3+1.5IQR))]

print(df['price_per_sqft'])

# (3) use z score of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

import scipy.stats as stats

df['price_per_sqft']=stats.zscore(df['price_per_sqft'])

print(df['price_per_sqft'])

![image](https://github.com/Rajasree-321/Ex02-Outlier/assets/96918911/a6b68b56-3096-4dd0-8173-41127f6fc2cc)

# (4) for the data set height_weight.csv find the following
## (i) Using IQR detect weight outliers and print them.
import pandas as pd

df = pd.read_csv("/content/height_weight.csv")

q1 = df['weight'].quantile(0.25)

q3 = df['weight'].quantile(0.75)

IQR = q3-q1

df_new=df['weight'][((df['weight']>=q1-1.5IQR)&(df['weight']<=q3+1.5IQR))]

print(df['weight'])

![image](https://github.com/Rajasree-321/Ex02-Outlier/assets/96918911/e48dea83-0369-4af5-8574-4015cfcdf79b)

## ii)Using IQR, detect height outliers and print them.
import pandas as pd

df = pd.read_csv("/content/height_weight.csv")

q1 = df['height'].quantile(0.25)

q3 = df['height'].quantile(0.75)

IQR = q3-q1

df_new=df['height'][((df['height']>=q1-1.5IQR)&(df['height']<=q3+1.5IQR))]

print(df['height'])

![image](https://github.com/Rajasree-321/Ex02-Outlier/assets/96918911/626327d1-b6fb-4b69-a8a8-4856467d2521)


# RESULT:
Thus, the given data is read, outliers are detected and removed it and then is saved into file
