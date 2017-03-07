Writing arcpy scripts
=====================

At this point we have created a nice interface for our Python tool in ArcGIS:

.. figure:: img/Arcpy_version1_interface.png
    :scale: 40 %

Next we need to write the functionality for our tool. The first version of our tool will simply convert Shapefiles into raster using the polygon to raster conversion -tool
and print out a customized message for the user.

First, we need start the ArcGIS IDLE (if it is not open already) from **All Programs** --> **ArcGIS**:

.. figure:: img/arcgis-idle-location.png

Create a new script called ``Arcpy_1_SimplePoly2Raster.py`` in IDLE (**File** --> **New File**) and save it to your computer:

.. figure:: img/arcgis-idle-new.png
    :scale: 40 %

Let's start writing the functionality of our tool to the script that we just created.

Importing arcpy
---------------

First thing to do is to import the arcpy module:

.. code:: python

    # Import neede modules
    import arcpy
    import os

.. note::

    Notice that arcpy can only be imported with Python interpreter that comes with ArcGIS. If you try to import it e.g. in Spyder, you will receive an error ``ImportError: No module named 'arcpy'``.

    Well...actually there is a way to `import arcpy from other places <http://gis.stackexchange.com/questions/86850/making-separate-python-installation-that-can-call-arcpy>`_ as well and also `import it into Spyder <http://gis.stackexchange.com/questions/176879/importing-arcpy-in-spyder>`_ but we will not
    cover this during our course.


Getting parameters from the toolbox
-----------------------------------

Before we can do anything with our tool and our nice interface for it, we need to get those parameters into our script. This can be done by using arcpy's function called ``.GetParameterAsText()`` where the index
value of the parameter is passed to the function (where number 0 is the first parameter). ArcGIS has a good documentation that should be used for searching the information about how different functions are used.

Let's import the first parameters from the graphical interface into our Python script using `GetParameterAsText() <http://desktop.arcgis.com/en/arcmap/latest/analyze/arcpy-functions/getparameterastext.htm>`_ -function:
Also, let's add a line of code which enables arcpy to owerwrite existing files: ``arcpy.env.overwriteOutput = True``.
Full script so far should look like this:

.. code:: python

    # Import neede modules
    import arcpy
    import os

    # Enable Arcpy to overwrite existing files
    arcpy.env.overwriteOutput = True

    #---------------------------------------------------------------------------------------------
    # 1. Get parameters from the toolbox using 'GetParametersAsText' method
    #   --> check ArcGIS help for info how to use methods
    #   Method info: http://resources.arcgis.com/en/help/main/10.2/index.html#//018v00000047000000
    #---------------------------------------------------------------------------------------------

    input_shp = arcpy.GetParameterAsText(0)
    output_raster = arcpy.GetParameterAsText(1)
    value_attribute = arcpy.GetParameterAsText(2)


Now we have a link between the user interface and the script. Next, let's call the required tool for converting input shapefile
into raster using the given parameters:

.. code:: python

    #--------------------------------------------------------------------------------------------
    # 2. Convert input Shapefile into a Raster Dataset using 'PolygonToRaster_conversion' method
    # Method info: http://resources.arcgis.com/en/help/main/10.2/index.html#//001200000030000000
    #--------------------------------------------------------------------------------------------

    arcpy.PolygonToRaster_conversion(in_features=input_shp, value_field=value_attribute, out_rasterdataset=output_raster)



Sending messages to the Script tool
-----------------------------------

It is possible to "print" messages to the user-interface while the tool is running. The regular ``print()`` -function won't do in this case and
we need to use ``AddMessage()`` -function (see `help <http://desktop.arcgis.com/en/arcmap/latest/analyze/arcpy-functions/addmessage.htm>`_) to send
any kind of messages to the user-interface of our tool.

Let's add a message at the end of our script:

.. code:: python

    #Print that the process was finished successfully
    message_text = "Process was a great success! \n Output generated: " + output_raster
    arcpy.AddMessage(info)



Save the full script as ``Arcpy_1_SimplePoly2Raster.py``.
Now, we have a script that we can use from our Toolbox in ArcGIS! Let's next see how it can be used.

