Pandas-module
==============

Materials
--------------

- `Overview of Pandas and Geopandas in the full version of the AutoGIS-course https://automating-gis-processes.github.io/2016/Lesson2-overview-pandas-geopandas.html`_

- `Pandas documentation and tutorials <http://pandas.pydata.org/pandas-docs/stable/tutorials.html>`_

Example code from class
-----------------------

    .. code:: python

        # -*- coding: utf-8 -*-
        """
        Created on Wed Mar  8 10:35:19 2017

        @author: Henrikki T.
        """

        # Testing modules and functions

        # Importoidaan tarvittavat modulit
        import os
        import glob
        import pandas as pd

        # Tiedostonimien parsiminen
        # -------------------------

        # Kansiopolku
        input_dir = r"C:\HY-Data\VUOKKHEI\documents\AUTOGIS\5972xxx"
        f = "travel_times_to_ 5972095.txt"

        # Parsitaan tiedostopolku
        fp = os.path.join(input_dir, f)

        # Luetaan tiedosto sisään
        data = pd.read_csv(fp, sep=';')
        #print(data)

        # Usean tiedoston lukeminen
        # -------------------------

        # Hyödynnetään glob moduulin glob funktiota tiedostopolkujen määrittämisessä
        q = "travel*.txt"
        cmd = os.path.join(input_dir, q)
        filepaths = glob.glob(cmd)

        for fp in filepaths:
            # Luodaan infotekstiä itsellemme (tiedostonimi)
            basename = os.path.basename(fp)
            info = "Processing file: %s" % basename
            print(info)

            # Luetaan tiedosto sisään
            data = pd.read_csv(fp, sep=';')

            # Printataan kolumnit
            cols = data.columns

            # Lasketaan joukkoliikenteen ja autoilun matka-aikojen erotus
            data['difference'] = data['pt_r_t'] - data['car_r_t']

            # Printataan viisi ensimmäistä riviä
            print(data.head())
            print("\n\n")
