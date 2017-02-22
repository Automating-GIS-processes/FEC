String-operations [under construction!]
=================


This section introduces you to most common (and often very useful) operations for text processing in Python. For a comprehensive list of string operations, please refer to `Python documentation <https://docs.python.org/3.5/library/string.html>`_.
You will find these string operations very useful in different context, for example when re-naming data files, or generating print-messages within your own scripts.

String is a data type that is used for representing text. Within code, strings can be enclosed with single ('') or double ("") quotation marks:


    .. code:: python
        # Strings can be enclosed with " or ' characters
        text1 = "Python"
        text2 = ' is cool!'
        multiline_text = """
                            Text using
                            multiple lines!
                        """

Concatenation
--------------

Combining several pieces of text into one:

    .. code:: python

        # You can concatenate strings
        combined_text = text1 + text2


By default, strings and numbers cannot be concatenated. Just try:

    .. code:: python
        #concatenate text and number
        number =3.5
        text_and_number = text1 + number  # will result in error

Numbers need to be converted into string data type using function `str()` prior to combining with strings.

    .. code:: python
        #concatenate text and number
        number =3.5
        text_and_number = text1 + str(number)  # should work!


Other operations
----------------

    .. code:: python
        # You can slice strings
        sliced_text = combined_text[0:6]   # --> take 6 letters starting from position 0

        # You can get the length of the string
        len(combined_text)
        len(sliced_text)

        # You can repeat using strings
        repeated = sliced_text*4


String escape characters
-------------------------
- Escape characters are non-printable characters that can be represented with back slash notation
- Most commonly used characters are: `\n` (new line) and `\t` (tabulator)



Formatting strings with `%`-operator

- `%s` –converts numbers into text
- `%f` –rounds decimals into a desired length and converts the value into text



Upper- and lower-case
---------------------

.. code:: python
    # You can replace words/letters with another one by using a built-in 'replace' function
    replaced_word = combined_text.replace('Python', 'Coding')

    # You can change letters to lower-case / upper-case
    upper = replaced_word.upper()
    lower = replaced_word.lower()

