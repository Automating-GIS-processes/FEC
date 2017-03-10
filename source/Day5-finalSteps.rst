Running the Complete tool
=====================================

Now that we have the interface and script ready for the extended version of our tool.

Before we can run the tool, remember **which Python script will be run when the tool is executed** from the ``Properties`` of your Script tool under a ``Source`` -tab. Add the
``Arcpy_X_SimplePoly2Raster.py`` -file that we just created as the source file for this tool.

.. figure:: img/arcgis-properties.png
    :scale: 95 %
    :align: left

.. figure:: img/arcgis-source.png
    :scale: 75 %
    :align: left


Run the tool (via ArcMap!) and inspect the results in the output folder you specified.

.. note::

    You can also run the code in the Python IDLE by pressing **Run** > **Run Module** (or F5).
    However, you first need to replace the ``GetPaarametersAsText()`` so that the value is defined in the code. See code below.


.. code:: python

    #---------------------------------------------
    # If you wish to run the code in python Shell:
    #--------------------------------------------

    # you can comment out the link to the user interface
    """
    input_shp = arcpy.GetParameterAsText(0)
    output_raster = arcpy.GetParameterAsText(1)
    cell_size = arcpy.GetParameter(2)
    attribute_name = arcpy.GetParameterAsText(3)
    presence_value = arcpy.GetParameterAsText(4)
    """
    # And define parameters locally within your code
    input_shp = r"C:\HY-Data\vuokkhei\documents\AUTOGIS\DAMSELFISH\TEMP\DAMSELFISH.shp"
    output_raster = r"C:\HY-Data\vuokkhei\documents\AUTOGIS\DAMSELFISH\Results\damselfish.tif"
    value_attribute = "binomial"
    cell_size = 0.79
    attribute_name = "NewFIELD"
    """