ArcGIS Toolbox
==============

Creating an ArcGIS Toolbox for Python scripts
---------------------------------------------

Now as we know how to use/access Python in ArcGIS, let's start our arcpy demo by creating a **Toolbox** for our scripts.

A Toolbox is a Graphical User Interface for using specific tools in ArcGIS:

   - Setting input/output files

   - Setting parameters

It is also possible and recommendable to create your own toolbox for the Python scripts that you have created, although it is possible to run your Python script also
without one.

New Toolboxes are created in the Catalog. Open the file catalog panel in ArcGIS (i.e. file explorer of ArcGIS).
Navigate to your course folder (or create a new Folder Connection). On top of the folder, press right mouse,
and choose **New** --> **Toolbox**. Give it a name ``SpeciesDataConverter.tbx`` and save it.

.. figure:: img/arcgis-create-toolbox.png
    :scale: 50 %

Opening the toolbox in ArcGIS
-----------------------------

Now you have should have an empty toolbox saved on a disk. Next, we will import the toolbox into ArcMap.
You can either drag and drop the new toolbox from Catalog to ArcToolbox-window, or:

  1. activate ArcToolbox panel
  2. right click in white space
  3. Add Toolbox (browse to the directory where you save your toolbox)






