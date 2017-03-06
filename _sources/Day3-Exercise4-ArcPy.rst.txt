Final Exercise: ArcPy-script for processing species data
=====================================================

As an output of this exercise we will create three  ArcPy-scripts:

- **Version 1:** Arcpy_1_SimplePoly2Raster.py
- **Version 2:** Arcpy_2_SpeciesPoly2Raster.py
- **Version 3:** Arcpy_3_SpeciesPoly2Raster_Iterate.py

We will write the scripts together in the class, but if you wish you can also proceed at your own pace by following the
instructions in the upcoming sections. Feel free to document your codes into GitHub.


Version 1:
--------------------------------------

Create a ArcGIS toolbox that converts a Shapefile into a Raster Dataset.
Toolbox asks three parameters from the user: **input shapefile**, **output rasterdataset**, and **value field** (raster_value).
Toolbox executes a python script called ‘Arcpy_1_SimplePoly2Raster.py` that contains all the required functionalities of the tool.

.. figure:: img/Arcpy_version1_interface.png


**Required steps in the script-file for Version 1:**

- Import the required module (arcpy)
- Get parameters from the toolbox using ``GetParametersAsText`` function
- Convert input shapefile into a Raster Dataset using `PolygonToRaster_conversion <http://pro.arcgis.com/en/pro-app/tool-reference/conversion/polygon-to-raster.htm>`_ -function



Version 2:
--------------------------------------

Create a ArcGIS toolbox that converts a Shapefile into a Raster Dataset based on values on attribute field that will be created during the execution.
Tool asks four parameters: input shapefile, output raster Dataset, attribute_name, and presence value.
Tool will print useful information for the user about the execution process. Toolbox executes a python script called *Arcpy_2_SpeciesPoly2Raster.py* that contains all the required functionality of the tool.


.. figure:: img/Arcpy_version2_interface.png

**Required steps in the script-file for Version 2:**

- Import the required module (arcpy)
- Get parameters from the toolbox using ``GetParametersAsText`` function
- Add a new field into the Shapefile with ``AddField_management`` function
- Update the value for the attribute just created with ``CalculateField_management`` function
- Convert input shapefile into a Raster Dataset using ``PolygonToRaster_conversion`` function
- Print info for the user that tool has finished successfully using ``AddMessage`` function



Version 3:
-----------

Create a ArcGIS toolbox that converts individual species in a Shapefile into Raster Datasets based on species information on attribute field ‘binomial’.
Tool asks five parameters: **input shapefile**, **output folder**, **species_attribute**, **attribute_name_for_raster_value**, **raster_value**.
Tool will print useful information for the user about the execution process.
Toolbox executes a python script called *Arcpy_3_SpeciesPoly2Raster_Iterate.py* that contains all the required functionality of the tool.

.. figure:: img/Arcpy_version3_interface.png

**Required steps in the script-file for Version 3:**

- Import the required module (arcpy)
- Get parameters from the toolbox using ``GetParametersAsText`` function
- Add a new field into the Shapefile with ``AddField_management`` function
- Update the value for the attribute with ``CalculateField_management`` function
- Determine a list of unique species in the Shapefile using ``SearchCursor`` function
- Create a Feature Layer from the shapefile using ``MakeFeatureLayer_management`` function
- Select individual species from the Shapefile using ``SelectLayerByAttribute_management`` function
- Convert individual species in the Shapefile into Raster Datasets using ``PolygonToRaster_conversion`` function
- Print info for the user that tool has finished successfully using ``AddMessage`` function
