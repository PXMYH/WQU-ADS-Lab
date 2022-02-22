.. code:: ipython3

    # WELCOME THE FIRST LESSON OF PROJECT 1!
    #
    # If you haven't watched the virtual machine orientation video yet,
    # 👆 Click the ▶️ button above to get started.
    
    from IPython.display import VimeoVideo
    
    VimeoVideo("656189257", h="3298dbabb7", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/656189257?h=3298dbabb7"
        frameborder="0"
        allowfullscreen
    ></iframe>




1.1 Organizing Tabular Data in Python

.. code:: ipython3

    from IPython.display import VimeoVideo

What’s Tabular Data?
====================

.. code:: ipython3

    VimeoVideo("645390762", h="578b5a9e19", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645390762?h=578b5a9e19"
        frameborder="0"
        allowfullscreen
    ></iframe>




Information can come in many forms, and part of a data scientist’s job
is making sure that information is organized in a way that’s conducive
to analysis. Take for example these five houses from the Mexico real
estate dataset we’ll use in this project:

.. figure:: ../images/proj-1.001.png
   :alt: Five houses showing price, number of rooms, and area in square
   meters for each

   Five houses showing price, number of rooms, and area in square meters
   for each

One common way to organize this information is in a **table**, which is
a group of **cells** organized into **rows** and **columns**:

.. figure:: ../images/proj-1.002.png
   :alt: Table, organized into rows and columns, with housing
   information from previous image

   Table, organized into rows and columns, with housing information from
   previous image

When working with this sort of **tabular data**, it’s important to
organize row and columns following the principles of “`tidy
data <https://en.wikipedia.org/wiki/Tidy_data>`__.” What does that mean
in the case of our dataset?

1. Each row corresponds to a single house in our dataset. We’ll call
   each of these houses an **observation**.
2. Each column corresponds to a characteristic of each house. We’ll call
   these **features**.
3. Each cell contains only one **value**.

.. figure:: ../images/proj-1.003.png
   :alt: Three copies of table from previous image, emphasizing
   observations as rows and features as columns

   Three copies of table from previous image, emphasizing observations
   as rows and features as columns

So whenever you encounter a new dataset, make sure your data is “tidy.”
``NOTE: need to add activity here``

Tabular Data and Python Data Structures
=======================================

Working with Lists
------------------

Python comes with several data structures that we can use to organize
tabular data. Let’s start by putting a single observation in a **list**.

.. code:: ipython3

    house_0_list = [115910.26, 128, 4]
    house_0_list




.. parsed-literal::

    [115910.26, 128, 4]



.. code:: ipython3

    VimeoVideo("645390786", h="da0bb831d1", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645390786?h=da0bb831d1"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.1.1:** One metric that people in the real estate industry look
at is price per square meter because it allows them to compare houses of
different sizes. Can you use the information in this list to calculate
the price per square meter for ``house_0``?

-  `What’s a
   list? <../%40textbook/01-python-getting-started.ipynb#Lists>`__
-  `Access an item in a list using
   Python. <../%40textbook/01-python-getting-started.ipynb#Working-with-Lists>`__
-  `Perform basic mathematical operations in
   Python. <../%40textbook/01-python-getting-started.ipynb#Simple-Calculations>`__

.. code:: ipython3

    house_0_price_m2 = house_0_list[0] / house_0_list[1]
    house_0_price_m2




.. parsed-literal::

    905.54890625



.. code:: ipython3

    VimeoVideo("645390797", h="86c579a9cb", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645390797?h=86c579a9cb"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.1.2:** Next, use the
```append`` <https://docs.python.org/3/tutorial/datastructures.html#more-on-lists>`__
method to add the price per square meter to the end of the end of
``house_0``.

-  `Append an item to a list in
   Python. <../%40textbook/01-python-getting-started.ipynb#Appending-Items>`__

.. code:: ipython3

    house_0_list.append(house_0_price_m2)
    house_0_list




.. parsed-literal::

    [115910.26, 128, 4, 905.54890625]



Now that you can work with data for a single house, let’s think about
how to organize the whole dataset. One option would be to create a list
for each observation and then put those together in another list. This
is called a `nested
list <http://127.0.0.1:8888/lab/tree/work/ds_curriculum/%40textbook/Python.ipynb#creating-lists>`__.

.. code:: ipython3

    houses_nested_list = [
        [115910.26, 128.0, 4.0],
        [48718.17, 210.0, 3.0],
        [28977.56, 58.0, 2.0],
        [36932.27, 79.0, 3.0],
        [83903.51, 111.0, 3.0],
    ]
    
    houses_nested_list




.. parsed-literal::

    [[115910.26, 128.0, 4.0],
     [48718.17, 210.0, 3.0],
     [28977.56, 58.0, 2.0],
     [36932.27, 79.0, 3.0],
     [83903.51, 111.0, 3.0]]



Now that we have more observations, it doesn’t make sense to calculate
the price per square meter for each house one-by-one. Instead, we can
automate this repetitive task using a ``for`` loop.

.. code:: ipython3

    VimeoVideo("645390807", h="4536120cf5", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645390807?h=4536120cf5"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.1.3:** Append the price per square meter to each observation in
``houses_nested_list`` using a ``for`` loop.

-  `What’s a for
   loop? <../%40textbook/01-python-getting-started.ipynb#Python-for-Loops>`__
-  `Write a for loop in
   Python. <../%40textbook/01-python-getting-started.ipynb#Working-with-for-Loops>`__

.. code:: ipython3

    for house in houses_nested_list:
        house.append(house[0]/house[1])
    houses_nested_list




.. parsed-literal::

    [[115910.26, 128.0, 4.0, 905.54890625],
     [48718.17, 210.0, 3.0, 231.9912857142857],
     [28977.56, 58.0, 2.0, 499.61310344827587],
     [36932.27, 79.0, 3.0, 467.4970886075949],
     [83903.51, 111.0, 3.0, 755.8874774774774]]



Working with Dictionaries
-------------------------

Lists are a good way to organize data, but one drawback is that we can
only represent values. Why is that a problem? For example, someone
looking at ``[115910.26, 128.0, 4]`` wouldn’t know which values
corresponded to price, area, etc. A better option might be a
`dictionary <http://127.0.0.1:8888/lab/tree/work/ds_curriculum/%40textbook/Python.ipynb#whats-a-dictionary>`__,
where each value is associated with a key. Here’s what ``house_0`` looks
like as a dictionary instead of a list.

.. code:: ipython3

    house_0_dict = {
        "price_aprox_usd": 115910.26,
        "surface_covered_in_m2": 128,
        "rooms": 4,
    }
    
    house_0_dict




.. parsed-literal::

    {'price_aprox_usd': 115910.26, 'surface_covered_in_m2': 128, 'rooms': 4}



.. code:: ipython3

    VimeoVideo("645390821", h="884613d46b", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645390821?h=884613d46b"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.1.4:** Calculate the price per square meter for ``house_0`` and
add it to the dictionary under the key ``"price_per_m2"``.

-  `What’s a
   dictionary? <../%40textbook/01-python-getting-started.ipynb#Python-Dictionaries>`__
-  `Access an item in a dictionary in
   Python. <../%40textbook/01-python-getting-started.ipynb#Working-with-Dictionaries>`__

.. code:: ipython3

    house_0_dict["price_per_m2"] = house_0_dict["price_aprox_usd"] / house_0_dict["surface_covered_in_m2"]
    house_0_dict




.. parsed-literal::

    {'price_aprox_usd': 115910.26,
     'surface_covered_in_m2': 128,
     'rooms': 4,
     'price_per_m2': 905.54890625}



If we wanted to combine all our observations together, the best way
would be to create a list of dictionaries.

.. code:: ipython3

    houses_rowwise = [
        {
            "price_aprox_usd": 115910.26,
            "surface_covered_in_m2": 128,
            "rooms": 4,
        },
        {
            "price_aprox_usd": 48718.17,
            "surface_covered_in_m2": 210,
            "rooms": 3,
        },
        {
            "price_aprox_usd": 28977.56,
            "surface_covered_in_m2": 58,
            "rooms": 2,
        },
        {
            "price_aprox_usd": 36932.27,
            "surface_covered_in_m2": 79,
            "rooms": 3,
        },
        {
            "price_aprox_usd": 83903.51,
            "surface_covered_in_m2": 111,
            "rooms": 3,
        },
    ]
    
    houses_rowwise




.. parsed-literal::

    [{'price_aprox_usd': 115910.26, 'surface_covered_in_m2': 128, 'rooms': 4},
     {'price_aprox_usd': 48718.17, 'surface_covered_in_m2': 210, 'rooms': 3},
     {'price_aprox_usd': 28977.56, 'surface_covered_in_m2': 58, 'rooms': 2},
     {'price_aprox_usd': 36932.27, 'surface_covered_in_m2': 79, 'rooms': 3},
     {'price_aprox_usd': 83903.51, 'surface_covered_in_m2': 111, 'rooms': 3}]



This way of storing data is so popular, it has its own name:
`JSON <http://127.0.0.1:8888/lab/tree/work/ds_curriculum/%40textbook/Python.ipynb#JSON>`__.
We’ll learn more about it later in the course. For now, let’s build
another for loop, but this time, we’ll add a add the price per square
meter to each dictionary.

.. code:: ipython3

    VimeoVideo("645390833", h="0d3963c0d0", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645390833?h=0d3963c0d0"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.1.5:** Using a ``for`` loop, calculate the price per square
meter and store the result under a ``"price_per_m2"`` key for each
observation in ``houses_rowwise``.

-  `What’s
   JSON? <../%40textbook/01-python-getting-started.ipynb#JSON>`__
-  `Write a for loop in
   Python. <../%40textbook/01-python-getting-started.ipynb#Working-with-for-Loops>`__

.. code:: ipython3

    for house in houses_rowwise:
        house["price_per_m2"] = house["price_aprox_usd"] / house["surface_covered_in_m2"]
    houses_rowwise




.. parsed-literal::

    [{'price_aprox_usd': 115910.26,
      'surface_covered_in_m2': 128,
      'rooms': 4,
      'price_per_m2': 905.54890625},
     {'price_aprox_usd': 48718.17,
      'surface_covered_in_m2': 210,
      'rooms': 3,
      'price_per_m2': 231.9912857142857},
     {'price_aprox_usd': 28977.56,
      'surface_covered_in_m2': 58,
      'rooms': 2,
      'price_per_m2': 499.61310344827587},
     {'price_aprox_usd': 36932.27,
      'surface_covered_in_m2': 79,
      'rooms': 3,
      'price_per_m2': 467.4970886075949},
     {'price_aprox_usd': 83903.51,
      'surface_covered_in_m2': 111,
      'rooms': 3,
      'price_per_m2': 755.8874774774774}]



JSON is a great way to organize data, but it does have some downsides.
Note that each dictionary represents a single house or, if we think
about it as tabular data, a row in our dataset. This means that it’s
pretty easy to do row-wise calculations (like we did with price per
square meter), but column-wise calculations are more complicated. For
instance, what if we wanted to know the mean house price for our
dataset? First we’d need to collect the price for each house in a list
and then calculate mean.

.. code:: ipython3

    VimeoVideo("645390848", h="889a3cfb33", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645390848?h=889a3cfb33"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.1.6:** To calculate the mean price for ``houses_rowwise`` by
completing the code below.

-  `Write a for loop in
   Python. <../%40textbook/01-python-getting-started.ipynb#Working-with-for-Loops>`__
-  `Append an item to a list in
   Python. <../%40textbook/01-python-getting-started.ipynb#Appending-Items>`__

.. code:: ipython3

    house_prices = []
    for house in houses_rowwise:
        
        ...
    mean_house_price = sum(house_prices) / len(house_prices)
    
    mean_house_price

One way to make this sort of calculation easier is to organize our data
by features instead of observations. We’ll still use dictionaries and
lists, but we’ll implement them a slightly differently.

.. code:: ipython3

    houses_columnwise = {
        "price_aprox_usd": [115910.26, 48718.17, 28977.56, 36932.27, 83903.51],
        "surface_covered_in_m2": [128.0, 210.0, 58.0, 79.0, 111.0],
        "rooms": [4.0, 3.0, 2.0, 3.0, 3.0],
    }
    
    houses_columnwise




.. parsed-literal::

    {'price_aprox_usd': [115910.26, 48718.17, 28977.56, 36932.27, 83903.51],
     'surface_covered_in_m2': [128.0, 210.0, 58.0, 79.0, 111.0],
     'rooms': [4.0, 3.0, 2.0, 3.0, 3.0]}



.. code:: ipython3

    VimeoVideo("645390869", h="ef4d49bf66", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645390869?h=ef4d49bf66"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.1.7:** Calculate the mean house price in ``houses_columnwise``

-  `Perform common aggregation tasks on a list in
   Python. <../%40textbook/01-python-getting-started.ipynb#Aggregating-Items>`__

.. code:: ipython3

    mean_house_price = sum(houses_columnwise["price_aprox_usd"])/ len(houses_columnwise["price_aprox_usd"])
    
    mean_house_price




.. parsed-literal::

    62888.35399999999



Of course, when we organize our data according to columns / features,
row-wise operations become more difficult.

.. code:: ipython3

    VimeoVideo("645396267", h="66eda35f00", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645396267?h=66eda35f00"
        frameborder="0"
        allowfullscreen
    ></iframe>




**Task 1.1.8:** Create a ``"price_per_m2"`` column in
``houses_columnwise``?

-  `Add a a key-value pair to a dictionary in
   Python. <../%40textbook/01-python-getting-started.ipynb#Creating-Dictionaries>`__
-  `Zip two lists together in
   Python. <../%40textbook/01-python-getting-started.ipynb#Zipping-Items>`__
-  `Write a for loop in
   Python. <../%40textbook/01-python-getting-started.ipynb#Working-with-for-Loops>`__

.. code:: ipython3

    price = houses_columnwise["price_aprox_usd"]
    area = houses_columnwise["surface_covered_in_m2"]
    total_list = zip(price, area)
    price_per_m2_list = []
    
    for price, area in total_list:
        price_per_m2 = price / area
        price_per_m2_list.append(price_per_m2)
    house["price_per_m2"] = price_per_m2_list
        
    houses_columnwise




.. parsed-literal::

    {'price_aprox_usd': [115910.26, 48718.17, 28977.56, 36932.27, 83903.51],
     'surface_covered_in_m2': [128.0, 210.0, 58.0, 79.0, 111.0],
     'rooms': [4.0, 3.0, 2.0, 3.0, 3.0]}



Tabular Data and pandas DataFrames
==================================

.. raw:: html

   <iframe src="https://player.vimeo.com/video/645396345?h=ba25c25741&amp;title=0&amp;byline=0&amp;portrait=0&amp;speed=0&amp;badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479" width="1920" height="1080" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen title="011-9">

.. raw:: html

   </iframe>

.. code:: ipython3

    VimeoVideo("645396345", h="ba25c25741", width=600)




.. raw:: html

    
    <iframe
        width="600"
        height="300"
        src="https://player.vimeo.com/video/645396345?h=ba25c25741"
        frameborder="0"
        allowfullscreen
    ></iframe>




While you’ve shown that you can wrangle data using lists and
dictionaries, it’s not as intuitive as working with, say, a spreadsheet.
Fortunately, there are lots of libraries for Python that make it an even
better tool for tabular data — way better than spreadsheet applications
like Microsoft Excel or Google Sheets! One of the best known data
science libraries is **pandas**, which allows you to organize data into
**DataFrames**.

Let’s import pandas and then create a DataFrame from
``houses_columnwise``.

.. code:: ipython3

    import pandas as pd
    
    data = {
        "price_aprox_usd": [115910.26, 48718.17, 28977.56, 36932.27, 83903.51],
        "surface_covered_in_m2": [128.0, 210.0, 58.0, 79.0, 111.0],
        "rooms": [4.0, 3.0, 2.0, 3.0, 3.0],
    }
    
    df_houses = pd.DataFrame(data)
    
    df_houses




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
          <th>price_aprox_usd</th>
          <th>surface_covered_in_m2</th>
          <th>rooms</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>115910.26</td>
          <td>128.0</td>
          <td>4.0</td>
        </tr>
        <tr>
          <th>1</th>
          <td>48718.17</td>
          <td>210.0</td>
          <td>3.0</td>
        </tr>
        <tr>
          <th>2</th>
          <td>28977.56</td>
          <td>58.0</td>
          <td>2.0</td>
        </tr>
        <tr>
          <th>3</th>
          <td>36932.27</td>
          <td>79.0</td>
          <td>3.0</td>
        </tr>
        <tr>
          <th>4</th>
          <td>83903.51</td>
          <td>111.0</td>
          <td>3.0</td>
        </tr>
      </tbody>
    </table>
    </div>



Excellent work! You’ve mastered the concept of **tabular data**,
understand the principles behind **tidy data**, and used **lists** and
**dictionaries** to organize and augment our Mexico housing dataset.
Next, we’ll use these skills on the entire dataset — with over 150,000
observations — to better understand the real estate market in the
country.

--------------

Copyright © 2022 WorldQuant University. This content is licensed solely
for personal use. Redistribution or publication of this material is
strictly prohibited.
