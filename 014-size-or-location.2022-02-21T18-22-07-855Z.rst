Location or Size: What Influences House Prices in Mexico?

.. code:: ipython3

    import matplotlib.pyplot as plt
    import pandas as pd
    from IPython.display import VimeoVideo

You’ve wrangled the data, you’ve gained an understanding of its basic
characteristics in your EDA, and now it’s time to ask some research
questions.

Import Data
===========

**Task 1.4.1:** Read the CSV file that you created in the last notebook
(``"../small-data/mexico-real-estate-clean.csv"``) into a DataFrame
named ``df``. Be sure to check that all your columns are the correct
data type before you go to the next task.

-  `What’s a
   DataFrame? <../%40textbook/03-pandas-getting-started.ipynb#Working-with-DataFrames>`__
-  `What’s a CSV
   file? <../%40textbook/03-pandas-getting-started.ipynb#CSV-Files>`__
-  `Read a CSV file into a DataFrame using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Working-with-DataFrames>`__

.. code:: ipython3

    df = pd.read_csv("./data/mexico-re-data.csv")
    df




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
          <th>4</th>
          <td>house</td>
          <td>Yucatán</td>
          <td>21.052583</td>
          <td>-89.538639</td>
          <td>205.0</td>
          <td>105191.37</td>
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
          <th>1731</th>
          <td>house</td>
          <td>NaN</td>
          <td>20.532264</td>
          <td>-103.484418</td>
          <td>175.0</td>
          <td>121178.91</td>
        </tr>
        <tr>
          <th>1732</th>
          <td>house</td>
          <td>NaN</td>
          <td>18.928986</td>
          <td>-99.180215</td>
          <td>100.0</td>
          <td>47417.83</td>
        </tr>
        <tr>
          <th>1733</th>
          <td>house</td>
          <td>NaN</td>
          <td>21.028404</td>
          <td>-89.653006</td>
          <td>81.0</td>
          <td>39524.23</td>
        </tr>
        <tr>
          <th>1734</th>
          <td>house</td>
          <td>NaN</td>
          <td>22.118304</td>
          <td>-101.032194</td>
          <td>360.0</td>
          <td>245050.24</td>
        </tr>
        <tr>
          <th>1735</th>
          <td>house</td>
          <td>NaN</td>
          <td>19.233201</td>
          <td>-99.558519</td>
          <td>115.0</td>
          <td>110667.85</td>
        </tr>
      </tbody>
    </table>
    <p>1736 rows × 6 columns</p>
    </div>



Research Question 1
===================

**Which state has the most expensive real estate market?**

Do housing prices vary by state? If so, which are the most expensive
states for purchasing a home? During our exploratory data analysis, we
used descriptive statistics like mean and median to get an idea of the
“typical” house price in Mexico. Now, we need to break that calculation
down by state and visualize the results.

We know in which state each house is located thanks to the ``"state"``
column. The next step is to divide our dataset into groups (one per
state) and calculate the mean house price for each group.

.. code:: ipython3

    VimeoVideo("656378731", h="8daa35d1e8", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656378731?h=8daa35d1e8"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.2:** Use the
```groupby`` <https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html>`__
method to create a Series named ``mean_price_by_state``, where the index
contains each state in the dataset and the values correspond to the mean
house price for that state. Make sure your Series is sorted from highest
to lowest mean price.

-  `What’s a
   Series? <../%40textbook/05-pandas-summary-statistics.ipynb#Series>`__
-  `Aggregate data using the ``groupby`` method in
   pandas. <../%40textbook/04-pandas-advanced.ipynb#Series-and-Groupby>`__

.. code:: ipython3

    mean_price_by_state = df.groupby("state")["price_usd"].mean().sort_values(ascending=False)
    mean_price_by_state




.. parsed-literal::

    state
    Querétaro                          141521.234079
    Guanajuato                         138934.256000
    Distrito Federal                   137502.272525
    Chihuahua                          132085.373333
    Quintana Roo                       130142.436400
    Estado de México                   124329.215766
    Puebla                             123336.021781
    Guerrero                           115691.668919
    Nuevo León                         112529.309623
    Jalisco                            110828.913415
    Sonora                             109995.920000
    Yucatán                            109715.606462
    Morelos                            108134.703196
    Aguascalientes                     104197.078750
    Chiapas                            103286.501562
    Baja California Sur                 97075.972500
    Hidalgo                             95241.989167
    Tamaulipas                          94822.754865
    Veracruz de Ignacio de la Llave     93383.069125
    Sinaloa                             92547.207778
    San Luis Potosí                     83595.254872
    Durango                             83590.000000
    Tlaxcala                            80340.822000
    Nayarit                             77654.416250
    Zacatecas                           76395.400000
    Baja California                     65993.726842
    Tabasco                             63247.572857
    Colima                              63157.890000
    Name: price_usd, dtype: float64



.. code:: ipython3

    VimeoVideo("656378435", h="b3765f3339", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656378435?h=b3765f3339"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.3:** Use ``mean_price_by_state`` to create a bar chart of
your results. Make sure the states are sorted from the highest to lowest
mean, that you label the x-axis as ``"State"`` and the y-axis as
``"Mean Price [USD]"``, and give the chart the title
``"Mean House Price by State"``.

-  `Create a bar chart using
   pandas. <../%40textbook/06-visualization-matplotlib.ipynb#Bar-Charts>`__

.. code:: ipython3

    mean_price_by_state.plot(
        kind="bar",
        xlabel="State",
        ylabel="Price[USD]",
        title="Mean House Price by State"
    );



.. image:: output_14_0.png


It seems odd that Querétaro would be the most expensive real estate
market in Mexico when, `according to recent GDP
numbers <https://en.wikipedia.org/wiki/List_of_Mexican_states_by_GDP>`__,
it’s not in the top 10 state economies. With all the variations in house
sizes across states, a better metric to look at would be price per m2.
In order to do that, we need to create a new column.

.. code:: ipython3

    VimeoVideo("656378342", h="2f4da7f7b4", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656378342?h=2f4da7f7b4"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.4:** Create a new column in ``df`` called ``"price_per_m2"``.
This should be the price for each house divided by it’s size.

-  `Create new columns derived from existing columns in a DataFrame
   using
   pandas. <../%40textbook/03-pandas-getting-started.ipynb#Working-with-Columns>`__

.. code:: ipython3

    df["price_per_m2"] = df["price_usd"]/df["area_m2"]
    df.head()




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
          <th>price_per_m2</th>
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
          <td>453.103733</td>
        </tr>
        <tr>
          <th>1</th>
          <td>house</td>
          <td>Nuevo León</td>
          <td>25.688436</td>
          <td>-100.198807</td>
          <td>186.0</td>
          <td>63223.78</td>
          <td>339.912796</td>
        </tr>
        <tr>
          <th>2</th>
          <td>apartment</td>
          <td>Guerrero</td>
          <td>16.767704</td>
          <td>-99.764383</td>
          <td>82.0</td>
          <td>84298.37</td>
          <td>1028.028902</td>
        </tr>
        <tr>
          <th>3</th>
          <td>apartment</td>
          <td>Guerrero</td>
          <td>16.829782</td>
          <td>-99.911012</td>
          <td>150.0</td>
          <td>94308.80</td>
          <td>628.725333</td>
        </tr>
        <tr>
          <th>4</th>
          <td>house</td>
          <td>Yucatán</td>
          <td>21.052583</td>
          <td>-89.538639</td>
          <td>205.0</td>
          <td>105191.37</td>
          <td>513.128634</td>
        </tr>
      </tbody>
    </table>
    </div>



Let’s redo our bar chart from above, but this time with the mean of
``"price_per_m2"`` for each state.

.. code:: ipython3

    VimeoVideo("656377991", h="c7319b0458", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656377991?h=c7319b0458"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.5:** First, use the
```groupby`` <https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html>`__
method to create a Series where the index contains each state in the
dataset and the values correspond to the mean house price per m2 for
that state. Then use the Series to create a bar chart of your results.
Make sure the states are sorted from the highest to lowest mean, that
you label the x-axis as ``"State"`` and the y-axis as
``"Mean Price per M^2[USD]"``, and give the chart the title
``"Mean House Price per M^2 by State"``.

-  `What’s a
   Series? <../%40textbook/05-pandas-summary-statistics.ipynb#Series>`__
-  `Aggregate data using the ``groupby`` method in
   pandas. <../%40textbook/04-pandas-advanced.ipynb#Series-and-Groupby>`__
-  `Create a bar chart using
   pandas. <../%40textbook/06-visualization-matplotlib.ipynb#Bar-Charts>`__

.. code:: ipython3

    df.groupby("state")["price_per_m2"].mean().sort_values(ascending=False).plot(
        kind="bar",
        xlabel="State",
        ylabel="Mean Price per M^2[USD]",
        title="Mean House Price per M^2 by State"
    );



.. image:: output_22_0.png


Now we see that the capital Mexico City (*Distrito Federal*) is by far
the most expensive market. Additionally, many of the top 10 states by
GDP are also in the top 10 most expensive real estate markets. So it
looks like this bar chart is a more accurate reflection of state real
estate markets.

Research Question 2
===================

**Is there a relationship between home size and price?**

From our previous question, we know that the location of a home affects
its price (especially if it’s in Mexico City), but what about home size?
Does the size of a house influence price?

A scatter plot can be helpful when evaluating the relationship between
two columns because it lets you see if two variables are correlated — in
this case, if an increase in home size is associated with an increase in
price.

.. code:: ipython3

    VimeoVideo("656377758", h="62546c7b86", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656377758?h=62546c7b86"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.6:** Create a scatter plot from ``df`` that represents price
as a function of size. In other words, ``"area_m2"`` should be on the
x-axis, and ``"price_usd"`` should be on the y-axis. Be sure to use
expressive axis labels (``"Area [sq meters]"`` and ``"Price [USD]"``,
respectively).

-  `What’s a scatter
   plot? <../%40textbook/06-visualization-matplotlib.ipynb#Scatter-Plots>`__
-  `What’s
   correlation? <../%40textbook/05-pandas-summary-statistics.ipynb#Correlations>`__
-  `Create a scatter plot using
   Matplotlib. <../%40textbook/06-visualization-matplotlib.ipynb#Scatter-Plots>`__

.. code:: ipython3

    plt.scatter(x=df["area_m2"], y=df["price_usd"]);
    plt.xlabel("Area [sq meters]")
    plt.ylabel("Price [USD]")
    plt.title("Price vs. Area")




.. parsed-literal::

    Text(0.5, 1.0, 'Price vs. Area')




.. image:: output_29_1.png


While there’s a good amount of variation, there’s definitely a positive
correlation — in other words, the bigger the house, the higher the
price. But how can we quantify this correlation?

.. code:: ipython3

    VimeoVideo("656377616", h="8d3b060e71", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656377616?h=8d3b060e71"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.7:** Using the
```corr`` <https://pandas.pydata.org/docs/reference/api/pandas.Series.corr.html>`__
method, calculate the Pearson correlation coefficient for ``"area_m2"``
and ``"price_usd"``.

-  `What’s a correlation
   coefficient? <../%40textbook/05-pandas-summary-statistics.ipynb#Correlations>`__
-  `Calculate the correlation coefficient for two Series using
   pandas. <../%40textbook/05-pandas-summary-statistics.ipynb#Correlations>`__

.. code:: ipython3

    p_correlation = df["area_m2"].corr(df["price_usd"])
    print(p_correlation)


.. parsed-literal::

    0.5855182453232062


The correlation coefficient is over 0.5, so there’s a moderate
relationship house size and price in Mexico. But does this relationship
hold true in every state? Let’s look at a couple of states, starting
with Morelos.

.. code:: ipython3

    VimeoVideo("656377515", h="d2478d38df", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656377515?h=d2478d38df"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.8:** Create a new DataFrame named ``df_morelos``. It should
include all the houses from ``df`` that are in the state of Morelos.

-  `Subset a DataFrame with a mask using
   pandas. <../%40textbook/04-pandas-advanced.ipynb#Subsetting-with-Masks>`__

.. code:: ipython3

    df_morelos = df[df["state"] == "Morelos"]
    df_morelos




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
          <th>price_per_m2</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>6</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.812605</td>
          <td>-98.954826</td>
          <td>281.0</td>
          <td>151509.56</td>
          <td>539.179929</td>
        </tr>
        <tr>
          <th>9</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.804197</td>
          <td>-98.932816</td>
          <td>117.0</td>
          <td>63223.78</td>
          <td>540.374188</td>
        </tr>
        <tr>
          <th>18</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.855343</td>
          <td>-99.241142</td>
          <td>73.0</td>
          <td>36775.16</td>
          <td>503.769315</td>
        </tr>
        <tr>
          <th>49</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.804197</td>
          <td>-98.932816</td>
          <td>130.0</td>
          <td>65858.10</td>
          <td>506.600769</td>
        </tr>
        <tr>
          <th>55</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.960244</td>
          <td>-99.212962</td>
          <td>305.0</td>
          <td>227351.46</td>
          <td>745.414623</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>1109</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.840925</td>
          <td>-98.934196</td>
          <td>110.0</td>
          <td>94736.84</td>
          <td>861.244000</td>
        </tr>
        <tr>
          <th>1118</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.795519</td>
          <td>-99.231445</td>
          <td>165.0</td>
          <td>93684.21</td>
          <td>567.783091</td>
        </tr>
        <tr>
          <th>1119</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.885848</td>
          <td>-98.973834</td>
          <td>82.0</td>
          <td>75694.74</td>
          <td>923.106585</td>
        </tr>
        <tr>
          <th>1142</th>
          <td>house</td>
          <td>Morelos</td>
          <td>23.634501</td>
          <td>-102.552788</td>
          <td>110.0</td>
          <td>68421.05</td>
          <td>622.009545</td>
        </tr>
        <tr>
          <th>1149</th>
          <td>house</td>
          <td>Morelos</td>
          <td>18.917542</td>
          <td>-98.963181</td>
          <td>140.0</td>
          <td>76315.79</td>
          <td>545.112786</td>
        </tr>
      </tbody>
    </table>
    <p>97 rows × 7 columns</p>
    </div>



.. code:: ipython3

    VimeoVideo("656377395", h="bd93b05ff9", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656377395?h=bd93b05ff9"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.9:** Using ``df_morelos``, create a scatter plot that shows
price vs area. Make sure to use the same axis labels as your last
scatter plot. The title should be ``"Morelos: Price vs. Area"``.

-  `What’s a scatter
   plot? <../%40textbook/06-visualization-matplotlib.ipynb#Scatter-Plots>`__
-  `Create a scatter plot using
   Matplotlib. <../%40textbook/06-visualization-matplotlib.ipynb#Scatter-Plots>`__

.. code:: ipython3

    plt.scatter(x=df_morelos["area_m2"], y=df_morelos["price_usd"])
    plt.xlabel("Area [sq meters]")
    plt.ylabel("Price [USD]")
    plt.title("Morelos: Price vs. Area");



.. image:: output_40_0.png


Wow! It looks like the correlation is even stronger within Morelos.
Let’s calculate the correlation coefficient and verify that that’s the
case.

.. code:: ipython3

    VimeoVideo("656377340", h="664cb44291", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656377340?h=664cb44291"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.10:** Using the
```corr`` <https://pandas.pydata.org/docs/reference/api/pandas.Series.corr.html>`__
method, calculate the Pearson correlation coefficient for ``"area_m2"``
and ``"price_usd"`` in ``df_morelos``.

-  `What’s a correlation
   coefficient? <../%40textbook/05-pandas-summary-statistics.ipynb#Correlations>`__
-  `Calculate the correlation coefficient for two Series using
   pandas. <../%40textbook/05-pandas-summary-statistics.ipynb#Correlations>`__

.. code:: ipython3

    p_correlation = df_morelos["area_m2"].corr(df_morelos["price_usd"])
    print(p_correlation)


.. parsed-literal::

    0.8725659056131556


With a correlation coefficient that high, we can say that there’s a
strong relationship between house size and price in Morelos.

To conclude, let’s look at the capital Mexico City (*Distrito Federal*).

.. code:: ipython3

    VimeoVideo("656376911", h="19666a4c87", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656376911?h=19666a4c87"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.4.11:** First, create a new DataFrame called ``df_mexico_city``
that includes all the observations from ``df`` that are part of the
*Distrito Federal*. Next, create a scatter plot that shows price vs
area. Don’t forget to label the x- and y-axis and use the title
``"Mexico City: Price vs. Area"``. Finally, calculate the correlation
coefficient for ``"area_m2"`` and ``"price_usd"`` in ``df_mexico_city``.

-  `Calculate the correlation coefficient for two Series using
   pandas. <../%40textbook/05-pandas-summary-statistics.ipynb#Correlations>`__
-  `Create a scatter plot using
   Matplotlib. <../%40textbook/06-visualization-matplotlib.ipynb#Scatter-Plots>`__
-  `Subset a DataFrame with a mask using
   pandas. <../%40textbook/04-pandas-advanced.ipynb#Subsetting-with-Masks>`__

.. code:: ipython3

    # Subset `df` to include only observations from `"Distrito Federal"`
    df_mexico_city = df[df["state"] == "Distrito Federal"]
    df_mexico_city
    
    # Create a scatter plot price vs area
    plt.scatter(x=df_mexico_city["area_m2"], y=df_mexico_city["price_usd"]);
    plt.xlabel("Area [sq meters]")
    plt.ylabel("Price [USD]")
    plt.xlabel("Mexico City: Price vs. Area")
    
    p_correlation = df_mexico_city["area_m2"].corr(df_mexico_city["price_usd"])
    print(p_correlation)


.. parsed-literal::

    0.34631963237093566



.. image:: output_48_1.png


Looking at the scatter plot and correlation coefficient, there’s see a
weak relationship between size and price. How should we interpret this?

One interpretation is that the relationship we see between size and
price in many states doesn’t hold true in the country’s biggest and most
economically powerful urban center because there are other factors that
have a larger influence on price. In fact, in the next project, we’re
going to look at another important Latin American city — Buenos Aires,
Argentina — and build a model that predicts housing price by taking much
more than size into account.

--------------

Copyright © 2022 WorldQuant University. This content is licensed solely
for personal use. Redistribution or publication of this material is
strictly prohibited.
