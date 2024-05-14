## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label..
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
```
    import pandas as pd
    df=pd.read_csv("/content/Encoding Data (1).csv")
    df
```
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/d9d483ec-fb5e-4c8b-8083-2b1e75baa268)
 ````
      from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
      pm=['Hot','Warm','Cold']
      e1=OrdinalEncoder(categories=[pm])
      e1.fit_transform(df[["ord_2"]])
 ````
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/d780259c-b1d3-4749-b427-1c639d006915)
  ```
      df['bo2']=e1.fit_transform(df[["ord_2"]])
```
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/3667ae43-1ad0-408d-9a72-0b0d3c178e69)
  ```
       le=LabelEncoder()
       dfc=df.copy()
       dfc['ord_2']=le.fit_transform(dfc['ord_2'])
````
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/12ed427f-2409-4821-aad3-208d24bf9bb9)
```
      from sklearn.preprocessing import OneHotEncoder
       ohe=OneHotEncoder(sparse=False)
       df2=df.copy()
       enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
````
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/e66ab6a0-3ed8-4127-b067-c28cfb7637cb)
```
        df2=pd.concat([df2,enc],axis=1)
````
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/60d66a25-43b3-4390-8751-c2c50d1ab30a)
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/fe209085-f7ad-41ef-b045-38e558ff3ea1)
```
         from category_encoders import BinaryEncoder
         df=pd.read_csv("/content/data.csv")
         be=BinaryEncoder()
         nd=be.fit_transform(df['Ord_2'])
         dfb=pd.concat([df,nd],axis=1)
         dfb1=df.copy()
```
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/feda282d-eff8-457e-9b7f-7602a5c292f8)
```
         from category_encoders import TargetEncoder
         te=TargetEncoder()
         cc=df.copy()
         new=te.fit_transform(X=cc["City"],y=cc["Target"])
         cc=pd.concat([cc,new],axis=1)
```
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/deb2f8f3-70af-4257-8ec3-517bd5ff4710)

         
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/41850545-4de3-4917-ac68-9b6a67d0d46e)
          
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/7c7f9b9f-5aaa-490f-bddf-2c000721f67c)
         
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/6b6d487b-f1b4-44f3-8838-efb1246ae985)
          
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/466d71d0-466f-4511-a687-7820692e46e2)
 ```         
df["Higly Positive Skew_borcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
 `````   
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/8aea5279-420a-4b33-961b-f08b7a56f9f1)
```
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
```
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/6cadfe89-5113-48ca-a8b9-fc9dca4bde53)
````
         from sklearn.preprocessing import QuantileTransformer
         qt=QuantileTransformer(output_distribution='normal')
````
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/73d45744-ca36-4d6f-8222-cb758dd56f44)
         
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/3a8ed884-a95d-4d50-9b46-aad00d46f94e)
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/cc2671a5-cf40-4a93-9003-721776154737)
![image](https://github.com/Harshinisrini1910/EXNO-3-DS/assets/161415847/95ce913d-a3b5-42d1-9968-77ba93f7e230)

![image](https://github.com/vinodhini-17/EXNO-3-DS/assets/145742741/c3810c1e-034d-47ce-883c-c9c7ecdee05a)
![image](https://github.com/vinodhini-17/EXNO-3-DS/assets/145742741/36f959b2-3852-4e7e-b227-96799d81806b)
![image](https://github.com/vinodhini-17/EXNO-3-DS/assets/145742741/12e65b68-deb5-4a9b-b53b-521170744c5a)


# RESULT:
    
Thus To read the given data and perform Feature Encoding and Transformation process and save the data to a file has successfully executed 
       
