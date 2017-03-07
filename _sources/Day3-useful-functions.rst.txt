Useful functions related to filepaths
======================================

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
   filename = os.path.basename("C:\HY-Data\VUOKKHEI\documents\CODES\AutoGIS\test.txt") # change filepath to your own folder!
   print(filename)

2. One typical example that you might need to do sometime is to copy a
   part of file into a new file in another folder. Let's create a new
   folder called ***Results*** to the home -folder of our computer
   instance using specific command called ``os.makedirs()`` but ONLY if
   it does not exist already (we can take advantage of
   ``os.path.exists()`` -function):

.. code:: python

   import os
   result_dir = "C:\HY-Data\VUOKKHEI\documents\CODES\AutoGIS\Exercise1"

   # Check if folder does NOT exist
   f not os.path.exists(result_dir):

   # If folder didn't exist create one
   os.makedirs(result_dir)

Now we have a new folder in the specified location

3. Now we can combine the filename (test.txt) and our new folder using
   ``os.path.join()`` -function:

.. code:: python

   # Filename:
   filename = newfile.txt

   #Create a filepath for the new file:

   output_file_path = os.path.join(result_dir, filename)
   print(output_file_path)

Copying selected lines of (multiple) files into a new location
---------------------------------------------------------------

1. Let's take our previous exercise (reading multiple files) as a
   starting point and copy the first line of each inflammation csv-file
   and save them into new files using the same filenames but located
   into our new Results folder. We will use ``os.path.basename()``
   -function to find out the filename of the input files and
   ``os.path.join()`` -function to create the new output filepaths that
   will be saved into the new Results folder:

.. code:: python
   import glob

   # List inflammation data files from the source directory
   source_dir = "/home/geo/data"
   inflammation_paths = glob.glob(source_dir + "/inflammation\*.csv")

   # As a reminder our result directory
   result_dir = "/home/geo/Results"

   # Iterate over the files
   for fp in inflammation_paths:

      # Parse the filename of the input file and print it as information for the user
      filename = os.path.basename(fp)
      print(filename)

.. code:: python

         # Open the source file in read mode
         with open(fp, 'r') as f:
             # Parse the output file name, combine the result_dir folder-path and the filename of the input file
             output_fp = os.path.join(result_dir, filename)

             # Open and create the output file in write mode
             with open(output_fp, 'w') as w:

                # Read the first line of the source file
                first_line = f.readline()

                # Write it to the output file
                w.write(first_line)


**Footnotes**

-  [0]: When reading / writing in Python, it is best to use the ``with``
   -statement as it takes care of closing your file after you have
   read/written something into your file. *Closing* the file takes care
   of saving the data into that file. If the file is not closed after
   writing something into it, the contents won't be saved into that
   file. It is similar idea than when thinking of writing something into
   a Word template document but without saving it anywhere. You can find
   more info about how to write data without ``with`` -statement, and
   how to close files from
   **`here <https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files>`__**.
