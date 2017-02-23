Getting started with Python
===========================

This tutorial is based on material from the `python-for-geopeople <https://github.com/Python-for-geo-people>`_ -course and `Software Carpentry
group's <http://software-carpentry.org/>`__ lessons on `Programming with
Python <http://swcarpentry.github.io/python-novice-inflammation/>`__.

For a full documentation of Python, please refer to the `online documentation <https://docs.python.org/3.5/>`_
Throughout the course, if you get confused remember ask from others and to search for help online (just google it!).


Python console
---------------
There are different ways of using the Python-interpreter. We will start familiarizing ourselves with the python syntax via the IPython console window in Spyder, which is an integrated development environment (IDE) for
scientific programming with Python.

1. Open Spyder from Start> All Programs > Anaconda3 > Spyder


.. figure:: img/Spyder.png
   :alt: Spyder IDE

   Spyder IDE

The console-window is in the bottom-right corner of the Spyder-window. For now, you can ignore the other components in Spyder, we will get back to those a bit later.

Variables and basic arithmetic
------------------------------

We will start our Python lesson by learning a bit of the basic
operations you can perform using Python.

1. Python can be used as a simple calculator.

   .. code:: python

       >>> 1 + 1
       2
       >>> 5 * 7
       35

2. You can use Python for more advanced math by using *functions*.
   Functions are pieces of code that perform a single action such as
   printing information to the screen (e.g., the ``print()`` function).
   Functions exist for a huge number of operations in Python.

   .. code:: python

       >>> sin(3)
       Traceback (most recent call last):
         File "<stdin>", line 1, in <module>
       NameError: name 'sin' is not defined
       >>> sqrt(4)
       Traceback (most recent call last):
         File "<stdin>", line 1, in <module>
       NameError: name 'sqrt' is not defined

   Wait, what? Python can't calculate square roots or do basic
   trigonometry? Of course it can, but we need one more step.

3. The list of basic arithmetic operations that can be done by default
   in Python is in the table below.


+----------------+--------+---------------+----------------+
| Operation      | Symbol | Example syntax| Returned value |
+================+========+===============+================+
| Addition       | ``+``  | ``2 + 2``     |     ``4``      |
+----------------+--------+---------------+----------------+
| Subtraction    | ``-``  | ``4 - 2``     |     ``2``      |
+----------------+--------+---------------+----------------+
| Multiplication | ``*``  | ``2 * 3``     |     ``6``      |
+----------------+--------+---------------+----------------+
| Division       | ``/``  | ``4 / 2``     |     ``2``      |
+----------------+--------+---------------+----------------+
|Exponentiation  | ``**`` | ``2**3``      |     ``8``      |
+----------------+--------+---------------+----------------+

For anything more advanced, we need to load a *library*.

libraries
---------

   .. code:: python

       >>> import math
       >>> math.sin(3)
       0.1411200080598672
       >>> math.sqrt(4)
       2.0

   A *library* is a group of code items such as functions that are
   related to one another. Libraries are loaded using ``import``.
   Functions that are part of the library ``libraryname`` could then be
   used by typing ``libraryname.functionname()``. For example, ``sin()``
   is a function that is part of the ``math`` library, and used by
   typing ``math.sin()`` with some number between the parentheses.
   Libraries may also contain constants such as ``math.pi``.

   .. code:: python

       >>> math.pi
       3.141592653589793
       >>> math.sin(math.pi)
       1.2246467991473532e-16

4. Functions can also be combined.

   .. code:: python

       >>> print(math.sqrt(4))
       2.0
       >>> print('The square root of 4 is',math.sqrt(4))
       The square root of 4 is 2.0

5. *Variables* can be used to store values calculated in expressions and
   used for other calculations.

   .. code:: python

       >>> temp_celsius = 10.0
       >>> print(temp_celsius)
       10.0
       >>> print('temperature in Fahrenheit:', 9/5 * temp_celsius + 32)
       temperature in Fahrenheit: 50.0

   Above, we also see one common format for *good* variable naming,
   separation of words by underscores ``_`` (e.g., ``temp_celsius``).
   This is called pothole\_case\_naming. We'll see another below.

6. Values stored in *variables* can also be updated.

   .. code:: python

       >>> temp_celsius = 15.0
       >>> print('temperature in Celsius is now:', temp_celsius)
       temperature in Celsius is now: 15.0
       >>> TemperatureInFahrenheit = 9/5 * temp_celsius + 32
       >>> print('temperature in Celsius:', temp_celsius, 'and in Fahrenheit:', TemperatureInFahrenheit)
       temperature in Celsius: 15.0 and in Fahrenheit: 59.0

   An alternative to naming variables using pothole\_case\_naming is to
   use capital letters for each word with no spaces between (e.g.,
   ``TemperatureInFahrenheit``). This is called CamelCaseNaming. Both
   options are easy to read and help you use *good* variable names.
   After all, *people* should be able to easily understand what
   different variables contain :+1:.

7. Note that changing the values of a variable does not affect those of
   other variables.

   .. code:: python

       >>> temp_celsius = 20.0
       >>> print('temperature in Celsius is now:', temp_celsius, 'and temperature in Fahrenheit is still:', TemperatureInFahrenheit)
       temperature in Celsius is now: 20.0 and temperature in Fahrenheit is still: 59.0

8. One of the nice options in IPython is that you can see which
   variables are in memory by typing ``%whos``.

   .. code:: python

       >>> %whos
       Variable                  Type      Data/Info
       ---------------------------------------------
       TemperatureInFahrenheit   float     59.0
       temp_celsius              float     20.0

9. There are 4 basic *data types* in Python as shown in the table below.


+----------------+----------------------+-----------+
| Data type name | Data type            | Example   |
+================+======================+===========+
| ``int``        | Whole integer values | ``4``     |
+----------------+----------------------+-----------+
| ``float``      | Decimal values       |``3.1415`` |
+----------------+----------------------+-----------+
| ``str``        | Character strings    | ``'Hot'`` |
+----------------+----------------------+-----------+
| ``bool``       | True/false values    | ``True``  |

The data types are displayed when using ``%whos``, but can also be found using the``type()`` function.
As you will see, the data types are important because some are not compatible with one another.

   .. code:: python

       >>> WeatherForecast = 'Hot'
       >>> type(WeatherForecast)
       str
       >>> type(TemperatureInFahrenheit)
       float
       >>> TemperatureInFahrenheit = TemperatureInFahrenheit + 5.0 * WeatherForecast
       ---------------------------------------------------------------------------
       TypeError                                 Traceback (most recent call last)
       <ipython-input-21-7046bdc97a54> in <module>()
       ----> 1 TemperatureInFahrenheit = TemperatureInFahrenheit + 5.0 * WeatherForecast

       TypeError: can't multiply sequence by non-int of type 'float'

Summary
---------

In this first section we have seen a bit of what we can do in Python: defining variables,
basic arithmetic, importing libraries, using functions, and combining
these things to put the computer to work for us.




