Preparing Mexico Data

.. code:: ipython3

    import pandas as pd
    from IPython.display import VimeoVideo

Import
======

The first part of any data science project is preparing your data, which
means making sure its in the right place and format for you to conduct
your analysis. The first step of any data preparation is importing your
raw data and cleaning it.

If you look in the ``small-data`` directory on your machine, you’ll see
that the data for this project comes in three CSV files:
``mexico-real-estate-1.csv``, ``mexico-real-estate-2.csv``, and
``mexico-real-estate-3.csv``.

.. code:: ipython3

    VimeoVideo("656321516", h="e85e3bf248", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656321516?h=e85e3bf248"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.2.1:** Read these three files into three separate DataFrames
named ``df1``, ``df2``, and ``df3``, respectively.

-  `What’s a
   DataFrame? <../%40textbook/03-pandas-getting-started.ipynb#Pandas>`__
-  `What’s a CSV
   file? <../%40textbook/03-pandas-getting-started.ipynb#CSV-Files>`__
-  `Read a CSV file into a DataFrame using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Working-with-DataFrames>`__

.. code:: ipython3

    df1 = pd.read_csv('./data/mexico-real-estate-1.csv')
    df2 = pd.read_csv('./data/mexico-real-estate-2.csv')
    df3 = pd.read_csv('./data/mexico-real-estate-3.csv')
    
    df3




.. raw:: html

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
          <th>property_type</th>
          <th>place_with_parent_names</th>
          <th>lat-lon</th>
          <th>area_m2</th>
          <th>price_usd</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>apartment</td>
          <td>|México|Distrito Federal|Gustavo A. Madero|Acu...</td>
          <td>19.52589,-99.151703</td>
          <td>71.0</td>
          <td>48550.59</td>
        </tr>
        <tr>
          <th>1</th>
          <td>house</td>
          <td>|México|Estado de México|Toluca|Metepec|</td>
          <td>19.2640539,-99.5727534</td>
          <td>233.0</td>
          <td>168636.73</td>
        </tr>
        <tr>
          <th>2</th>
          <td>house</td>
          <td>|México|Estado de México|Toluca|Toluca de Lerd...</td>
          <td>19.268629,-99.671722</td>
          <td>300.0</td>
          <td>86932.69</td>
        </tr>
        <tr>
          <th>3</th>
          <td>house</td>
          <td>|México|Morelos|Temixco|Burgos Bugambilias|</td>
          <td>NaN</td>
          <td>275.0</td>
          <td>263432.41</td>
        </tr>
        <tr>
          <th>4</th>
          <td>apartment</td>
          <td>|México|Veracruz de Ignacio de la Llave|Veracruz|</td>
          <td>19.511938,-96.871956</td>
          <td>84.0</td>
          <td>68508.67</td>
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
          <th>695</th>
          <td>house</td>
          <td>|México|Jalisco|Tlajomulco de Zúñiga|Tlajomulc...</td>
          <td>20.532264,-103.484418</td>
          <td>175.0</td>
          <td>121178.91</td>
        </tr>
        <tr>
          <th>696</th>
          <td>house</td>
          <td>|México|Morelos|Jiutepec|</td>
          <td>18.9289862,-99.1802147</td>
          <td>100.0</td>
          <td>47417.83</td>
        </tr>
        <tr>
          <th>697</th>
          <td>house</td>
          <td>|México|Yucatán|Mérida|</td>
          <td>21.0284038368,-89.6530058049</td>
          <td>81.0</td>
          <td>39524.23</td>
        </tr>
        <tr>
          <th>698</th>
          <td>house</td>
          <td>|México|San Luis Potosí|San Luis Potosí|</td>
          <td>22.11830417,-101.0321938992</td>
          <td>360.0</td>
          <td>245050.24</td>
        </tr>
        <tr>
          <th>699</th>
          <td>house</td>
          <td>|México|Estado de México|Toluca|Metepec|</td>
          <td>19.233201,-99.558519</td>
          <td>115.0</td>
          <td>110667.85</td>
        </tr>
      </tbody>
    </table>
    <p>700 rows × 5 columns</p>
    </div>



Clean ``df1``
-------------

Now that you have your three DataFrames, it’s time to inspect them to
see if they need any cleaning. Let’s look at them one-by-one.

.. code:: ipython3

    VimeoVideo("656320563", h="a6841fed28", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656320563?h=a6841fed28"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.2.2:** Inspect ``df1`` by looking at its
```shape`` <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.shape.html>`__
attribute. Then use the
```info`` <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.info.htm>`__
method to see the data types and number of missing values for each
column. Finally, use the
```head`` <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.head.html>`__
method to determine to look at the first five rows of your dataset.

-  `Inspect a DataFrame using the ``shape``, ``info``, and ``head`` in
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Inspecting-DataFrames>`__

.. code:: ipython3

    df1.head()




.. raw:: html

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
          <th>property_type</th>
          <th>state</th>
          <th>lat</th>
          <th>lon</th>
          <th>area_m2</th>
          <th>price_usd</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>house</td>
          <td>Estado de México</td>
          <td>19.560181</td>
          <td>-99.233528</td>
          <td>150.0</td>
          <td>$67,965.56</td>
        </tr>
        <tr>
          <th>1</th>
          <td>house</td>
          <td>Nuevo León</td>
          <td>25.688436</td>
          <td>-100.198807</td>
          <td>186.0</td>
          <td>$63,223.78</td>
        </tr>
        <tr>
          <th>2</th>
          <td>apartment</td>
          <td>Guerrero</td>
          <td>16.767704</td>
          <td>-99.764383</td>
          <td>82.0</td>
          <td>$84,298.37</td>
        </tr>
        <tr>
          <th>3</th>
          <td>apartment</td>
          <td>Guerrero</td>
          <td>16.829782</td>
          <td>-99.911012</td>
          <td>150.0</td>
          <td>$94,308.80</td>
        </tr>
        <tr>
          <th>4</th>
          <td>house</td>
          <td>Veracruz de Ignacio de la Llave</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>175.0</td>
          <td>$94,835.67</td>
        </tr>
      </tbody>
    </table>
    </div>



It looks like there are a couple of problems in this DataFrame that you
need to solve. First, there are many rows with ``NaN`` values in the
``"lat"`` and ``"lon"`` columns. Second, the data type for the
``"price_usd"`` column is ``object`` when it should be ``float``.

.. code:: ipython3

    VimeoVideo("656316512", h="33eb5cb26e", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656316512?h=33eb5cb26e"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.2.3:** Clean ``df1`` by dropping rows with ``NaN`` values. Then
remove the ``"$"`` and ``","`` characters from ``"price_usd"`` and
recast the values in the column as floats.

-  `What’s a data
   type? <../%40textbook/01-python-getting-started.ipynb#Data-Types>`__
-  `Drop rows with missing values from a DataFrame using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Dropping-Rows>`__
-  `Replace string characters in a column using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Replacing-String-Characters>`__
-  `Recast a column as a different data type in
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Recasting-Data>`__

.. code:: ipython3

    # clean NaN rows
    df1.dropna(inplace=True)
    
    # convert object type to float
    df1["price_usd"] = (
        df1["price_usd"]
        .str.replace("$", "", regex=False)
        .str.replace(",", "")
        .astype(float)
    )
    
    
    df1["price_usd"]




.. parsed-literal::

    0       67965.56
    1       63223.78
    2       84298.37
    3       94308.80
    5      105191.37
             ...    
    693    115910.26
    694     77572.89
    696    137017.34
    697    110404.35
    699     56637.97
    Name: price_usd, Length: 583, dtype: float64



Clean ``df2``
-------------

Now it’s time to tackle ``df2``. Take a moment to inspect it using the
same commands you used before. You’ll notice that it has the same issue
of ``NaN`` values, but there’s a new problem, too: The home prices are
in Mexican pesos (``"price_mxn"``), not US dollars (``"price_usd"``). If
we want to compare all the home prices in this dataset, they all need to
be in the same currency.

.. code:: ipython3

    VimeoVideo("656315668", h="c9bd116aca", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656315668?h=c9bd116aca"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.2.4:** First, drop rows with ``NaN`` values in ``df2``. Next,
use the ``"price_mxn"`` column to create a new column named
``"price_usd"``. (Keep in mind that, when this data was collected in
2014, a dollar cost 19 pesos.) Finally, drop the ``"price_mxn"`` from
the DataFrame.

-  `Drop rows with missing values from a DataFrame using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Dropping-Rows>`__
-  `Create new columns derived from existing columns in a DataFrame
   using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Adding-Columns>`__
-  `Drop a column from a DataFrame using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Dropping-Columns>`__

.. code:: ipython3

    df2.dropna(inplace=True)
    
    # exchange rate mxn to usd
    usd_mxn_fx = 19
    
    df2["price_usd"] = (df2["price_mxn"] / usd_mxn_fx).round(2)
    df2.drop(columns=["price_mxn"], inplace=True)
    df2




.. raw:: html

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
          <th>property_type</th>
          <th>state</th>
          <th>lat</th>
          <th>lon</th>
          <th>area_m2</th>
          <th>price_usd</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>apartment</td>
          <td>Nuevo León</td>
          <td>25.721081</td>
          <td>-100.345581</td>
          <td>72.0</td>
          <td>68421.05</td>
        </tr>
        <tr>
          <th>2</th>
          <td>house</td>
          <td>Morelos</td>
          <td>23.634501</td>
          <td>-102.552788</td>
          <td>360.0</td>
          <td>278947.37</td>
        </tr>
        <tr>
          <th>6</th>
          <td>apartment</td>
          <td>Estado de México</td>
          <td>19.272040</td>
          <td>-99.572013</td>
          <td>85.0</td>
          <td>65789.47</td>
        </tr>
        <tr>
          <th>7</th>
          <td>house</td>
          <td>San Luis Potosí</td>
          <td>22.138882</td>
          <td>-100.996510</td>
          <td>158.0</td>
          <td>111578.95</td>
        </tr>
        <tr>
          <th>8</th>
          <td>apartment</td>
          <td>Distrito Federal</td>
          <td>19.394558</td>
          <td>-99.129707</td>
          <td>65.0</td>
          <td>39904.74</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>695</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.917542</td>
          <td>-98.963181</td>
          <td>140.0</td>
          <td>76315.79</td>
        </tr>
        <tr>
          <th>696</th>
          <td>house</td>
          <td>Distrito Federal</td>
          <td>19.472128</td>
          <td>-99.146697</td>
          <td>190.0</td>
          <td>102263.16</td>
        </tr>
        <tr>
          <th>697</th>
          <td>house</td>
          <td>Estado de México</td>
          <td>19.234984</td>
          <td>-99.558175</td>
          <td>115.0</td>
          <td>110526.32</td>
        </tr>
        <tr>
          <th>698</th>
          <td>house</td>
          <td>Puebla</td>
          <td>18.918714</td>
          <td>-98.426639</td>
          <td>90.0</td>
          <td>46842.11</td>
        </tr>
        <tr>
          <th>699</th>
          <td>house</td>
          <td>Yucatán</td>
          <td>21.075163</td>
          <td>-89.516731</td>
          <td>185.0</td>
          <td>89210.53</td>
        </tr>
      </tbody>
    </table>
    <p>571 rows × 6 columns</p>
    </div>



.. code:: ipython3

    df2.info()


.. parsed-literal::

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 571 entries, 0 to 699
    Data columns (total 6 columns):
     #   Column         Non-Null Count  Dtype  
    ---  ------         --------------  -----  
     0   property_type  571 non-null    object 
     1   state          571 non-null    object 
     2   lat            571 non-null    float64
     3   lon            571 non-null    float64
     4   area_m2        571 non-null    float64
     5   price_usd      571 non-null    float64
    dtypes: float64(4), object(2)
    memory usage: 31.2+ KB


Clean ``df3``
-------------

Great work! We’re now on the final DataFrame. Use the same ``shape``,
``info`` and ``head`` commands to inspect the ``df3``. Do you see any
familiar issues?

You’ll notice that we still have ``NaN`` values, but there are two new
problems:

1. Instead of separate ``"lat"`` and ``"lon"`` columns, there’s a single
   ``"lat-lon"`` column.
2. Instead of a ``"state"`` column, there’s a
   ``"place_with_parent_names"`` column.

We need the resolve these problems so that ``df3`` has the same columns
in the same format as ``df1`` and ``df2``.

.. code:: ipython3

    VimeoVideo("656314718", h="8d1127a93f", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656314718?h=8d1127a93f"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.2.5:** Drop rows with ``NaN`` values in ``df3``. Then use the
```split`` <https://pandas.pydata.org/docs/reference/api/pandas.Series.str.split.html>`__
method to create two new columns from ``"lat-lon"`` named ``"lat"`` and
``"lon"``, respectively.

-  `Drop rows with missing values from a DataFrame using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Dropping-Rows>`__
-  `Split the strings in one column to create another using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Splitting-Strings>`__

.. code:: ipython3

    df3.dropna(inplace=True)
    # split lat/lon first, then drop NaN
    df3[["lat", "lon"]] = df3["lat-lon"].str.split(",", expand=True)
    df3.head()
    # lat, lon = df3["lat-lon"].str.split(",")[0], df3["lat-lon"].str.split(",")[1]





.. raw:: html

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
          <th>property_type</th>
          <th>place_with_parent_names</th>
          <th>lat-lon</th>
          <th>area_m2</th>
          <th>price_usd</th>
          <th>lat</th>
          <th>lon</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>apartment</td>
          <td>|México|Distrito Federal|Gustavo A. Madero|Acu...</td>
          <td>19.52589,-99.151703</td>
          <td>71.0</td>
          <td>48550.59</td>
          <td>19.52589</td>
          <td>-99.151703</td>
        </tr>
        <tr>
          <th>1</th>
          <td>house</td>
          <td>|México|Estado de México|Toluca|Metepec|</td>
          <td>19.2640539,-99.5727534</td>
          <td>233.0</td>
          <td>168636.73</td>
          <td>19.2640539</td>
          <td>-99.5727534</td>
        </tr>
        <tr>
          <th>2</th>
          <td>house</td>
          <td>|México|Estado de México|Toluca|Toluca de Lerd...</td>
          <td>19.268629,-99.671722</td>
          <td>300.0</td>
          <td>86932.69</td>
          <td>19.268629</td>
          <td>-99.671722</td>
        </tr>
        <tr>
          <th>4</th>
          <td>apartment</td>
          <td>|México|Veracruz de Ignacio de la Llave|Veracruz|</td>
          <td>19.511938,-96.871956</td>
          <td>84.0</td>
          <td>68508.67</td>
          <td>19.511938</td>
          <td>-96.871956</td>
        </tr>
        <tr>
          <th>5</th>
          <td>house</td>
          <td>|México|Jalisco|Guadalajara|</td>
          <td>20.689157,-103.366728</td>
          <td>175.0</td>
          <td>102763.00</td>
          <td>20.689157</td>
          <td>-103.366728</td>
        </tr>
      </tbody>
    </table>
    </div>



.. code:: ipython3

    df3.info()


.. parsed-literal::

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 582 entries, 0 to 699
    Data columns (total 7 columns):
     #   Column                   Non-Null Count  Dtype  
    ---  ------                   --------------  -----  
     0   property_type            582 non-null    object 
     1   place_with_parent_names  582 non-null    object 
     2   lat-lon                  582 non-null    object 
     3   area_m2                  582 non-null    float64
     4   price_usd                582 non-null    float64
     5   lat                      582 non-null    object 
     6   lon                      582 non-null    object 
    dtypes: float64(2), object(5)
    memory usage: 36.4+ KB


.. code:: ipython3

    VimeoVideo("656314050", h="13f6a677fd", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656314050?h=13f6a677fd"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.2.6:** Use the
```split`` <https://pandas.pydata.org/docs/reference/api/pandas.Series.str.split.html>`__
method again, this time to extract the state for every house. (Note that
the state name always appears after ``"México|"`` in each string.) Use
this information to create a ``"state"`` column. Finally, drop the
``"place_with_parent_names"`` and ``"lat-lon"`` columns from the
DataFrame.

-  `Split the strings in one column to create another using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Splitting-Strings>`__
-  `Drop a column from a DataFrame using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Dropping-Columns>`__

.. code:: ipython3

    df3["state"] = df3["place_with_parent_names"].str.split("|", expand=True)[2].head()
    df3.drop(columns=["place_with_parent_names", "lat-lon"], inplace=True)
    df3.head()




.. raw:: html

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
          <th>property_type</th>
          <th>area_m2</th>
          <th>price_usd</th>
          <th>lat</th>
          <th>lon</th>
          <th>state</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>apartment</td>
          <td>71.0</td>
          <td>48550.59</td>
          <td>19.52589</td>
          <td>-99.151703</td>
          <td>Distrito Federal</td>
        </tr>
        <tr>
          <th>1</th>
          <td>house</td>
          <td>233.0</td>
          <td>168636.73</td>
          <td>19.2640539</td>
          <td>-99.5727534</td>
          <td>Estado de México</td>
        </tr>
        <tr>
          <th>2</th>
          <td>house</td>
          <td>300.0</td>
          <td>86932.69</td>
          <td>19.268629</td>
          <td>-99.671722</td>
          <td>Estado de México</td>
        </tr>
        <tr>
          <th>4</th>
          <td>apartment</td>
          <td>84.0</td>
          <td>68508.67</td>
          <td>19.511938</td>
          <td>-96.871956</td>
          <td>Veracruz de Ignacio de la Llave</td>
        </tr>
        <tr>
          <th>5</th>
          <td>house</td>
          <td>175.0</td>
          <td>102763.00</td>
          <td>20.689157</td>
          <td>-103.366728</td>
          <td>Jalisco</td>
        </tr>
      </tbody>
    </table>
    </div>



Concatenate DataFrames
----------------------

Great work! You have three clean DataFrames, and now it’s time to
combine them into a single DataFrame so that you can conduct your
analysis.

.. code:: ipython3

    VimeoVideo("656313395", h="ccadbc2689", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656313395?h=ccadbc2689"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.2.7:** Use
```pd.concat`` <https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.concat.html>`__
to concatenate ``df1``, ``df2``, ``df3`` as new DataFrame named ``df``.
Your new DataFrame should have 1,736 rows and 6
columns:``"property_type"``, ``"state"``, ``"lat"``, ``"lon"``,
``"area_m2"``, ``"price_usd"``, and ``"price_per_m2"``.

-  `Concatenate two or more DataFrames using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Concatenating-DataFrames>`__

.. code:: ipython3

    df = pd.concat([df1, df2, df3])
    print(df.shape)
    df.head()


.. parsed-literal::

    (1736, 6)




.. raw:: html

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
          <th>property_type</th>
          <th>state</th>
          <th>lat</th>
          <th>lon</th>
          <th>area_m2</th>
          <th>price_usd</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>house</td>
          <td>Estado de México</td>
          <td>19.560181</td>
          <td>-99.233528</td>
          <td>150.0</td>
          <td>67965.56</td>
        </tr>
        <tr>
          <th>1</th>
          <td>house</td>
          <td>Nuevo León</td>
          <td>25.688436</td>
          <td>-100.198807</td>
          <td>186.0</td>
          <td>63223.78</td>
        </tr>
        <tr>
          <th>2</th>
          <td>apartment</td>
          <td>Guerrero</td>
          <td>16.767704</td>
          <td>-99.764383</td>
          <td>82.0</td>
          <td>84298.37</td>
        </tr>
        <tr>
          <th>3</th>
          <td>apartment</td>
          <td>Guerrero</td>
          <td>16.829782</td>
          <td>-99.911012</td>
          <td>150.0</td>
          <td>94308.80</td>
        </tr>
        <tr>
          <th>5</th>
          <td>house</td>
          <td>Yucatán</td>
          <td>21.052583</td>
          <td>-89.538639</td>
          <td>205.0</td>
          <td>105191.37</td>
        </tr>
      </tbody>
    </table>
    </div>



Save ``df``
-----------

The data is clean and in a single DataFrame, and now you need to save it
as a CSV file so that you can examine it in your exploratory data
analysis.

.. code:: ipython3

    VimeoVideo("656312464", h="81ee04de15", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656312464?h=81ee04de15"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.2.8:** Save ``df`` as a CSV file using the
```to_csv`` <https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html>`__
method. The file path should be
``"./data/mexico-real-estate-clean.csv"``. Be sure to set the ``index``
argument to ``False``.

-  `What’s a CSV
   file? <../%40textbook/03-pandas-getting-started.ipynb#CSV-Files>`__
-  `Save a DataFrame as a CSV file using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Saving-a-DataFrame-as-a-CSV>`__

.. code:: ipython3

    df.to_csv("./data/mexico-re-data.csv", index=False)

--------------

Copyright © 2022 WorldQuant University. This content is licensed solely
for personal use. Redistribution or publication of this material is
strictly prohibited.
