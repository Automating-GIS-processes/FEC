Conditional statements
======================

Sources
-------

This lesson is based on the `Software Carpentry
group's <http://software-carpentry.org/>`__ lessons on `Programming with
Python <http://swcarpentry.github.io/python-novice-inflammation/>`__.

Basics of conditional statements
--------------------------------

Conditional statements can change the code behaviour based on meeting
certain conditions.

1. Let's take a simple example.

   .. code:: python

       >>> num = 37
       >>> if num > 100:
       ...     print('greater')
       ... else:
       ...     print('not greater')
       ...
       not greater

   What did we do here? First, we used the ``if`` and ``else``
   statements to determine what parts of the code to execute. Note that
   both lines containing ``if`` or ``else`` end with a ``:`` and the
   text beneath is indented. What do these tests do? The ``if`` test
   checks to see whether the variable value for ``num`` is greater than
   100. If so, 'greater' would be written to the screen. Since 37 is
   smaller than 100, the code beneath the ``else`` is executed. The
   ``else`` statement code will run whenever the ``if`` test is false.

2. The combination of ``if`` and ``else`` is very common, but both are
   not strictly required.

   .. code:: python

       >>> num = 53
       >>> if num > 100:
       ...     print('53 is greater than 100')
       ...
       >>>

   Note that here we use only the ``if`` statement, and because 53 is
   not greater than 100, nothing is printed to the screen.

3. We can also have a second test for an ``if`` statment by using the
   ``elif`` (else-if) statement.

   .. code:: python

       >>> num = -3
       >>> if num > 0:
       ...     print(num, 'is positive')
       ... elif num == 0:
       ...     print(num, 'is zero')
       ... else:
       ...     print(num, 'is negative')
       ...
       -3 is negative

   Makes sense, right? Note here that we use the ``==`` to test if a
   value is equal to another. The complete list of these comparison
   operators is given in the table below.

   +------------+----------------------------+
   | Operator   | Meaning                    |
   +============+============================+
   | ``<``      | Less than                  |
   +------------+----------------------------+
   | ``<=``     | Less than or equal to      |
   +------------+----------------------------+
   | ``==``     | Equal to                   |
   +------------+----------------------------+
   | ``>=``     | Greater than or equal to   |
   +------------+----------------------------+
   | ``>``      | Greater than               |
   +------------+----------------------------+
   | ``!=``     | Not equal to               |
   +------------+----------------------------+


Example with Urban area classifications:
----------------------------------------

Note that the elif-statement is tested only if the previous if- or elif-statement was not true.

    .. code:: python

        """
        This code will find out if the user lives in a sparsely populated area or an urban area
        according to the definition of urban areas in Finland: https://en.wikipedia.org/wiki/Urban_areas_in_Finland
        """

        # As population size as input from user
        population = input("What is the population of the area (number of people)?: ")

        #Convert user input as integer:
        population = int(population)

        # If population is zero or negative
        if population <= 0:
	        print("Ghost town!")

        # If population equals one
        elif population == 1:
	        print("Living alone!")

        # If population is less than 200
        elif population < 200:
            print("Sparsely populated area")

        # If population is more than 200
        elif population > 200:

            # Ask the user for maximum distance between buildings
            building_dist = input("What is the maximum distance between buildings in the area (m)?: ")
            #Convert user input as integer:
            building_dist = int(building_dist)

            #If building distance is greater than 200
            if building_dist >= 200:
                print("Sparsely populated area")

            #In case population was more than 200, and building distance less than 200
            else:
                print("Urban area")




4. We can also use ``and`` and ``or`` to have multiple conditions.

   .. code:: python

       >>> if (1 > 0) and (-1 > 0):
       ...     print('Both parts are true')
       ... else:
       ...     print('One part is not true')
       ...
       One part is not true
       >>> if (1 < 0) or (-1 < 0):
       ...     print('At least one test is true')
       ...
       At least one test is true

   This can be quite handy.



String comparisons
------------------

    .. code:: python

        # Define two text strings:
        text1 ="What's the story"
        text2 = "Morning glory?"

        #Check if strings are equal or not
        text1 == text2
        text1 != text2


        #Check if a letter/work is found in a string
        'a' in text1
        'a' in text2
        'glory' in text2
        'Glory' in text2

        # Check if string starts with spesific word /letter:
        filename.startswith("Toto")
        filename.startswith('.shp')
