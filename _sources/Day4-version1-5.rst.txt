Species tool: Version 1.5
===========================

Before adding all the required functionality to our species converter tool, let's make an intermediate
version to make it easier to follow the process.

This **Version 1.5.** should execute the following processing steps:

- Import the required module (arcpy)
- Get parameters from the toolbox using ``GetParametersAsText`` function
- Add a new field into the Shapefile with ``AddField_management`` function
- Update the value for the attribute just created with ``CalculateField_management`` function
- Convert input shapefile into a Raster Dataset using ``PolygonToRaster_conversion`` function
- Print info for the user that tool has finished successfully using ``AddMessage`` function


**The interface**

.. figure:: img/Arcpy_version2_interface.png

**The code (Original plan):**


.. code:: python

    # Import arcpy module so we can use ArcGIS geoprocessing tools
    import arcpy

    """ This script adds a field into the input shapefile and updates the value
        of that field based (range: 1-5) and finally rasterizes the shapefile """

    # 1. Get parameters from the toolbox using 'GetParametersAsText' method
    #----------------------------------------------------------------------
    # --> check ArcGIS help for info how to use methods
    # Method info: http://resources.arcgis.com/en/help/main/10.2/index.html#//018v00000047000000

    input_species_shp = arcpy.GetParameterAsText(0)
    output_path = arcpy.GetParameterAsText(1)
    attribute_name = arcpy.GetParameterAsText(2)
    presence_value = arcpy.GetParameterAsText(3)


    # 2. Add a new field into the input shapefile with 'AddField_management' method
    #------------------------------------------------------------------------------
    # Method info: http://resources.arcgis.com/en/help/main/10.2/index.html#//001700000047000000

    arcpy.AddField_management(in_table=input_species_shp, field_name=attribute_name, field_type="SHORT") # Other possible parameters can be left as default


    # 3. Update the presence value for our newly created attribute with 'CalculateField_management' method
    #-----------------------------------------------------------------------------------------------------
    # Method info: http://resources.arcgis.com/en/help/main/10.2/index.html#//00170000004m000000

    arcpy.CalculateField_management(in_table=input_species_shp, field=attribute_name, expression=presence_value)


    # 4. Convert polygon to raster using 'PolygonToRaster_conversion' method
    #-----------------------------------------------------------------------
    # Method info: http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html#//001200000030000000
    arcpy.PolygonToRaster_conversion(in_features=input_species_shp, value_field=attribute_name, out_rasterdataset=output_path)


    # 5. Print info for the user that tool has finished succesfully using 'AddMessage' method
    #----------------------------------------------------------------------------------------
    # Method info: http://resources.arcgis.com/en/help/main/10.2/index.html#//018v00000007000000

    my_message = "Tool finished successfully! Rock on!"
    arcpy.AddMessage(my_message)



**The code (Created during class on thursday 9.3.):**

The toolbox and corresponding code below was created during the lesson on 9.3.2016 (we added the cell size parameter to our tool):

.. figure:: img/Version_1_5_modified.png

.. figure:: img/ValueListArcToolbox.png



    #---------------------------------------------------------------------
    # Arcpy_1_SimplePoly2Raster.py
    # This script takes a shapefile as an input and converts it to raster.
    #
    # Arcpy script
    # Usage: ArcToolbox [name]
    #----------------------------------------------------------------------

    # Import needed modules
    import arcpy


    # Enable Arcpy to overwrite existing files
    arcpy.env.overwriteOutput = True

    #---------------------------------------------------------------------------------------------
    # 1. Get parameters from the toolbox using 'GetParametersAsText' method
    #   --> check ArcGIS help for info how to use methods
    #   Method info: http://pro.arcgis.com/en/pro-app/arcpy/functions/getparameterastext.htm
    #---------------------------------------------------------------------------------------------


    input_shp = arcpy.GetParameterAsText(0)
    output_raster = arcpy.GetParameterAsText(1)
    cell_size = arcpy.GetParameter(2)
    attribute_name = arcpy.GetParameterAsText(3)
    presence_value = arcpy.GetParameterAsText(4)

    """
    input_shp = r"C:\HY-Data\vuokkhei\documents\AUTOGIS\DAMSELFISH\TEMP\DAMSELFISH_test_data.shp"
    output_raster = r"C:\HY-Data\vuokkhei\documents\AUTOGIS\DAMSELFISH\Results\damselfish_test3.tif"
    value_attribute = "binomial"
    cell_size = 0.79
    attribute_name = "NewFIELD"
    """


    #---------------------------------------------------------------------------
    # 2. Add new field into the shapefile using AddField_management -function
    # Syntax: AddField_management (in_table, field_name, field_type, {field_precision}, {field_scale}, {field_length}, {field_alias}, {field_is_nullable}, {field_is_required}, {field_domain})
    #------------------------------------------------------------------------
    arcpy.AddField_management(in_table=input_shp, field_name=attribute_name, field_type="SHORT")

    #-----------------------------------------------------------------------------------
    # 3. CALCULATE VALUE FOR THE NEW FIELD
    # SYNTAX: CalculateField_management (in_table, field, expression, {expression_type}, {code_block})
    #-------------------------------------------------------------------------------------------------
    arcpy.CalculateField_management(in_table=input_shp, field=attribute_name, expression=presence_value)

    #--------------------------------------------------------------------------------------------
    # 4. Convert input Shapefile into a Raster Dataset using 'PolygonToRaster_conversion' method
    # Method info: http://resources.arcgis.com/en/help/main/10.2/index.html#//001200000030000000
    #
    # Syntax: PolygonToRaster_conversion (in_features, value_field, out_rasterdataset, {cell_assignment}, {priority_field}, {cellsize})
    #--------------------------------------------------------------------------------------------
    arcpy.PolygonToRaster_conversion(in_features=input_shp, value_field=attribute_name, out_rasterdataset=output_raster, cellsize=cell_size)


    #arcpy.PolygonToRaster_conversion(input_shp, value_attribute, output_raster, "", "", cell_size)

    # 3. ADD INFO MESSAGE

    message_text = "\n\nProcess was a great success! \nOutput generated: " + output_raster + "\n\n"

    #ADD INFO TO TOOLBOX PROCESSING WINDOW
    arcpy.AddMessage(message_text)

    #PRINT INFO TO PYTHON CONSOLE
    print(message_text)
