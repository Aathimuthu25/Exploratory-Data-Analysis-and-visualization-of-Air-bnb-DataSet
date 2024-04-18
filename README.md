# <p align="left"> *Exploratory-Data-Analysis-Visualisation-on-Airbnb-Dataset* </p>

# <p align="center"> ![Airbnb-Logo](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/1d1c46db-be69-4162-af33-015053a162ab)

 
 </p>

## Overview

The Exploratory Data Analysis (EDA) and Visualization on Airbnb Dataset is a comprehensive examination of Airbnb data aimed at extracting meaningful insights and patterns. Airbnb is a popular platform for short-term lodging rentals, offering a vast array of properties worldwide. This dataset typically contains various attributes such as property type, location, price, availability, and host information.

**Tools:-** Excel,Python

[Datasets Used](Airbnb_Excel.xls)

[Python Script (Code)](Python_Project.ipynb)

## Requirements

- Python 3

- Libraries: NumPy, pandas, Sklearn, etc.

- Jupyter Lab


## Exploratory-Data-Analysis

```py
#To show the Attribotes and it's Datatype
a.info()
```
Result : 
# <p align="center">![Img_1](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/a5fb6db9-8d85-4060-b766-bbcd5197525e)

</p>

```py
#To show the Statistical Summary of a Dataset
a.describe()
```
Result : 
# <p align="center">![Img_2](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/7719339f-1dc3-4cb1-873d-741d37a3e137)

</p>

```py
#To check for Duplicates
b = a.duplicated().sum()
print("The total number of Duplicate values : ",b)
```
Result : 
# <p align="center">![Img_3](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/8d6a55d7-4089-4213-944f-71220b8d766c)

</p>

```py
#To remove the Duplicate Values 
c = a.drop_duplicates(inplace = True)
#To verify if the Duplicate values are Removed
a.duplicated().sum()
```
Result : 
# <p align="center">![img_4](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/17a70299-cfa4-4a83-8cdb-27f4161a4cd2)

</p>

```py
#To remove the ir-relevant Attributes column
e = a.drop(['license'],axis=1,inplace=True)
f = a.drop(['house_rules'],axis=1,inplace=True)
#To verify if the columns are removed 
a.info()
```
Result : 
# <p align="center">![Img_5](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/e18ea096-b8c4-4d75-8428-12ae51ae8cad)

</p>

```py
#To check for Null values
d = a.isnull().sum()
print("The total number of Null values : \n",d)
```
Result : 
# <p align="center">![Img_6](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/b68425ff-7a66-4772-9bdd-04be600c8021)

</p>

```py
#To Replace the Null values
a['NAME'].fillna(a['NAME'].mode().iloc[0],inplace=True)
a['host_identity_verified'].fillna(a['host_identity_verified'].mode().iloc[0],inplace=True)
a['host name'].fillna(a['host name'].mode().iloc[0],inplace=True)
a['neighbourhood group'].fillna(a['neighbourhood group'].mode().iloc[0],inplace=True)
a['neighbourhood'].fillna(a['neighbourhood'].mode().iloc[0],inplace=True)
a['country'].fillna(a['country'].mode().iloc[0],inplace=True)
a['country code'].fillna(a['country code'].mode().iloc[0],inplace=True)
a['instant_bookable'].fillna(a['instant_bookable'].mode().iloc[0],inplace=True)
a['cancellation_policy'].fillna(a['cancellation_policy'].mode().iloc[0],inplace=True)
a['Construction year'].fillna(a['Construction year'].mode().iloc[0],inplace=True)
a['minimum nights'].fillna(a['minimum nights'].mode().iloc[0],inplace=True)
```

```py
#To rename the column  
a['service fee'] = a['service fee'].str.replace('$','')
a['price'] = a['price'].str.replace('$','')
a = a.rename(columns={'price':'price in dollars','service fee':'service fee in dollars'})
```

```py
#To change the datatype
a['price in dollars'] = pd.to_numeric(a['price in dollars'], errors='coerce')
a['service fee in dollars'] = pd.to_numeric(a['service fee in dollars'], errors='coerce')
```

```py
a['price in dollars'].fillna(a['price in dollars'].mean(),inplace =True)
a['service fee in dollars'].fillna(a['service fee in dollars'].mean(),inplace =True)
a['number of reviews'].fillna(a['number of reviews'].mode().iloc[0],inplace=True)
a['last review'].fillna(a['last review'].mode().iloc[0],inplace=True)
a['reviews per month'].fillna(a['reviews per month'].mean(),inplace=True)
a['review rate number'].fillna(a['review rate number'].mode().iloc[0],inplace=True)
a['calculated host listings count'].fillna(a['calculated host listings count'].mode().iloc[0],inplace=True)
a['availability 365'].fillna(a['availability 365'].mode().iloc[0],inplace=True)
```

```py
#To verify for Null values
a.isnull().sum()
```
Result : 
# <p align="center">![Img_7](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/0f89042d-ce7f-423f-8cc8-b2a3266f5b84)

</p>


```py
#To List the count of various room types available in the Dataset
g = a.groupby(['room type']).size()
g
```
Result : 
# <p align="center">![Img_8](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/d7977305-3755-4a30-8610-4c91b5d54711)

</p>


```py
#Which room type has strict cancellation policy
h = a[a['cancellation_policy'] == 'strict']
i = h.groupby('room type').size()
i.sort_values().tail(1)c
```
Result : 
# <p align="center">![Img_9](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/ae9e330f-6ba7-4f27-9cf4-283e4e8ee54b)

</p>


```py
#To List the average price per neighborhood group
j = a.groupby('neighbourhood group')['price in dollars'].mean()
j
```
Result : 
# <p align="center">![Img_10](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/2b556fca-0657-4167-a1ad-731c338b27ad)

</p>


```py
#Most expensive neighborhood to rent from
k = a.groupby('neighbourhood group')['price in dollars'].mean()
k
k.sort_values().tail(1)
```
Result : 
# <p align="center">![Img_11](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/6c721554-1f0d-45f5-8da6-b860d4a70480)

</p>

## DATA VISUALIZATION

```py
#List the count of various room types avaliable with Airnb
l = a.groupby('room type').size()
m = ['Entire home/apt','Hotel room','Private room','Shared room']
plt.pie(l,labels = m,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">![Img_12](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/934a6293-d8ea-4d22-8b94-722510ddb0c2)


</p>


```py
#Which room type adheres to more strict cancellation policy
n = a[a['cancellation_policy'] == 'strict']
o = h.groupby('room type').size()
p = ['Entire home/apt','Hotel room','Private room','Shared room']
plt.pie(o,labels = p,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">![Img_13](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/a8994999-edb8-446d-b174-56cb285a35bd)

</p>


```py
#List the prices by neighborhood group and also mention which is the most expensive neighborhood group for rentals
q = a.groupby('neighbourhood group')['price in dollars'].mean()
r = ['Bronx','Brooklyn','Manhattan','Queens','Staten Island','brookln','manhatan']
plt.pie(q,labels=r,autopct='%1.1f%%')
plt.show()
most_expensive_neighborhood = q.idxmax()
most_expensive_price = q.max()
print("The Most Expensive Neighborhood group for rentals : ", most_expensive_neighborhood , most_expensive_price)
```
Result : 
# <p align="center">![Img_14](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/c7ab1933-d49a-431d-863f-5af98ae25ccd)

</p>


```py
#List the top 10 neighborhoods in the increasing order of their price with the help of a horizontal bar graph. Which is the cheapest neighborhood.
s = a.groupby('neighbourhood')['price in dollars'].mean().sort_values().head(10)
s.plot(kind='barh',color ='Red')
plt.show()
print("The cheapest neighborhood is :", s.sort_values().head(1))
```
Result : 
# <p align="center">![Img_15](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/a948f3bb-66e6-4958-b510-b5c7ec14eeb0)

</p>


```py
#List the neighborhoods which offer short term rentals within 10 days.Illustrate with a bar graph
f = a.groupby('neighbourhood')['minimum nights'].mean().sort_values()
g = f.head(196)
plt.figure(figsize=(30, 6))
g.plot(kind='bar',color ='Red')
plt.title('neighborhoods which offer short term rentals within 10 days')
plt.xlabel('Neighbourhood')
plt.ylabel('minimum nights')
plt.show()
```
Result : 
# <p align="center">![Img_16](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/17eb48bd-1a7d-4c5d-a51c-9e3e40b3f15a)

</p>


```py
#List the prices with respect to room type using a bar graph and also state your inferences.
d = a.groupby('room type')['price in dollars'].mean()
plt.figure(figsize=(6, 4))
d.plot(kind='bar',color ='Red')
plt.title('prices with respect to room type')
plt.xlabel('room type')
plt.ylabel('prices')
plt.show()
```
Result : 
# <p align="center">![Img_17](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/7d2b5a75-f7e4-4edd-a3f0-3bbb7f1c6cde)

</p>


```py
#Create a pie chart that shows distribution of booked days for each neighborhood group 
x = a.groupby('neighbourhood group')['availability 365'].size()
y = ['Brooklyn','Bronx','Manhattan','Staten Island','Queens','brookln','manhatan']
plt.pie(x,labels = y,autopct='%1.1f%%')
plt.show()
```
Result : 
# <p align="center">![Img_18](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/9db08aea-a2f8-4cb7-bcc4-ac6e1880ca03)

</p>


```py
#Which neighborhood has the highest booking percentage
a.groupby('neighbourhood')['availability 365'].mean().sort_values().head(1)
```
Result : 
# <p align="center">![Img_19](https://github.com/Aathimuthu25/Exploratory-Data-Analysis-and-visualization-of-Air-bnb-DataSet/assets/158067286/dd95489f-6994-4ef5-9e26-e88b68f17c2a)

</p>
