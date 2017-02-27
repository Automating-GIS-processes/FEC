

##<a name="list-files"></a> 2. Listing files 

Listing and searching for file pathnames from file system can be done using a specific module called **[glob](https://docs.python.org/3/library/glob.html)**.
 
The glob library contains a function, also called glob, that finds files and directories whose names match a pattern \[0\]. 
We provide those patterns as strings: the character * matches zero or more characters, while ? matches any one character. 

1. We can use this to get the names of all files in the data directory ('/home/geo/data'):

  ```python
  >>> import glob
  >>> print(glob.glob('/home/geo/data/*'))
  ['/home/geo/data/inflammation-08.csv',
   '/home/geo/data/inflammation-10.csv',
   '/home/geo/data/inflammation-11.csv',
   '/home/geo/data/inflammation-06.csv',
   '/home/geo/data/inflammation-12.csv',
   '/home/geo/data/small-03.csv',
   '/home/geo/data/small-02.csv',
   '/home/geo/data/inflammation-07.csv',
   '/home/geo/data/inflammation-05.csv',
   '/home/geo/data/small-01.csv',
   '/home/geo/data/inflammation-03.csv',
   '/home/geo/data/inflammation-04.csv',
   '/home/geo/data/inflammation-02.csv',
   '/home/geo/data/inflammation-01.csv',
   '/home/geo/data/inflammation-09.csv']
  ```
  
2. We can also search for only specific files and file formats. Here, we search for files that starts with the word 'small' and ends with file format '.csv':
 
 ```python
  >>> print(glob.glob('/home/geo/data/small*.csv'))
  ['/home/geo/data/small-03.csv', '/home/geo/data/small-02.csv', '/home/geo/data/small-01.csv']
 ```

##<a name="read-multiple"></a> 3. Reading data from multiple files

As the previous examples show, glob.glob’s result is a **list** of file and directory paths in arbitrary order. This means we can loop over it to do something with each filename in turn. 
What we want to do next is to read the first line of each file and add it to a list called `headers`.
 
1. Let's create a list of csv-files (called _filepaths_) that contain data about inflammation:

  ```python
  >>> filepaths = glob.glob("/home/geo/data/inflammation*.csv")
  >>> print(fps)
  ['/home/geo/data/inflammation-08.csv', 
  '/home/geo/data/inflammation-10.csv', 
  '/home/geo/data/inflammation-11.csv', 
  '/home/geo/data/inflammation-06.csv', 
  '/home/geo/data/inflammation-12.csv', 
  '/home/geo/data/inflammation-07.csv', 
  '/home/geo/data/inflammation-05.csv', 
  '/home/geo/data/inflammation-03.csv', 
  '/home/geo/data/inflammation-04.csv', 
  '/home/geo/data/inflammation-02.csv', 
  '/home/geo/data/inflammation-01.csv', 
  '/home/geo/data/inflammation-09.csv']
  ```
