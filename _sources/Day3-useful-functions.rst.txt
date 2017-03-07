Useful functions related to filepaths
======================================

Download example dataset
-------------------------

Download the example dataset ``5972xxx.zip`` for this section from `this link <https://github.com/Automating-GIS-processes/FEC/raw/master/data/5972xxx.zip>`_.
The zip-file contains a folder with a subset of data from the `Travel Time Matrix dataset <http://blogs.helsinki.fi/accessibility/data/metropaccess-travel-time-matrix/>`_.

Unzip the folder to your local working directory. You should see the following files:

.. figure:: img/Travel_times_to_xxxxx.png
    :scale: 30 %


os-module
---------

When dealing with file paths in Python there are several useful
functions available in a sub-module called
`os.path <https://docs.python.org/3/library/os.path.html>`_.

For instance when creating output filepaths it is common that you have a
common folder where all the output files will be created. In such cases,
you need to combine the path to the folder and the output filename for
each output file that you produce, os-module can help with such an
operation.

1. It is possible to parse the filename of a file (without folder
   information):

.. code:: python

   import os

   # Extract filename from full path (change filepath to your own folder!)
   filename = os.path.basename("C:\HY-Data\username\AutoGIS\Data\5972xxx\travel_times_to_ 5972103.txt")
   print(filename)

2. One typical example that you might need to do sometime is to copy a
   part of file into a new file in another folder. Let's create a new
   folder called ***Results*** to the home -folder of our computer
   instance using specific command called ``os.makedirs()`` but ONLY if
   it does not exist already (we can take advantage of
   ``os.path.exists()`` -function):

.. code:: python

   import os
   result_dir = r"C:\HY-Data\username\AutoGIS\Results"

   # Check if folder does NOT exist
   f not os.path.exists(result_dir):

   # If folder didn't exist create one
   os.makedirs(result_dir)

Now we have a new folder in the specified location

3. Now we can combine the filename  and our new folder using
   ``os.path.join()`` -function:

.. code:: python

   # Filename:
   filename = "newfile.txt"

   #Create a filepath for the new file:
   output_file_path = os.path.join(result_dir, filename)
   print(output_file_path)


.. note::

   When reading / writing in Python, it is best to use the ``with``
   -statement as it takes care of closing your file after you have
   read/written something into your file. *Closing* the file takes care
   of saving the data into that file. If the file is not closed after
   writing something into it, the contents won't be saved into that
   file. It is similar idea than when thinking of writing something into
   a Word template document but without saving it anywhere. You can find
   more info about how to write data without ``with`` -statement, and
   how to close files from `here <https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files>`__.


glob
----

.. code:: python

   import glob

   # List all files in the folder
   file_list = glob.glob("C:\\HY-Data\\VUOKKHEI\\documents\\AUTOGIS\\*")

   for file in file_list:
       print(file)


more examples of how to combine the os-module in the next section.