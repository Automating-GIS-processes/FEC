Task: generate numbers
=======================

1. Write a short script which prints out numbers 1-10 using a ``for``-loop (2 lines of code!). Comment your code and store it in a script file `printNumbers.py`.

|

2. Make a script which prints numbers 10-20. You can use the script `printNumbers.py` as a starting point (make a copy and store it as `printNumbers_if.py` )

You might need to use an if-statement in order to complete the second task. Can you think of a way to print numbers 10-20 without the if-statement?

*Mallivastaus:*

.. code:: python

        # numerot 1-10
        for number in range(1,11):
            print(number)

        # Printtaa numerot 10-20, vaihtoehto 1:
        for number in range(10,21):
            print(number)

        # Printtaa numerot 10-20, vaihtoehto 1:
        for number in range(1,21):
            if number >=10:
                print(number)
            else:
                print("liian pieni!")