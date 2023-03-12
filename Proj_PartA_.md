---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

<div class="cell markdown" id="tK5OdplVC5rH">

# **CUHK-STAT1013: Assignment Part 1: Sharing Your Idea and Data**

</div>

<div class="cell markdown" id="mTvLD01HC5MB">

### Description:

Dataset describing the prices of flats in Hong Kong and the houses that
of in Korea.

Github:<https://github.com/Joey12333/datasets/blob/main/seoul%20-%20SeoulRealEstate%20(1).csv>
<https://github.com/Joey12333/datasets/blob/main/TM_Register_of_Transactions_tc%20(3).csv>

Sample size total:4312

</div>

<div class="cell code" execution_count="112"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="HqQt0ofjxLmq" outputId="51fbc150-1fe7-478b-b9a4-b6d30c595e88">

``` python
df1.info()
```

<div class="output stream stdout">

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 291 entries, 0 to 290
    Data columns (total 5 columns):
     #   Column            Non-Null Count  Dtype  
    ---  ------            --------------  -----  
     0   買賣合約
    的日期
    (日-月-年)  290 non-null    object 
     1   大廈名稱              290 non-null    object 
     2   樓層                290 non-null    float64
     3   單位                290 non-null    object 
     4   成交金額              290 non-null    float64
    dtypes: float64(2), object(3)
    memory usage: 11.5+ KB

</div>

</div>

<div class="cell code" execution_count="113"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="WfQPwmk_xKfH" outputId="43770573-a7ca-4b28-bd08-34fc61d120b6">

``` python
df2.info()
```

<div class="output stream stdout">

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4021 entries, 0 to 4020
    Data columns (total 11 columns):
     #   Column      Non-Null Count  Dtype  
    ---  ------      --------------  -----  
     0   id          4021 non-null   int64  
     1   lat         4021 non-null   float64
     2   lng         4021 non-null   float64
     3   households  4021 non-null   int64  
     4   buildDate   4021 non-null   int64  
     5   score       4021 non-null   float64
     6   m2          4021 non-null   int64  
     7   p           4021 non-null   int64  
     8   min_sales   3931 non-null   float64
     9   max_sales   3931 non-null   float64
     10  avg_sales   3931 non-null   float64
    dtypes: float64(6), int64(5)
    memory usage: 345.7 KB

</div>

</div>

<div class="cell markdown" id="owPJwQpjgKee">

### Hypothesis:

-   Tell us what your idea is and why you have chosen to pursue this
    idea.
    -   I am interested in the difference between the housing price in
        Hong Kong and Korea. Which country has the higher average
        housing price?
-   What two groups you are comparing:
    -   **G1**: housing price in Hong Kong ; **G2**: housing price in
        Korea
-   What you will be measuring (i.e., what your response variable will
    be)
    -   'housing prices'
-   Is your response variable quantitative rather than categorical?
    -   'price' is numerical data that be considered as quantitative
        variables.
-   Make a prediction about what kind of difference you expect to see
    between your samples and WHY.
    -   **G1>G2**,since [Hong Kong named world’s most expensive city to
        buy a
        home](https://capital.com/hong-kong-house-price-crash-world-most-expensive-housing-market)
-   Talk about how you will gather your data
    -   From Github
        link:1.)<https://github.com/Joey12333/datasets/blob/main/seoul%20-%20SeoulRealEstate%20(1).csv>

        2.)<https://github.com/Joey12333/datasets/blob/main/TM_Register_of_Transactions_tc%20(3).csv>

        -   And on the gorvernment websites
-   If you had unlimited resources (time, money, staff, etc.) how would
    you collect your data?
    -   Collect more data about the housing prices in Hong Kong and
        Korea -Measure all the data are collected in random but not be
        collected in specific(ie. specific districts or places)

</div>

<div class="cell markdown" id="PIIOcJ81vqFD">

# **Prepare your dataset**

</div>

<div class="cell markdown" id="pB49E0fHuXn6">

Tell us what groups you want to compare in the dataset?

-   **G1 (Housing Price \| Country = Hong Kong) vs. G2 (Housing Price \|
    Country = Korea)**

</div>

<div class="cell markdown" id="zvdysfgPBrCY">

### Print first 5 records of each group, respectively.

</div>

<div class="cell code" execution_count="114"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:206}"
id="GDD2DDU4loRD" outputId="fa1a4edb-198a-4ade-cbb7-b0a43b2e1f86">

``` python
import pandas as pd

df1 = pd.read_csv('TM_Register_of_Transactions_tc (3).csv')
df2 = pd.read_csv('seoul - SeoulRealEstate.csv')
df1.head(5)
```

<div class="output execute_result" execution_count="114">

      買賣合約\n的日期\n(日-月-年) 大廈名稱    樓層 單位        成交金額
    0         05-03-2018  翠鳴臺   2.0  B  $2,895,000
    1         05-03-2018  翠鳴臺   5.0  G  $3,146,000
    2         05-03-2018  翠鳴臺  11.0  G  $3,203,000
    3         05-03-2018  翠鳴臺  16.0  J  $2,091,000
    4         05-03-2018  翠鳴臺  20.0  B  $3,301,000

</div>

</div>

<div class="cell code" execution_count="121"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="AEFgomV9x2sP" outputId="cb5aab89-f977-4623-b9dd-9e628830cd00">

``` python
print((df1['成交金額']).head(5))
```

<div class="output stream stdout">

    0    2895000.0
    1    3146000.0
    2    3203000.0
    3    2091000.0
    4    3301000.0
    Name: 成交金額, dtype: float64

</div>

</div>

<div class="cell code" execution_count="116"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:206}"
id="Y994qnl7nBjq" outputId="2dbf10c4-6458-407f-a8c8-4624c1f27a8d">

``` python
df2.head(5)
```

<div class="output execute_result" execution_count="116">

          id        lat         lng  households  buildDate  score   m2   p  \
    0   2766  37.681604  127.056592         492     200006    4.3  139  42   
    1   5860  37.679290  127.057021         468     200105    4.1  105  32   
    2  15564  37.676882  127.058075          57     200502    4.8   86  26   
    3   3700  37.675277  127.060001         216     199509    4.8  102  31   
    4   6204  37.676381  127.058361         165     200306    4.8   91  28   

       min_sales  max_sales  avg_sales  
    0    60100.0    62000.0    61000.0  
    1    48600.0    52200.0    51000.0  
    2    36000.0    46000.0    40500.0  
    3    34000.0    34800.0    34500.0  
    4    27900.0    50300.0    40000.0  

</div>

</div>

<div class="cell code" execution_count="117"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;}"
id="7dQF9KDB0K3E" outputId="f50c4427-b6ac-4e4e-e05c-bba61b46c79a">

``` python
print((df2['avg_sales']).head(5))
```

<div class="output stream stdout">

    0    61000.0
    1    51000.0
    2    40500.0
    3    34500.0
    4    40000.0
    Name: avg_sales, dtype: float64

</div>

</div>

<div class="cell markdown" id="dEOy8DVxpuzK">

Any other data description and visualization you want to add.

-   'min_sales' 'max_sales' 'avg_sales' are all in (10k) and prices in
    'seoul - SeoulRealEstate.csv' are in unit of 'won'.
-   The price conversion rate of 'HKD' to 'WON' is 1:166

</div>

<div class="cell code" execution_count="118"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:424}"
id="aXKQ5kaQ6JNY" outputId="aa7da5d2-f6e2-4331-b1a6-4f174d677f86">

``` python
df1['成交金額']=df1['成交金額'].str.replace(',','')
df1
```

<div class="output execute_result" execution_count="118">

        買賣合約\n的日期\n(日-月-年) 大廈名稱    樓層   單位      成交金額
    0           05-03-2018  翠鳴臺   2.0    B  $2895000
    1           05-03-2018  翠鳴臺   5.0    G  $3146000
    2           05-03-2018  翠鳴臺  11.0    G  $3203000
    3           05-03-2018  翠鳴臺  16.0    J  $2091000
    4           05-03-2018  翠鳴臺  20.0    B  $3301000
    ..                 ...  ...   ...  ...       ...
    286         23-03-2018  翠鳴臺  12.0    K  $2008000
    287         26-03-2018  翠鳴臺  13.0    K  $2015000
    288         23-03-2018  翠鳴臺  14.0    K  $2021000
    289         22-03-2018  翠鳴臺  15.0    K  $2027000
    290                NaN  NaN   NaN  NaN       NaN

    [291 rows x 5 columns]

</div>

</div>

<div class="cell code" execution_count="119"
colab="{&quot;base_uri&quot;:&quot;https://localhost:8080/&quot;,&quot;height&quot;:478}"
id="UG13B1Fm_NUJ" outputId="05a55157-83b7-4945-8ba7-84b113d32c9b">

``` python
df1['成交金額']=df1['成交金額'].str.replace('$','')
df1
```

<div class="output stream stderr">

    <ipython-input-119-fd8147d17daf>:1: FutureWarning: The default value of regex will change from True to False in a future version. In addition, single character regular expressions will *not* be treated as literal strings when regex=True.
      df1['成交金額']=df1['成交金額'].str.replace('$','')

</div>

<div class="output execute_result" execution_count="119">

        買賣合約\n的日期\n(日-月-年) 大廈名稱    樓層   單位     成交金額
    0           05-03-2018  翠鳴臺   2.0    B  2895000
    1           05-03-2018  翠鳴臺   5.0    G  3146000
    2           05-03-2018  翠鳴臺  11.0    G  3203000
    3           05-03-2018  翠鳴臺  16.0    J  2091000
    4           05-03-2018  翠鳴臺  20.0    B  3301000
    ..                 ...  ...   ...  ...      ...
    286         23-03-2018  翠鳴臺  12.0    K  2008000
    287         26-03-2018  翠鳴臺  13.0    K  2015000
    288         23-03-2018  翠鳴臺  14.0    K  2021000
    289         22-03-2018  翠鳴臺  15.0    K  2027000
    290                NaN  NaN   NaN  NaN      NaN

    [291 rows x 5 columns]

</div>

</div>

<div class="cell code" execution_count="120" id="ljv8LJ_JAyH9">

``` python
df1['成交金額']=df1['成交金額'].astype(float)
```

</div>
