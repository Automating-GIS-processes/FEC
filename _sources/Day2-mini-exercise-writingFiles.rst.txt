Task: write results to text file
=================================

In Exercise 3 on functions you were asked to define a function ``circleArea()`` which takes in one parameter ``radius``
and returns the Area of a circle with the given radius. Using the function, update the following code so that
you store the output into a text file `Circle_areas.txt` on your computer:


.. code:: python

    textfile = "Circle_areas.txt" #Update full filepath if needed

    # Update the variable result for different radius, and save the text into a text file (one result per row)
    for r in range(5):

        # Generate the result sentence and store it in a variable:
        result = 'The area for a circle with a radius of ' + str(r) + ' mm is ' + str(circleArea(r))+' mm^2'

        # Save the contents of the variable result to the textfile
        # your code here!!
