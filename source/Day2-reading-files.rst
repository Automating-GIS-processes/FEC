Reading and writing text files
==============================

Reading and writing text files within a Python code can be very handy for example when you want to document a process,
or to automatically print out simple information and results (for example statistics) when running a bigger process.

Delimited text files
---------------------

Simple tabular data is often stored in delimited text files, where each row of data represents
a record of data (for example a country) and the attributes for each row are separated
with a specific character (for example a comma ``,``). First row of data often contains the column names for the array.

.. note::

    When working with Comma-Separated Values file (*csv), pay attention to your language and region-settings! (In Windows: Control panel > Region and language > Additional Settings)
    There you can determine the decimal separator as``.``(recommended) or ``,`` and the list separator as ``;`` or ``,``.

During this short course we will not be working extensively with tabular data in Python. You can find more information about essential modules for handling tabular data in Python
from the more extensive versions of this course:
- `Pandas and Geopandas modules <https://automating-gis-processes.github.io/2016/Lesson2-overview-pandas-geopandas.html>`_
- `NumPy-module <https://github.com/Python-for-geo-people/Lesson-6-Intro-to-NumPy>`_

Listing all files in a directory
--------------------------------

Listing and searching for file path names from file system can be done
using a specific module called
**`glob <https://docs.python.org/3/library/glob.html>`__**.

The glob library contains a function, also called glob, that finds files
and directories whose names match a pattern [0]. We provide those
patterns as strings: the character \* matches zero or more characters,
while ? matches any one character.

1. We can use this to get the names of all files in the data directory
   ('/data'):

.. code:: python
    import glob

    #Read file paths for all files in the folder to a list:
    DataPathList = glob.glob('/data/5972xxx/*'))

    len(DataPathList)   #number of items in the list
    print(DataPathList) # print all file paths


2. We can also search for only specific files and file formats. Here, we
   search for files that starts with "travel_times_to_ 59721" and ends with file
   format '.txt':

.. code:: python
    DataPathList = glob.glob('/data/travel_times_to_ 59721*.txt'))

    len(DataPathList)   #number of items in the list
    print(DataPathList) # print all file paths

 3. Reading data from multiple files
====================================

As the previous examples show, glob.glob’s result is a **list** of file
and directory paths in arbitrary order. This means we can loop over it
to do something with each filename in turn. What we want to do next is
to read the first line of each file and add it to a list called
``headers``.

1. Let's create a list of headers for the files:


.. code:: python
     filepaths = glob.glob('/data/5972xxx/travel_times_to_ 59721*.txt') #modify the filepath if needed!

     headers = [] # empty list for collecting the headers

     # iterate for each file path in the list
     for fp in filepaths:

        #Open the file in read mode
       with open(fp, 'r') as f:
           # Read the first line of the file
           first_line = f.readline()
           # Append the first line into the headers-list
           headers.append(first_line)

    #After going trough all the files, print the list of headers
    print(headers)