```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
reg = pd.read_csv(r"C:\Users\Windows 10 Pro\Downloads\Housing.csv")
```


```python
reg.head
```




    <bound method NDFrame.head of         price  area  bedrooms  bathrooms  stories mainroad guestroom basement  \
    0    13300000  7420         4          2        3      yes        no       no   
    1    12250000  8960         4          4        4      yes        no       no   
    2    12250000  9960         3          2        2      yes        no      yes   
    3    12215000  7500         4          2        2      yes        no      yes   
    4    11410000  7420         4          1        2      yes       yes      yes   
    ..        ...   ...       ...        ...      ...      ...       ...      ...   
    540   1820000  3000         2          1        1      yes        no      yes   
    541   1767150  2400         3          1        1       no        no       no   
    542   1750000  3620         2          1        1      yes        no       no   
    543   1750000  2910         3          1        1       no        no       no   
    544   1750000  3850         3          1        2      yes        no       no   
    
        hotwaterheating airconditioning  parking prefarea furnishingstatus  
    0                no             yes        2      yes        furnished  
    1                no             yes        3       no        furnished  
    2                no              no        2      yes   semi-furnished  
    3                no             yes        3      yes        furnished  
    4                no             yes        2       no        furnished  
    ..              ...             ...      ...      ...              ...  
    540              no              no        2       no      unfurnished  
    541              no              no        0       no   semi-furnished  
    542              no              no        0       no      unfurnished  
    543              no              no        0       no        furnished  
    544              no              no        0       no      unfurnished  
    
    [545 rows x 13 columns]>



                                         CHECKING THE DUPLICATE VALUES


```python
reg.duplicated()
```




    0      False
    1      False
    2      False
    3      False
    4      False
           ...  
    540    False
    541    False
    542    False
    543    False
    544    False
    Length: 545, dtype: bool




```python
reg.duplicated
```




    <bound method DataFrame.duplicated of         price  area  bedrooms  bathrooms  stories mainroad guestroom basement  \
    0    13300000  7420         4          2        3      yes        no       no   
    1    12250000  8960         4          4        4      yes        no       no   
    2    12250000  9960         3          2        2      yes        no      yes   
    3    12215000  7500         4          2        2      yes        no      yes   
    4    11410000  7420         4          1        2      yes       yes      yes   
    ..        ...   ...       ...        ...      ...      ...       ...      ...   
    540   1820000  3000         2          1        1      yes        no      yes   
    541   1767150  2400         3          1        1       no        no       no   
    542   1750000  3620         2          1        1      yes        no       no   
    543   1750000  2910         3          1        1       no        no       no   
    544   1750000  3850         3          1        2      yes        no       no   
    
        hotwaterheating airconditioning  parking prefarea furnishingstatus  
    0                no             yes        2      yes        furnished  
    1                no             yes        3       no        furnished  
    2                no              no        2      yes   semi-furnished  
    3                no             yes        3      yes        furnished  
    4                no             yes        2       no        furnished  
    ..              ...             ...      ...      ...              ...  
    540              no              no        2       no      unfurnished  
    541              no              no        0       no   semi-furnished  
    542              no              no        0       no      unfurnished  
    543              no              no        0       no        furnished  
    544              no              no        0       no      unfurnished  
    
    [545 rows x 13 columns]>




```python
reg.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>price</th>
      <th>area</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>stories</th>
      <th>parking</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>5.450000e+02</td>
      <td>545.000000</td>
      <td>545.000000</td>
      <td>545.000000</td>
      <td>545.000000</td>
      <td>545.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4.766729e+06</td>
      <td>5150.541284</td>
      <td>2.965138</td>
      <td>1.286239</td>
      <td>1.805505</td>
      <td>0.693578</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1.870440e+06</td>
      <td>2170.141023</td>
      <td>0.738064</td>
      <td>0.502470</td>
      <td>0.867492</td>
      <td>0.861586</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.750000e+06</td>
      <td>1650.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.430000e+06</td>
      <td>3600.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>4.340000e+06</td>
      <td>4600.000000</td>
      <td>3.000000</td>
      <td>1.000000</td>
      <td>2.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>5.740000e+06</td>
      <td>6360.000000</td>
      <td>3.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.330000e+07</td>
      <td>16200.000000</td>
      <td>6.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>3.000000</td>
    </tr>
  </tbody>
</table>
</div>



                                        REMOVING THE DUPLICATES


```python
reg.drop_duplicates
```




    <bound method DataFrame.drop_duplicates of         price  area  bedrooms  bathrooms  stories mainroad guestroom basement  \
    0    13300000  7420         4          2        3      yes        no       no   
    1    12250000  8960         4          4        4      yes        no       no   
    2    12250000  9960         3          2        2      yes        no      yes   
    3    12215000  7500         4          2        2      yes        no      yes   
    4    11410000  7420         4          1        2      yes       yes      yes   
    ..        ...   ...       ...        ...      ...      ...       ...      ...   
    540   1820000  3000         2          1        1      yes        no      yes   
    541   1767150  2400         3          1        1       no        no       no   
    542   1750000  3620         2          1        1      yes        no       no   
    543   1750000  2910         3          1        1       no        no       no   
    544   1750000  3850         3          1        2      yes        no       no   
    
        hotwaterheating airconditioning  parking prefarea furnishingstatus  
    0                no             yes        2      yes        furnished  
    1                no             yes        3       no        furnished  
    2                no              no        2      yes   semi-furnished  
    3                no             yes        3      yes        furnished  
    4                no             yes        2       no        furnished  
    ..              ...             ...      ...      ...              ...  
    540              no              no        2       no      unfurnished  
    541              no              no        0       no   semi-furnished  
    542              no              no        0       no      unfurnished  
    543              no              no        0       no        furnished  
    544              no              no        0       no      unfurnished  
    
    [545 rows x 13 columns]>




```python
reg.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>price</th>
      <th>area</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>stories</th>
      <th>mainroad</th>
      <th>guestroom</th>
      <th>basement</th>
      <th>hotwaterheating</th>
      <th>airconditioning</th>
      <th>parking</th>
      <th>prefarea</th>
      <th>furnishingstatus</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13300000</td>
      <td>7420</td>
      <td>4</td>
      <td>2</td>
      <td>3</td>
      <td>yes</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>yes</td>
      <td>2</td>
      <td>yes</td>
      <td>furnished</td>
    </tr>
    <tr>
      <th>1</th>
      <td>12250000</td>
      <td>8960</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>yes</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>yes</td>
      <td>3</td>
      <td>no</td>
      <td>furnished</td>
    </tr>
    <tr>
      <th>2</th>
      <td>12250000</td>
      <td>9960</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
      <td>yes</td>
      <td>no</td>
      <td>yes</td>
      <td>no</td>
      <td>no</td>
      <td>2</td>
      <td>yes</td>
      <td>semi-furnished</td>
    </tr>
    <tr>
      <th>3</th>
      <td>12215000</td>
      <td>7500</td>
      <td>4</td>
      <td>2</td>
      <td>2</td>
      <td>yes</td>
      <td>no</td>
      <td>yes</td>
      <td>no</td>
      <td>yes</td>
      <td>3</td>
      <td>yes</td>
      <td>furnished</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11410000</td>
      <td>7420</td>
      <td>4</td>
      <td>1</td>
      <td>2</td>
      <td>yes</td>
      <td>yes</td>
      <td>yes</td>
      <td>no</td>
      <td>yes</td>
      <td>2</td>
      <td>no</td>
      <td>furnished</td>
    </tr>
  </tbody>
</table>
</div>



                                          CHECKING THE NULL VALUES


```python
reg.isnull
```




    <bound method DataFrame.isnull of         price  area  bedrooms  bathrooms  stories mainroad guestroom basement  \
    0    13300000  7420         4          2        3      yes        no       no   
    1    12250000  8960         4          4        4      yes        no       no   
    2    12250000  9960         3          2        2      yes        no      yes   
    3    12215000  7500         4          2        2      yes        no      yes   
    4    11410000  7420         4          1        2      yes       yes      yes   
    ..        ...   ...       ...        ...      ...      ...       ...      ...   
    540   1820000  3000         2          1        1      yes        no      yes   
    541   1767150  2400         3          1        1       no        no       no   
    542   1750000  3620         2          1        1      yes        no       no   
    543   1750000  2910         3          1        1       no        no       no   
    544   1750000  3850         3          1        2      yes        no       no   
    
        hotwaterheating airconditioning  parking prefarea furnishingstatus  
    0                no             yes        2      yes        furnished  
    1                no             yes        3       no        furnished  
    2                no              no        2      yes   semi-furnished  
    3                no             yes        3      yes        furnished  
    4                no             yes        2       no        furnished  
    ..              ...             ...      ...      ...              ...  
    540              no              no        2       no      unfurnished  
    541              no              no        0       no   semi-furnished  
    542              no              no        0       no      unfurnished  
    543              no              no        0       no        furnished  
    544              no              no        0       no      unfurnished  
    
    [545 rows x 13 columns]>




```python
reg.isnull().sum()
```




    price               0
    area                0
    bedrooms            0
    bathrooms           0
    stories             0
    mainroad            0
    guestroom           0
    basement            0
    hotwaterheating     0
    airconditioning     0
    parking             0
    prefarea            0
    furnishingstatus    0
    dtype: int64



                                             RENAMING SOME COLUMNS


```python
reg.rename(columns = {'hotwaterheating':'Water_Heater', 'airconditioning': 'Air_conditioning', 'furnishingstatus':'Furnishing_Status', 
                      'prefarea':'Prefer', 'basement': 'Basement', 'guestroom': 'Guestroom', 'mainroad':'Mainroad', 'stories': 'Stories', 
                      'bathrooms': 'Bathrooms',	'bedrooms':'Bedrooms', 'area': 'Area', 'price': 'Price'}, inplace=True)
```


```python
reg.rename(columns ={'furnishing_status':'Furnishing_Status'}, inplace=True)
```


```python
reg.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Area</th>
      <th>Bedrooms</th>
      <th>Bathrooms</th>
      <th>Stories</th>
      <th>Mainroad</th>
      <th>Guestroom</th>
      <th>Basement</th>
      <th>Water_Heater</th>
      <th>Air_conditioning</th>
      <th>parking</th>
      <th>Prefer</th>
      <th>Furnishing_Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13300000</td>
      <td>7420</td>
      <td>4</td>
      <td>2</td>
      <td>3</td>
      <td>yes</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>yes</td>
      <td>2</td>
      <td>yes</td>
      <td>furnished</td>
    </tr>
    <tr>
      <th>1</th>
      <td>12250000</td>
      <td>8960</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>yes</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>yes</td>
      <td>3</td>
      <td>no</td>
      <td>furnished</td>
    </tr>
    <tr>
      <th>2</th>
      <td>12250000</td>
      <td>9960</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
      <td>yes</td>
      <td>no</td>
      <td>yes</td>
      <td>no</td>
      <td>no</td>
      <td>2</td>
      <td>yes</td>
      <td>semi-furnished</td>
    </tr>
    <tr>
      <th>3</th>
      <td>12215000</td>
      <td>7500</td>
      <td>4</td>
      <td>2</td>
      <td>2</td>
      <td>yes</td>
      <td>no</td>
      <td>yes</td>
      <td>no</td>
      <td>yes</td>
      <td>3</td>
      <td>yes</td>
      <td>furnished</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11410000</td>
      <td>7420</td>
      <td>4</td>
      <td>1</td>
      <td>2</td>
      <td>yes</td>
      <td>yes</td>
      <td>yes</td>
      <td>no</td>
      <td>yes</td>
      <td>2</td>
      <td>no</td>
      <td>furnished</td>
    </tr>
  </tbody>
</table>
</div>



                                        CHECKING MORE INFO ABOUT THE DATASETS


```python
reg.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 545 entries, 0 to 544
    Data columns (total 13 columns):
     #   Column             Non-Null Count  Dtype 
    ---  ------             --------------  ----- 
     0   Price              545 non-null    int64 
     1   Area               545 non-null    int64 
     2   Bedrooms           545 non-null    int64 
     3   Bathrooms          545 non-null    int64 
     4   Stories            545 non-null    int64 
     5   Mainroad           545 non-null    object
     6   Guestroom          545 non-null    object
     7   Basement           545 non-null    object
     8   Water_Heater       545 non-null    object
     9   Air_conditioning   545 non-null    object
     10  parking            545 non-null    int64 
     11  Prefer             545 non-null    object
     12  Furnishing_Status  545 non-null    object
    dtypes: int64(6), object(7)
    memory usage: 55.5+ KB
    


```python
reg.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Area</th>
      <th>Bedrooms</th>
      <th>Bathrooms</th>
      <th>Stories</th>
      <th>parking</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>5.450000e+02</td>
      <td>545.000000</td>
      <td>545.000000</td>
      <td>545.000000</td>
      <td>545.000000</td>
      <td>545.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>4.766729e+06</td>
      <td>5150.541284</td>
      <td>2.965138</td>
      <td>1.286239</td>
      <td>1.805505</td>
      <td>0.693578</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1.870440e+06</td>
      <td>2170.141023</td>
      <td>0.738064</td>
      <td>0.502470</td>
      <td>0.867492</td>
      <td>0.861586</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.750000e+06</td>
      <td>1650.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.430000e+06</td>
      <td>3600.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>4.340000e+06</td>
      <td>4600.000000</td>
      <td>3.000000</td>
      <td>1.000000</td>
      <td>2.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>5.740000e+06</td>
      <td>6360.000000</td>
      <td>3.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.330000e+07</td>
      <td>16200.000000</td>
      <td>6.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>3.000000</td>
    </tr>
  </tbody>
</table>
</div>



                                                 EDA


```python
sns.jointplot(x="Bedrooms", y="Price", data=reg, alpha=0.5)
```




    <seaborn.axisgrid.JointGrid at 0x23c85955580>




    
![png](output_21_1.png)
    



```python
sns.jointplot(x="Bathrooms", y="Price", data=reg)
```




    <seaborn.axisgrid.JointGrid at 0x23c860556a0>




    
![png](output_22_1.png)
    



```python
sns.pairplot(reg, kind='scatter', plot_kws={'alpha': 0.4})
```




    <seaborn.axisgrid.PairGrid at 0x23c863ce210>




    
![png](output_23_1.png)
    



```python

```


```python
sns.lmplot(x = 'Stories',
           y = 'Price',
           data = reg,
           scatter_kws={'alpha':0.03})
```




    <seaborn.axisgrid.FacetGrid at 0x23c8d8d2420>




    
![png](output_25_1.png)
    



```python
from sklearn.model_selection import train_test_split
```


```python
xt = reg[['Price', 'Area', 'Bedrooms', 'Bathrooms', 'Stories']]
```


```python
xt
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Price</th>
      <th>Area</th>
      <th>Bedrooms</th>
      <th>Bathrooms</th>
      <th>Stories</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13300000</td>
      <td>7420</td>
      <td>4</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>12250000</td>
      <td>8960</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>12250000</td>
      <td>9960</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>12215000</td>
      <td>7500</td>
      <td>4</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11410000</td>
      <td>7420</td>
      <td>4</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>540</th>
      <td>1820000</td>
      <td>3000</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>541</th>
      <td>1767150</td>
      <td>2400</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>542</th>
      <td>1750000</td>
      <td>3620</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>543</th>
      <td>1750000</td>
      <td>2910</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>544</th>
      <td>1750000</td>
      <td>3850</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>545 rows × 5 columns</p>
</div>




```python
x = reg[['Area', 'Bedrooms', 'Bathrooms', 'Stories']]
y = reg['Price']
```


```python
x_train, x_test, y_train, y_test, = train_test_split(x, y, test_size=0.3, random_state=42)
```


```python
y_train
```




    126    5880000
    363    3710000
    370    3640000
    31     8400000
    113    6083000
            ...   
    71     6755000
    106    6160000
    270    4340000
    435    3290000
    102    6195000
    Name: Price, Length: 381, dtype: int64




```python
y_test
```




    316    4060000
    77     6650000
    360    3710000
    90     6440000
    493    2800000
            ...   
    395    3500000
    425    3360000
    195    4970000
    452    3150000
    154    5530000
    Name: Price, Length: 164, dtype: int64




```python
x_train
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Area</th>
      <th>Bedrooms</th>
      <th>Bathrooms</th>
      <th>Stories</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>126</th>
      <td>7160</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>363</th>
      <td>3584</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>370</th>
      <td>4280</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>31</th>
      <td>7000</td>
      <td>3</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>113</th>
      <td>9620</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>71</th>
      <td>6000</td>
      <td>4</td>
      <td>2</td>
      <td>4</td>
    </tr>
    <tr>
      <th>106</th>
      <td>5450</td>
      <td>4</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>270</th>
      <td>4500</td>
      <td>3</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>435</th>
      <td>4040</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>102</th>
      <td>5500</td>
      <td>3</td>
      <td>2</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
<p>381 rows × 4 columns</p>
</div>




```python
x_test
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Area</th>
      <th>Bedrooms</th>
      <th>Bathrooms</th>
      <th>Stories</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>316</th>
      <td>5900</td>
      <td>4</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>77</th>
      <td>6500</td>
      <td>3</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>360</th>
      <td>4040</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>90</th>
      <td>5000</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>493</th>
      <td>3960</td>
      <td>3</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>395</th>
      <td>3600</td>
      <td>6</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>425</th>
      <td>3185</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>195</th>
      <td>4410</td>
      <td>4</td>
      <td>3</td>
      <td>2</td>
    </tr>
    <tr>
      <th>452</th>
      <td>9000</td>
      <td>3</td>
      <td>1</td>
      <td>2</td>
    </tr>
    <tr>
      <th>154</th>
      <td>3650</td>
      <td>3</td>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>164 rows × 4 columns</p>
</div>



                                             TRAINING THE MODEL


```python
from sklearn.linear_model import LinearRegression
```


```python
lm = LinearRegression()
```


```python
lm.fit(x_train, y_train)
```




<style>#sk-container-id-1 {
  /* Definition of color scheme common for light and dark mode */
  --sklearn-color-text: black;
  --sklearn-color-line: gray;
  /* Definition of color scheme for unfitted estimators */
  --sklearn-color-unfitted-level-0: #fff5e6;
  --sklearn-color-unfitted-level-1: #f6e4d2;
  --sklearn-color-unfitted-level-2: #ffe0b3;
  --sklearn-color-unfitted-level-3: chocolate;
  /* Definition of color scheme for fitted estimators */
  --sklearn-color-fitted-level-0: #f0f8ff;
  --sklearn-color-fitted-level-1: #d4ebff;
  --sklearn-color-fitted-level-2: #b3dbfd;
  --sklearn-color-fitted-level-3: cornflowerblue;

  /* Specific color for light theme */
  --sklearn-color-text-on-default-background: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, black)));
  --sklearn-color-background: var(--sg-background-color, var(--theme-background, var(--jp-layout-color0, white)));
  --sklearn-color-border-box: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, black)));
  --sklearn-color-icon: #696969;

  @media (prefers-color-scheme: dark) {
    /* Redefinition of color scheme for dark theme */
    --sklearn-color-text-on-default-background: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, white)));
    --sklearn-color-background: var(--sg-background-color, var(--theme-background, var(--jp-layout-color0, #111)));
    --sklearn-color-border-box: var(--sg-text-color, var(--theme-code-foreground, var(--jp-content-font-color1, white)));
    --sklearn-color-icon: #878787;
  }
}

#sk-container-id-1 {
  color: var(--sklearn-color-text);
}

#sk-container-id-1 pre {
  padding: 0;
}

#sk-container-id-1 input.sk-hidden--visually {
  border: 0;
  clip: rect(1px 1px 1px 1px);
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}

#sk-container-id-1 div.sk-dashed-wrapped {
  border: 1px dashed var(--sklearn-color-line);
  margin: 0 0.4em 0.5em 0.4em;
  box-sizing: border-box;
  padding-bottom: 0.4em;
  background-color: var(--sklearn-color-background);
}

#sk-container-id-1 div.sk-container {
  /* jupyter's `normalize.less` sets `[hidden] { display: none; }`
     but bootstrap.min.css set `[hidden] { display: none !important; }`
     so we also need the `!important` here to be able to override the
     default hidden behavior on the sphinx rendered scikit-learn.org.
     See: https://github.com/scikit-learn/scikit-learn/issues/21755 */
  display: inline-block !important;
  position: relative;
}

#sk-container-id-1 div.sk-text-repr-fallback {
  display: none;
}

div.sk-parallel-item,
div.sk-serial,
div.sk-item {
  /* draw centered vertical line to link estimators */
  background-image: linear-gradient(var(--sklearn-color-text-on-default-background), var(--sklearn-color-text-on-default-background));
  background-size: 2px 100%;
  background-repeat: no-repeat;
  background-position: center center;
}

/* Parallel-specific style estimator block */

#sk-container-id-1 div.sk-parallel-item::after {
  content: "";
  width: 100%;
  border-bottom: 2px solid var(--sklearn-color-text-on-default-background);
  flex-grow: 1;
}

#sk-container-id-1 div.sk-parallel {
  display: flex;
  align-items: stretch;
  justify-content: center;
  background-color: var(--sklearn-color-background);
  position: relative;
}

#sk-container-id-1 div.sk-parallel-item {
  display: flex;
  flex-direction: column;
}

#sk-container-id-1 div.sk-parallel-item:first-child::after {
  align-self: flex-end;
  width: 50%;
}

#sk-container-id-1 div.sk-parallel-item:last-child::after {
  align-self: flex-start;
  width: 50%;
}

#sk-container-id-1 div.sk-parallel-item:only-child::after {
  width: 0;
}

/* Serial-specific style estimator block */

#sk-container-id-1 div.sk-serial {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: var(--sklearn-color-background);
  padding-right: 1em;
  padding-left: 1em;
}


/* Toggleable style: style used for estimator/Pipeline/ColumnTransformer box that is
clickable and can be expanded/collapsed.
- Pipeline and ColumnTransformer use this feature and define the default style
- Estimators will overwrite some part of the style using the `sk-estimator` class
*/

/* Pipeline and ColumnTransformer style (default) */

#sk-container-id-1 div.sk-toggleable {
  /* Default theme specific background. It is overwritten whether we have a
  specific estimator or a Pipeline/ColumnTransformer */
  background-color: var(--sklearn-color-background);
}

/* Toggleable label */
#sk-container-id-1 label.sk-toggleable__label {
  cursor: pointer;
  display: block;
  width: 100%;
  margin-bottom: 0;
  padding: 0.5em;
  box-sizing: border-box;
  text-align: center;
}

#sk-container-id-1 label.sk-toggleable__label-arrow:before {
  /* Arrow on the left of the label */
  content: "▸";
  float: left;
  margin-right: 0.25em;
  color: var(--sklearn-color-icon);
}

#sk-container-id-1 label.sk-toggleable__label-arrow:hover:before {
  color: var(--sklearn-color-text);
}

/* Toggleable content - dropdown */

#sk-container-id-1 div.sk-toggleable__content {
  max-height: 0;
  max-width: 0;
  overflow: hidden;
  text-align: left;
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-1 div.sk-toggleable__content.fitted {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

#sk-container-id-1 div.sk-toggleable__content pre {
  margin: 0.2em;
  border-radius: 0.25em;
  color: var(--sklearn-color-text);
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-1 div.sk-toggleable__content.fitted pre {
  /* unfitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

#sk-container-id-1 input.sk-toggleable__control:checked~div.sk-toggleable__content {
  /* Expand drop-down */
  max-height: 200px;
  max-width: 100%;
  overflow: auto;
}

#sk-container-id-1 input.sk-toggleable__control:checked~label.sk-toggleable__label-arrow:before {
  content: "▾";
}

/* Pipeline/ColumnTransformer-specific style */

#sk-container-id-1 div.sk-label input.sk-toggleable__control:checked~label.sk-toggleable__label {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-1 div.sk-label.fitted input.sk-toggleable__control:checked~label.sk-toggleable__label {
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Estimator-specific style */

/* Colorize estimator box */
#sk-container-id-1 div.sk-estimator input.sk-toggleable__control:checked~label.sk-toggleable__label {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-1 div.sk-estimator.fitted input.sk-toggleable__control:checked~label.sk-toggleable__label {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-2);
}

#sk-container-id-1 div.sk-label label.sk-toggleable__label,
#sk-container-id-1 div.sk-label label {
  /* The background is the default theme color */
  color: var(--sklearn-color-text-on-default-background);
}

/* On hover, darken the color of the background */
#sk-container-id-1 div.sk-label:hover label.sk-toggleable__label {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-unfitted-level-2);
}

/* Label box, darken color on hover, fitted */
#sk-container-id-1 div.sk-label.fitted:hover label.sk-toggleable__label.fitted {
  color: var(--sklearn-color-text);
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Estimator label */

#sk-container-id-1 div.sk-label label {
  font-family: monospace;
  font-weight: bold;
  display: inline-block;
  line-height: 1.2em;
}

#sk-container-id-1 div.sk-label-container {
  text-align: center;
}

/* Estimator-specific */
#sk-container-id-1 div.sk-estimator {
  font-family: monospace;
  border: 1px dotted var(--sklearn-color-border-box);
  border-radius: 0.25em;
  box-sizing: border-box;
  margin-bottom: 0.5em;
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-0);
}

#sk-container-id-1 div.sk-estimator.fitted {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-0);
}

/* on hover */
#sk-container-id-1 div.sk-estimator:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-2);
}

#sk-container-id-1 div.sk-estimator.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-2);
}

/* Specification for estimator info (e.g. "i" and "?") */

/* Common style for "i" and "?" */

.sk-estimator-doc-link,
a:link.sk-estimator-doc-link,
a:visited.sk-estimator-doc-link {
  float: right;
  font-size: smaller;
  line-height: 1em;
  font-family: monospace;
  background-color: var(--sklearn-color-background);
  border-radius: 1em;
  height: 1em;
  width: 1em;
  text-decoration: none !important;
  margin-left: 1ex;
  /* unfitted */
  border: var(--sklearn-color-unfitted-level-1) 1pt solid;
  color: var(--sklearn-color-unfitted-level-1);
}

.sk-estimator-doc-link.fitted,
a:link.sk-estimator-doc-link.fitted,
a:visited.sk-estimator-doc-link.fitted {
  /* fitted */
  border: var(--sklearn-color-fitted-level-1) 1pt solid;
  color: var(--sklearn-color-fitted-level-1);
}

/* On hover */
div.sk-estimator:hover .sk-estimator-doc-link:hover,
.sk-estimator-doc-link:hover,
div.sk-label-container:hover .sk-estimator-doc-link:hover,
.sk-estimator-doc-link:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

div.sk-estimator.fitted:hover .sk-estimator-doc-link.fitted:hover,
.sk-estimator-doc-link.fitted:hover,
div.sk-label-container:hover .sk-estimator-doc-link.fitted:hover,
.sk-estimator-doc-link.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

/* Span, style for the box shown on hovering the info icon */
.sk-estimator-doc-link span {
  display: none;
  z-index: 9999;
  position: relative;
  font-weight: normal;
  right: .2ex;
  padding: .5ex;
  margin: .5ex;
  width: min-content;
  min-width: 20ex;
  max-width: 50ex;
  color: var(--sklearn-color-text);
  box-shadow: 2pt 2pt 4pt #999;
  /* unfitted */
  background: var(--sklearn-color-unfitted-level-0);
  border: .5pt solid var(--sklearn-color-unfitted-level-3);
}

.sk-estimator-doc-link.fitted span {
  /* fitted */
  background: var(--sklearn-color-fitted-level-0);
  border: var(--sklearn-color-fitted-level-3);
}

.sk-estimator-doc-link:hover span {
  display: block;
}

/* "?"-specific style due to the `<a>` HTML tag */

#sk-container-id-1 a.estimator_doc_link {
  float: right;
  font-size: 1rem;
  line-height: 1em;
  font-family: monospace;
  background-color: var(--sklearn-color-background);
  border-radius: 1rem;
  height: 1rem;
  width: 1rem;
  text-decoration: none;
  /* unfitted */
  color: var(--sklearn-color-unfitted-level-1);
  border: var(--sklearn-color-unfitted-level-1) 1pt solid;
}

#sk-container-id-1 a.estimator_doc_link.fitted {
  /* fitted */
  border: var(--sklearn-color-fitted-level-1) 1pt solid;
  color: var(--sklearn-color-fitted-level-1);
}

/* On hover */
#sk-container-id-1 a.estimator_doc_link:hover {
  /* unfitted */
  background-color: var(--sklearn-color-unfitted-level-3);
  color: var(--sklearn-color-background);
  text-decoration: none;
}

#sk-container-id-1 a.estimator_doc_link.fitted:hover {
  /* fitted */
  background-color: var(--sklearn-color-fitted-level-3);
}
</style><div id="sk-container-id-1" class="sk-top-container"><div class="sk-text-repr-fallback"><pre>LinearRegression()</pre><b>In a Jupyter environment, please rerun this cell to show the HTML representation or trust the notebook. <br />On GitHub, the HTML representation is unable to render, please try loading this page with nbviewer.org.</b></div><div class="sk-container" hidden><div class="sk-item"><div class="sk-estimator fitted sk-toggleable"><input class="sk-toggleable__control sk-hidden--visually" id="sk-estimator-id-1" type="checkbox" checked><label for="sk-estimator-id-1" class="sk-toggleable__label fitted sk-toggleable__label-arrow fitted">&nbsp;&nbsp;LinearRegression<a class="sk-estimator-doc-link fitted" rel="noreferrer" target="_blank" href="https://scikit-learn.org/1.4/modules/generated/sklearn.linear_model.LinearRegression.html">?<span>Documentation for LinearRegression</span></a><span class="sk-estimator-doc-link fitted">i<span>Fitted</span></span></label><div class="sk-toggleable__content fitted"><pre>LinearRegression()</pre></div> </div></div></div></div>




```python
lm.coef_
```




    array([3.75061655e+02, 1.96951901e+05, 1.23657238e+06, 4.58526872e+05])




```python
cdf = pd.DataFrame(lm.coef_, x.columns, columns=['Coef'])
print(cdf)

```

                       Coef
    Area       3.750617e+02
    Bedrooms   1.969519e+05
    Bathrooms  1.236572e+06
    Stories    4.585269e+05
    

                                                          PREDICTION


```python
predictions = lm.predict(x_test)
```


```python
predictions
```




    array([6268927.85604259, 6755539.81993245, 3482310.12730352,
           4497848.08899972, 3649257.09592971, 4684427.26348525,
           5359538.24232582, 5927621.75007319, 3182260.80337437,
           3176679.41074131, 9427719.21173292, 3442553.5918829 ,
           3362290.39773186, 3785230.944668  , 4111534.58444095,
           6457158.374978  , 3175711.22324632, 4872909.74391115,
           4816650.49567443, 4217430.97092992, 5422403.06602219,
           4723808.73725095, 3335661.02023315, 4047774.103106  ,
           5258271.59549974, 7594726.27396387, 3126001.55513766,
           4984297.15578033, 7573353.65927343, 3550772.87815775,
           5359358.81069176, 3792732.17776623, 6568008.99247674,
           5103572.66168167, 4610411.11766376, 5584395.80363862,
           4365076.26316107, 4012187.77808003, 3469227.50157223,
           5101360.92430331, 5157004.94867365, 3328534.84878983,
           6725534.88753954, 4197798.76507058, 4498727.21211349,
           4174298.8806151 , 7026535.86443886, 4559777.79425071,
           4986307.36349834, 3092246.00619563, 7579751.80543321,
           3092246.00619563, 4881290.10012314, 4310317.261544  ,
           4184716.13933929, 3255442.35827271, 6932770.450711  ,
           3522687.78623   , 5238639.3896404 , 3392295.33012477,
           4396329.48068316, 4659868.82428195, 4382458.09909094,
           3827366.84982203, 4632870.28476783, 4032771.63690955,
           7054620.9563666 , 3747724.77917686, 6887063.36064192,
           4301864.3754756 , 4928037.90754362, 5466458.81164138,
           5117578.94271734, 7338732.69565393, 2973726.52324362,
           5653826.74198784, 3984013.62177106, 3772982.90985987,
           4414382.87194903, 4151839.71351103, 6899983.08926396,
           4152791.3664812 , 5463424.42109678, 5582727.92466392,
           3260144.627792  , 7331052.03092163, 3214185.57623246,
           3916502.523887  , 7297548.44347008, 7543006.3981372 ,
           3730936.06908707, 5183259.26451745, 4011147.06072863,
           3901500.05769055, 8707617.3688278 , 4207219.83863397,
           5922404.78420973, 6951523.53345657, 5143905.78841755,
           6072944.14251847, 3837739.5763556 , 5584395.80363862,
           4194999.80149164, 6333388.02885723, 5069861.64493026,
           5418668.98399789, 7223487.76545797, 6109482.12051462,
           5688461.41404364, 7026535.86443886, 6101029.23444621,
           3398296.31660336, 3601450.7337614 , 4029021.02036043,
           4501598.70554883, 4066527.18585157, 4067825.90281087,
           3356709.0050988 , 4421884.10504725, 3792732.17776623,
           4855035.78427934, 4789444.52686045, 3961509.92247638,
           3550772.87815775, 5819732.99326264, 3064160.91426788,
           5585363.99113361, 4948470.6685429 , 8590559.49994433,
           6123532.9337409 , 3747724.77917686, 5031387.29194412,
           5773057.71569857, 7223443.23326736, 3991514.85486929,
           3330410.15706439, 3664259.56212617, 4928917.03065739,
           4082408.7751618 , 3942756.8397308 , 2655674.23987873,
           3803984.02741358, 4752890.01433949, 3885573.93618971,
           5005060.44624391, 3441053.34526326, 6267008.01557742,
           5408116.82583025, 7110197.04764843, 7681785.11009394,
           5852699.78634374, 4857907.27771469, 3702717.38058749,
           4810980.03866015, 3927754.37353435, 6774544.8641685 ,
           6508967.3151859 , 3209309.77471861, 7206565.45879634,
           4563617.47518105, 3161632.41235424, 6946658.36682803,
           5998094.70864543, 5228087.23147276])




```python
from sklearn.metrics import mean_squared_error, mean_absolute_error
import math
```


```python
print("Mean Absolute Error: ", mean_absolute_error(y_test, predictions))
print("Mean Squared Error: ", mean_squared_error(y_test, predictions))
print("RMSE: ", math.sqrt(mean_squared_error(y_test, predictions)))
```

    Mean Absolute Error:  1088088.9140581128
    Mean Squared Error:  2116673381183.6726
    RMSE:  1454879.163773979
    


```python
                                    RESIDUALS
```


```python
residuals = y_test - predictions
```


```python
residuals
```




    316   -2.208928e+06
    77    -1.055398e+05
    360    2.276899e+05
    90     1.942152e+06
    493   -8.492571e+05
               ...     
    395   -1.063617e+06
    425    1.983676e+05
    195   -1.976658e+06
    452   -2.848095e+06
    154    3.019128e+05
    Name: Price, Length: 164, dtype: float64




```python
sns.displot(residuals)
```




    <seaborn.axisgrid.FacetGrid at 0x23c89079460>




    
![png](output_49_1.png)
    



```python
import pylab
import scipy.stats as stats

stats.probplot(residuals, dist="norm", plot=pylab)
pylab.show()
```


    
![png](output_50_0.png)
    



```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```
