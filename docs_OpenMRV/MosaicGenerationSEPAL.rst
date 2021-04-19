---
title: Mosaic generation with SEPAL
summary: In this tutorial, you will create a Landsat mosaic for the Mai Ndombe region of the Democratic Republic of the Congo, where REDD+ projects are currently underway. You will also create mosaics for the State of Rondonia (Brazil).
author: Karen Dyson
creation date: March, 2021
language: English
publisher and license: Copyright 2021, World Bank. This work is licensed under a Creative Commons Attribution 3.0 IGO

tags:
- OpenMRV
- Landsat
- Sentinel-2
- Optical sensors
- Remote sensing
- GEE
- SEPAL
- Cloud cover
- Composite
- Mosaic

group:
- category: SEPAL
  stage: Composite creation/Pre-process
---

-----------------------------
Mosaic generation with SEPAL
-----------------------------

1. Background
--------------

SEPAL provides a robust interface for generating Landsat and Sentinel 2 mosaics. These mosaics can be downloaded locally or to your Google Drive.

Creating mosaics is a critical first step for creating classification maps (see tutorials here on OpenMRV under process "Classification", specifically under tool "SEPAL" but also tool "GEE") and change detection maps (see tutorials here on OpenMRV under process "Change detection", specifically under tool "SEPAL" but also tools "CCDC", "CODED", and "LandTrendr").


2. Learning Objectives
-----------------------

In this tutorial, you will create a Landsat mosaic for the Mai Ndombe region of the Democratic Republic of the Congo, where REDD+ projects are currently underway. You will also create mosaics for the State of Rondonia (Brazil).

* Create an image mosaic in SEPAL.
* Become familiar with a variety of options for selecting dates, sensors, mosaicking and download options in SEPAL.


2.1 Pre-requisites
===================

* A SEPAL account. Please check under tool "SEPAL" here on OpenMRV for an introduction to SEPAL.
* A GEE account. Please check under tool "SEPAL" here on OpenMRV for an introduction to SEPAL.

3. Tutorial: Mosaic generation in SEPAL
----------------------------------------

3.1 Create a Landsat mosaic using select Country/Province
==========================================================

1. If SEPAL is not already open, click to open SEPAL in your browser: https://sepal.io/ and login.
2. Click on the **Processing** tab.
3. Then, click on **Optical Mosaic**.
4. When the Optical Mosaic tab opens, you will see an **Area of Interest** window in the lower right hand corner of your screen.

   There are three ways to choose your area of interest. Bring up the menu by clicking the carrot to the right of the window label.

  a. Select Country/Province (the default)
  b. Select from EE table
  c. Draw a polygon

.. figure:: images/area_of_interest.png
   :alt: The Area of Interest menu
   :width: 350
   :align: center



5. We will use the **Select a country/province** option.

  a. In the list of countries that pops up, scroll down until you see the available options for **Congo, Dem Republic of**. Note there is also the Republic of Congo, which is not what we’re looking for.
  b. Under Province/Area, notice that there are many different options.
  c. Select **Mai-Ndombe.**
  d. [Optional] You can add a **Buffer** to your mosaic. This will include an area around the province of the specified size in your mosaic.
  e. Click **Next.**

.. figure:: images/country_province.png
   :alt: The Country or Province selection screen.
   :align: center



6. In the **Date** menu you can select the **Year** you are interested in or click on **More**.

  a. This interface allows you to refine the dates or seasons you are interested in.
  b. You can select a **target date** (The date in which pixels in the mosaic should ideally come from), as well as adjust the start and end date flags.
  c. You can also include additional seasons from the past or the future by adjusting the **Past Seasons** and **Future Seasons** slider. This will include additional years’ data of the same dates specified. For example, if you’re interested in August 2015, including one future season will also include data from August 2016. This is useful if you’re interested in a specific time of year but there is significant cloud cover.
  d. For this tutorial, let’s create imagery for the dry season of 2019.

    i. Select July 1 of 2019 as your target date (2019-07-01), and move your date flags to May 1-September 30.
    ii. Click **Apply**.

.. figure:: images/date_menu.png
   :alt: The date menu.
   :align: center



7. Now select the **Data Sources (SRC)** you’d like. Here, select the **Landsat L8 & L8 T2** option. The color of the label turns brown once it has been selected. Then click **Done**.

  * **L8** began operating in 2012 and is continuing to collect data
  * **L7** began operating in 2001, but has a scan-line error that can be problematic for dates between 2005-present
  * **L4-5** collected data from July 1982-May 2012
  * **Sentinel 2 A+B** began operating in June 2015

8. Now SEPAL will load a preview of your data. By default it will show you where RGB band data is available. You can click on the RGB image at the bottom to choose from other combinations of bands or metadata.

  a. When it is done, examine the preview to see how much data is available. For this example, coverage is good. However, in the future when you are creating your own mosaic, if there is not enough coverage of your area of interest, you will need to adjust your parameters.
  b. To do so, notice the five tabs in the lower right. You can adjust the initial search parameters using the first three of these tabs. For example, Click on **Dat** to expand the date range if you would like.
  c. The last two tabs are for **scene selection** and **composite,** which are more advanced filtering steps. We’ll cover those now.

.. figure:: images/mosaic_preview.png
   :alt: A preview of your mosaic.
   :align: center



9. We’re now going to go through the **scene selection process**. This allows you to change which specific images to include in your mosaic.

  a. You can change the scenes that are selected using the **SCN** button on the lower right of the screen. You can use all scenes or select which are prioritized. You can revert any changes by clicking on **Use All Scenes** and then **Apply**.
  b. Change the **Scenes** by selecting **Select Scenes** with Priority: **Target Date**

.. figure:: images/scene_selection.png
   :alt: Selecting scenes for your mosaic.
   :align: center



10. Click Apply. The result should look like the below image.

  a. Notice the collection of circles over the Mai Ndombe study area and that they are all populated with a zero. These represent the locations of scenes in the study area and the numbers of images per scene that are selected. The number is currently 0 because we haven’t selected the scenes yet.

  .. figure:: images/scene_selection_zeros.png
     :alt: Scene selection process showing zeros before selection.
     :align: center

  b. Click the Auto-Select button to auto-select some scenes.

.. figure:: images/auto_select_scenes.png
   :alt: Arrow showing the button for auto selecting scenes.
   :width: 550
   :align: center



11. You may set a minimum and maximum number of images per scene area that will be selected. Increase the minimum to 2 and the maximum to 100. Click **Select Scenes**. If there is only one scene for an area, that will be the only one selected despite the minimum.

.. figure:: images/auto_select_scenes_menu.png
   :alt: Menu for auto selecting scenes.
   :width: 350
   :align: center



12. You should now see imagery overlain with circles indicating how many scenes are selected.

.. figure:: images/imagery_number_scenes.png
   :alt: Example of the imagery with the number of scenes selected
   :width: 450
   :align: center



13. You will notice that the circles that previously displayed a zero now display a variety of numbers. These numbers represent the number of Landsat images per scene that meet your specifications.

    Hover your mouse over one of the circles to see the footprint (outline) of the Landsat scene that it represents. Click on that circle.

.. figure:: images/select_scenes_interface.png
   :alt: The select scenes interface showing 0 available and 4 selected scenes
   :align: center



14. In the window that opens, you will see a list of selected scenes on the right side of the screen. These are the images that will be added to the mosaic. There are three pieces of information for each:

    * Satellite (e.g. L8, L7, L5 or L4)
    * Percent cloud cover
    * Number of days from the target date

  a. To expand the Landsat image, hover over one of the images and click **Preview**. Click on the image to close the zoomed in graphic and return to the list of scenes.
  b. To remove a scene from the composite, click the **Remove** button when you hover over the selected scene.

.. figure:: images/remove_preview_scenes.png
   :alt: Removing or previewing selected scenes.
   :align: center



.. figure::images/scene_preview.png
   :alt: Scene preview screen.
   :align: center



15. On the left hand side, you will see **Available Scenes,** which are images that will not be included in the mosaic but can be added to it. If you have removed an image and would like to re-add it or if there are additional scenes you would like to add, hover over the image and click **Add.**

  a. Once you are satisfied with the selected imagery for a given area, click **Close** in the bottom right corner.
  b. You can then select different scenes (represented by the circles) and evaluate the imagery for each scene.

.. figure:: images/select_scenes_1.png
   :alt: Select scenes screen showing one available scene and 3 selected scenes
   :width: 450
   :align: center



16. You can also change the composing method using the **CMP** button on the lower right.

  a. Notice that there are several additional options including shadow tolerance, haze tolerance, NDVI importance, cloud masking and cloud buffering.
  b. For this tutorial, we will leave these at their default settings.
  c. If you make changes, click Apply after you’re done.

.. figure:: images/composite.png
   :alt: The composite menu.
   :width: 350px
   :align: center



17. Now we’ll explore the **Bands** dropdown. Click on the **Red Green Blue** at the bottom of the page.

.. figure:: images/arrow_bands.png
   :alt: Arrow pointing at the red, green, blue bands.
   :align: center



18. The below dropdown menu will appear.

  a. Select the **NIR, RED, GREEN** band combination. This band combination displays vegetation as red, with darker reds indicating dense vegetation. Bare ground and urban areas appear grey or tan, while water appears black. NIR stands for near infrared.
  b. Once selected, the preview will automatically show what the composite will look like.
  c. Use the scroll wheel on your mouse to zoom in to the mosaic and then click and drag to pan around the image. This will help you assess the quality of the mosaic.

.. figure:: images/bands_menu.png
   :alt: The band combinations menu.
   :width: 350px
   :align: center



19. The map now shows the complete mosaic that incorporates all of the user-defined settings. Here is an example, yours may look different depending on which scenes you chose.

.. figure:: images/completed_mosaic.png
   :alt: The imagery preview with the completed mosaic shown.
   :width: 450
   :align: center



20. Using what you’ve learned, take some time to explore adjusting some of the input parameters and examine the influence on the output. Once you have a composite you are happy with, we will download the mosaic (instructions follow).

  a. For example, if you have too many clouds in your mosaic, then you may want to adjust some of your settings or choose a different time of year when there is a lower likelihood of cloud cover.
  b. The algorithm used to create this mosaic attempts to remove all cloud cover, but is not always successful in doing so. Portions of clouds often remain in the mosaic.


You can view a demonstration of this approach on `YouTube <https://www.youtube.com/watch?v=N8kIBBE3tdM>`_.


3.2 Creating a mosaic by drawing a polygon
===========================================

We will create a mosaic for an area in the Amazon basin.

1. Navigate to the Process tab, then create a new optical mosaic by selecting Optical Mosaic on the Process menu.
2. Under **Area of Interest:**

  a. Select **Draw Polygon** from the dropdown list.

  .. figure:: images/aoi_dropdown.png
     :alt: Area of interest dropdown menu.
     :width: 450px
     :align: center

  b. Navigate using the map to the State of Rondonia (Brazil) and either draw a polygon around it or draw a polygon within the borders. A smaller polygon will export faster.

  .. figure:: images/rondonia.png
     :alt: A polygon drawn around the State of Rondonia.
     :align: center



3. Now use what you have learned the "Create a Landsat mosaic using select Country/Province" section above to create a mosaic with imagery from the year 2019. Don’t forget to consider which satellites you would like to include and which scenes you would like to include.
4. Your preview should include imagery data across your entire area of interest. Try also to get a cloud-free mosaic.
5. Name your mosaic for easy retrieval.
6. When you’re satisfied with your mosaic, **Retrieve** it to Google Earth Engine using the directions below in "Name and save your recipe and mosaic".

You can view a demonstration of this mosaic creation on `YouTube <https://www.youtube.com/watch?v=HiFOaXoclHQ>`_.


3.3 Name and save your recipe and mosaic
=========================================

1. Now, we will name the ‘recipe’ for creating the mosaic and explore options for the recipe.

  a. You can use this recipe when working with the classification or change detection tools (see e.g. the tutorials here on OpenMRV under processes "Classification" and "Change Detection", and tool "SEPAL").
  b. You can make the recipe easier to find by naming it. Click on the tab in the upper right and type in a new name.
  c. Now let's explore options for the recipe. Click on the three lines in the upper right hand corner.

    * You can **Save the recipe** (SEPAL will do this automatically on retrieval) so that it is available later.
    * You can also **Duplicate the recipe**. This is useful for creating two years of data.
    * Finally you can **Export the recipe**. This downloads a zip file with a JSON of your mosaic specifications.

  d. Click on **Save recipe….** This will also let you rename the mosaic if you choose.

.. figure:: images/save_duplicate_export_recipe.png
   :alt: Save, duplicate, export recipe menu.
   :align: center



2. Now if you click on the three lines icon, you should see an additional option: **Revert to old revision...**

.. figure:: images/revert_to_old_revision.png
   :alt: After saving the menu adds a revert to old revision option.
   :align: center



3. Clicking on this option brings up a list of auto-saved versions from SEPAL. You can use this to revert changes if you make a mistake.

   Now, when you open SEPAL and click the Search option, you will see a row with this name that contains the parameters you just set.

.. figure:: images/revision_menu.png
   :alt: Revisions menu dropdown.
   :align: center



4. Finally, we will save the mosaic itself. This is called ‘retrieving’ the mosaic. This step is necessary to perform analysis on the imagery (e.g. see the tutorials here on OpenMRV under process "Classification" and tool "SEPAL").

   To download this imagery mosaic to your SEPAL account, click the **Retrieve** button.

.. figure:: images/retrieve.png
   :alt: The retrieve button.
   :align: center



.. figure:: images/retrieve_menu.png
   :alt: The retrieve menu
   :align: center



5. A window will appear with the following options:

  a. **Bands to Retrieve:** select the desired bands you would like to include in the download.

    i. Select the **Blue, Green, Red, NIR, SWIR 1 and SWIR 2** bands. These are visible spectrum and infrared data collected by Landsat.
    ii. Other bands that are available include Aerosol, Thermal, Brightness, Greenness, and Wetness.
    iii. Metadata on Date, Day of Year, and Days from Target can also be selected.

  b. **Scale:** the resolution of the mosaic. Landsat data is collected at 30m resolution, so we will leave the slider there.
  c. **Retrieve to:** Sepal Workspace is the default option. Other options may appear depending on your permissions.

6. When you have the desired bands selected, click **Retrieve**.

7. You will notice the **Tasks** icon is now spinning. If you click on it, you will see the data retrieval is in process. This step will take some time.

.. figure:: images/retrieval_task.png
   :alt: Retrieval task being carried out
   :align: center



.. warning::
   If you are retrieving multiple mosaics, be sure to retrieve your mosaics using different names. If you do not change the recipe name between retrieving mosaics, the export may fail since both mosaics have the same name.



3.4 Finding your Earth Engine Asset
====================================

For other tutorials hosted on OpenMRV, you may need to know how to find your Earth Engine Asset.

1. Navigate to https://code.earthengine.google.com/ and login.
2. Navigate to your **Assets** tab in the left hand column.
3. Under **Assets,** look for the name of the mosaic you just exported.
4. Click on the mosaic name.
5. You will see a window with information about your mosaic pop up.
6. Click on the two overlapping box icon to copy your asset’s location.

.. figure:: images/mosaic_information.png
   :alt: Your mosaic’s information pane.
   :align: center


4. Frequently Asked Questions (FAQs)
-------------------------------------

**Where can I find more information about Landsat bands?**

More information on these can be found at: https://landsat.gsfc.nasa.gov/landsat-data-continuity-mission/.

==========================================

.. figure:: images/cc.png



This work is licensed under a `Creative Commons Attribution 3.0 IGO <https://creativecommons.org/licenses/by/3.0/igo/>`_

Copyright 2021, World Bank

This work was developed by Karen Dyson under World Bank contract with Spatial Informatics Group, LLC for the development of new Measurement, Reporting, and Verification related resources to support countries’ MRV implementation.

| Attribution
Dyson, K. 2021. Mosaic generation with SEPAL. © World Bank. License: `Creative Commons Attribution license (CC BY 3.0 IGO) <https://creativecommons.org/licenses/by/3.0/igo/>`_

.. figure:: images/wb_fcpf_gfoi.png
