=================================
Module 3. Image change detection
=================================

.. warning::
   THIS MODULE IS UNDER CONSTRUCTION.

   Recent changes to SEPAL mean that exiting new content is coming soon! Watch this space for the new Biota and Forest Cover Change tools.

Image change detection allows us to understand differences in the landscape--or more correctly, in the satellite images taken of the landscape--over time. There are many questions that change detection methods can help answer, including “When did deforestation take place?” and “How much forest area has been converted to agriculture in the past 5 years?”

Most methods for change detection use algorithms backed by statistical methods to extract and compare information in the satellite images. To conduct change detection then, we need multiple mosaics or images, each one representing a point in time. Here, we will describe how to detect change between two dates using a simple model, however this theory can be expanded to include more dates. In addition, we’ll describe time series analysis, which generally looks at longer periods of time.

The objective of this module is to become associated with methods of detecting change for an area of interest using the SEPAL platform. This will build upon and incorporate what we have covered in the previous modules including: creating mosaics, creating training samples, and classifying imagery. This module is split into two exercises. The first addresses change detection using two dates, and the second more advanced methods using time series analysis with the BFAST algorithm and LandTrendr. At the end of this module you will know how to conduct a two-date change detection in SEPAL, have a basic understanding of the BFAST tool in SEPAL, and be familiar with TimeSync and LandTrendr.

This module should take you approximately 3 hours.

----------------------------------------
Exercise 3.1. Two date change detection
----------------------------------------

In this Exercise, you will learn how to conduct a two-date change detection in SEPAL. This approach uses the same classification algorithm you used in Module 2. This approach can be used with more than two dates if you so choose in the future.

In this example, you will create optical mosaics and classify them, building on skills learned in Modules 1 and 2. Alternatively, you may also use two classifications from your own research area.

+------------------------------------+-----------------------------------+
| Objectives                         | Prerequisites                     |
+====================================+===================================+
| Learn how to conduct a two-date    | SEPAL account                     |
| change detection                   |                                   |
+------------------------------------+-----------------------------------+
| Build on skills learned in         | Complete Modules 1 & 2 or be      |
| Modules 1 & 2                      | familiar with the skills covered  |
+------------------------------------+-----------------------------------+

Part 1. Create mosaics for change detection
--------------------------------------------

Before we can identify change, we first need to have images to compare. We will create two mosaics of Sri Lanka, generate some training data, and then classify the mosaics. This is discussed in detail in Modules 1 & 2.

1. Open the **Process** menu
2. Click on **Optical Mosaic,** or click the **green plus symbol** to open the **Create Recipe** menu and then click on **Optical Mosaic.**

  a. Choose **Sri Lanka** for the Area of interest (AOI).
  b. Select 2015 for the Date (DAT).
  c. Select Landsat 8 (L8) as the source (SRC).
  d. In the Composite (CMP) menu, ensure the surface reflectance **(SR) correction** is selected and median is the compositing method.

3. Click **Retrieve Mosaic** and select **Blue, Green, Red, NIR, SWIR1, SWIR2,** then select Google Earth Engine Asset, and lastly click retrieve.

.. note::
   If you don’t see the Google Earth Engine asset option, you’ll need to connect your Google account to SEPAL by clicking on your user name in the lower right.



.. figure:: images/retrieval_mosaic.png
   :alt: The retrieval screen for mosaics.
   :width: 450
   :align: center



4. Repeat steps 2 & 3 but change the **Date** parameter to 2020.

.. warning::
   Be sure to retrieve your mosaics using different names. If you do not change the name between retrieving the 2015 and 2020 mosaics, the export may fail since both mosaics have the same name.

.. note::
   It may take a significant amount of time before your mosaics finish exporting.


You can view a demonstration of creating these mosaics on `YouTube <https://www.youtube.com/watch?v=X6bRlgXpTnM>`_.

.. raw:: html

   <iframe width="600" height="280" src="https://www.youtube.com/embed/X6bRlgXpTnM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


Part 2. Start the classification
---------------------------------

Now we will begin the classification, as we did in module 2. There are multiple pathways for collecting training data. Using desktop GIS, including QGIS and ArcGIS, to create a layer of points is one common approach. Using GEE is another approach. You can also use CEO to create a project of random points to identify (see detailed directions in Module 4.1 Part 2). All of these pathways will create .csv or an GEE table that you can import into SEPAL to use as your training data set.

However, SEPAL has a built-in reference data collection tool in the classifier. This is the tool you used in Module 2, and we will again use this tool to collect training data. Even if you use a .csv or GEE table in the future, this is a helpful feature to collect additional training data points to help refine your model.

1. In the **Process** menu, click the green plus symbol and select **Classification.**
2. Add the two Sri Lanka optical mosaics for classification:

  a. Click **+ Add** and choose either **Saved Sepal Recipe** or **Earth Engine Asset** (recommended).

    i. If you choose **Saved Sepal Recipe**, simply select your Module 2 Amazon recipe.
    ii. If you choose **Earth Engine Asset**, enter the Earth Engine Asset ID for the mosaic. The ID should look like “users/username/SriLanka2015”.

        Remember that you can find the link to your Earth Engine Asset ID via Google Earth Engine’s Asset tab (see Exercise 2.2 Part 2).

  b. Select bands: Blue, Green, Red, NIR, SWIR1, & SWIR2. You can add other bands as well if you included them in your mosaic.
  c. You can also include **Derived bands** by clicking on the green button on the lower left.
  d. Click **Apply**.
  e. Repeat steps a-d above for your 2020 optical mosaic and click **Next**.

.. figure:: images/two_assets.png
   :alt: Two assets ready for classification.
   :align: center

.. warning::
   Selecting **Saved Sepal Recipe** may cause an error stating "Google Earth Engine error: Failed to create preview" at the final stage of your classification. This occurs because GEE gets overloaded. If you encounter this error, please retrieve your classification as described in Exercise 2.2.

You can view a demonstration of setting up this classification on `YouTube <https://www.youtube.com/watch?v=2i391dPnCRY>`_.

.. raw:: html

   <iframe width="600" height="280" src="https://www.youtube.com/embed/2i391dPnCRY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



Part 3. Collect change classification training data
---------------------------------------------------------------

Now that we have the mosaics created, we will collect change training data. While more complex systems can be used, we will consider two land cover classes that each pixel can be in 2015 or 2020: forest and non-forest. Thinking about change detection, we will use three options: stable forest, stable non-forest, and change. That is, between 2015 and 2020 there are four pathways: a pixel can be forest in 2015 and in 2020 (stable forest); a pixel can be non-forest in 2015 and in 2020 (stable non-forest); or it can change from forest to non-forest or from non-forest to forest. If you use this manual to guide your own change classification, remember to log your decisions including how you are thinking about change detection (what classes can change and how), and the imagery and other settings used for your classification.

.. figure:: images/land_cover_flow_chart.png
   :alt: A land cover change flow chart.
   :width: 450
   :align: center



1. In the Legend menu, click **+ Add** This will add a place for you to write your first class label.

  a. You will need three legend entries.
  b. The first should have the number 1 and a Class label of Stable Forest.
  c. The second should have the number 2 and a Class  label of Stable Non-forest.
  d. The third should have the number 3 and a Class label of Change.
  d. Choose colors for each class as you see fit.
  e. Click **Close**.

.. figure:: images/3_classes.png
   :alt: Classification legend.
   :align: center



2. Now, we’ll create training data. First, let's pull up the correct imagery. Click on "Select layers to show." As a reminder, available base layers include SEPAL (Minimal dark Sepal default layer), Google Satellite, and Planet NICFI composites.

  a. We will use the Planet NICFI composites for this example. The composites are available in either RGB or false color infrared (CIR). Composites are available monthly after September 2020 and for every 6 months prior back till 2015.
  b. Select Dec 2015 (6 months). Both RGB and CIR will be useful, so choose whichever you prefer.
  c. You can also select "Show labels" to enable labels that can help you orient yourself in the landscape.
  d. You will need to switch between this Dec 2015 data and the Dec 2020 data to find stable areas and changed areas.

.. note::
   If you have collected data in QGIS, CEO, or another program, you can skip the following steps. Simply click on **TRN** in the lower right. Click **+ Add** then upload your data to SEPAL. Then skip ahead to Step 12.

3. Now click on the point icon. When you mouse over this icon, it says "Enable reference data collection."
4. With reference data collection enabled, you can start adding points to your map.
5. Use the scroll wheel on your mouse to zoom in to the study area. You can click-hold and drag to pan around the map. Be careful though, as a single click will place a point on the map.

   If you accidentally add a point, you can delete it by clicking on the red **Remove** button.

6. Collect training data for the "Stable Forest" class. Place points where there is forest in both 2015 and 2020 imagery.
7. Collect training data for the "Stable Non-forest" class. Place points where there is not forest in either 2015 or 2020. You should include water, built up areas, bare dirt, and agricultural areas in your points.
8. Collect training data for the "Change" class.

  a. If you are having a hard time finding areas of change, you can use the Google satellite imagery to help.

    i. Areas of forest loss often appear as black or dark purple patches on the landscape.
    ii. Be sure to always check the 2015 and 2020 Planet imagery to verify Change.

  b. The CIR (false color infrared) imagery from Planet can also be helpful in identifying areas of change.
  c. You can also use SEPAL's on-the-fly classification to help after collecting a few Change points.

    i. If the classification does not appear after collecting the Stable Forest and Stable Non-forest classes, click on the "Select layers to view" icon.
    ii. Toggle the "Classification" option off, and then on again.
    iii. You may need to click on "CLS" on the bottom right of the screen, then click "Close" to get the classification map to appear.
    iv. With the Classification map created, you can find change pixels and confirm whether they are change or not by comparing 2015 and 2020 imagery.

  d. One trick for determining change is to place a "Change" point in an area of suspected change. Then you can compare 2015 and 2020 imagery without losing the place you were looking at. If it is not Change, you can switch which classification you have identified the point as.

.. figure:: images/finding_change.png
   :alt: Using Google imagery to examine areas for change.
   :align: center

9. Continue collecting points until you have approximately 25 points for Forest and Non-forest classes and about 5 points for the Change class. More is better. Try to have your points are spread out across Sri Lanka.
10. If you need to modify classification of any of your data points, you can click on the point to return to the classification options. You can also remove the point in this way.
11. When you are happy with your data points, click on the **AUX** button in the bottom right. Select "Terrain" and "Water". This will add auxiliary data to the classification.
12. Click on the **CLS** button in the bottom right. You can change your classification type to see how the output changes.
8. If it has not already, SEPAL will now load a preview of your classification.

.. figure:: images/change_detection_model_preview.png
   :alt: A preview of the change detection model output.
   :width: 450
   :align: center



.. note::
   If any of the previous sections is unclear, review Modules 1 or 2 for more detailed explanations of how to process mosaics, and collect training data with CEO.

You can view a demonstration of collecting training data on `YouTube <https://www.youtube.com/watch?v=rqFvk5T3tzA>`_.

.. raw:: html

   <iframe width="600" height="280" src="https://www.youtube.com/embed/rqFvk5T3tzA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



Part 3. Two date classification retrieval
-------------------------------------------

Now that the hard work of setting up the mosaics and creating and adding the training data is complete, all that is left to do is retrieve the classification.

1. To retrieve your classification as an EE asset, click the cloud icon in the upper right to open the **Retrieve** panel.
2. Select **Google Earth Engine Asset** or **SEPAL Workspace.** Select GEE Asset if you would like to share your map or if you would like to use it for further analysis. Select SEPAL Workspace if you would like to use the map internally only.
3. Choose 30 m resolution.
4. Select the Class, Class probability, Forest % and Non-forest % bands.
5. Click **Retrieve.**

You can view a demonstration of completing and exporting this classification on `YouTube <https://www.youtube.com/watch?v=wJSSSs5tod0>`_.

.. raw:: html

   <iframe width="600" height="280" src="https://www.youtube.com/embed/wJSSSs5tod0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>





Part 4: Quality assurance and quality control
----------------------------------------------

Quality assurance and quality control, commonly referred to as QA/QC, is a critical part of any analysis. There are two approaches to QA/QC: formal and informal. Formal QA/QC, specifically sample-based estimates of error and area are described in Module 4. Informal QA/QC involves qualitative approaches to identifying problems with your analysis and classifications to iterate and create improved classifications. Here we’ll discuss one approach to informal QA/QC.

Following analysis you should spend some time looking at your change detection in order to understand if the results make sense. This allows us to visualize the data and collect additional training points if we find areas of poor classification. Other approaches not covered here include visualizing the data in Google Earth Engine or in another program, such as QGIS or ArcMAP.

With SEPAL you can examine your classification and collect additional training data to improve the classification.

.. figure:: images/examine_change_detection_map.png
   :alt: Examining your change detection map
   :align: center



1. Turn on the imagery for your Classification and pan and zoom around the map.
2. Compare your Classification map to the 2015 and 2020 imagery. Where do you see areas that are correct? Where do you see areas that are incorrect?
3. If your results make sense, and you are happy with them, great! Go on to the formal QA/QC in Module 4.
4. However, if you are not satisfied, collect additional points of training data where you see inaccuracies. Then re-export the classification following the steps in Part 3.


**Congratulations! You have learned how to conduct a two-date change detection classification in SEPAL.**

-----------------------------------
Exercise 3.2. Forest Cover Changes
-----------------------------------

.. warning::
   Watch this space! New content coming soon!

-------------------------------------------------------
Exercise 3.3. Other approaches to time series analysis
-------------------------------------------------------

In this exercise, you will learn more about time series analysis. SEPAL has the BFAST option, described first. We also provide information on TimeSync and LandTrendr, products currently only available outside of SEPAL and CEO.

TimeSync integration is coming to CEO in 2021.

+----------------------------------+-----------------------------+
| Objectives                       | Prerequisites               |
+==================================+=============================+
| Learn the basics of BFAST        | SEPAL account               |
| explorer in SEPAL                |                             |
+----------------------------------+-----------------------------+
| Learn about time series analysis |                             |
| options outside of SEPAL         |                             |
+----------------------------------+-----------------------------+

Part 1: BFAST Explorer
-----------------------

Breaks For Additive Seasonal and Trend (BFAST) is a change detection algorithm for time series which detects and characterizes changes. BFAST integrates the decomposition of time series into trend, seasonal, and remainder components with methods for detecting change within time series. BFAST iteratively estimates the time and number of changes, and characterizes change by its magnitude and direction (Verbesselt et al. 2009).

BFAST Explorer is a Shiny app, developed using R and Python, designed for the analysis of Landsat Surface Reflectance time series pixel data. Three change detection algorithms - bfastmonitor, bfast01 and bfast - are used in order to investigate temporal changes in trend and seasonal components, via breakpoint detection. If you encounter any bugs, please send a message to almeida.xan@gmail.com, or create an issue on the GitHub page.

More information can be found online at http://bfast.r-forge.r-project.org/.

1. Navigate to the **Apps** menu by clicking on the wrench icon
2. Type “BFAST” into the search field and select BFAST Explorer
3. Find a location on the map that you would like to run BFAST on.

  a. Click a location to drop a marker, and then click the marker to select it
  b. Select **Landsat 8 SR** from the select satellite products dropdown.
  c. Click **Get Data.** It may take a moment to download all the data for the point

.. figure:: images/BFAST_explorer_interface.png
   :alt: The BFAST Explorer interface.
   :align: center



4. Click the **Analysis** button at the top next to the **Map** button.
5. **Satellite product:** Add your satellite data by selecting them from the satellite products dropdown menu.
6. **Data:** The data to apply the BFAST algorithm to and plot. There are options for each band available as well as indices such as NDVI, EVI, and NDMI. Here select **ndvi.**
7. **Change detection algorithm:** Holds three options of BFAST to calculate for the data series.

  a. **Bfastmonitor** - Monitoring the first break at the end of the time series.
  b. **Bfast01** - Checking for one major break in the time series.
  c. **Bfast** - Time series decomposition and multiple breakpoint detection in tend and seasonal components.

Each BFSAT algorithm methodology has characteristics which affect when and why you may choose one over the other. For instance, if the goal of an analysis is to monitor when the last time change occurred in a forest then “Bfastmonitor” would be an appropriate choice. Bfast01 may be a good selection when trying to identify if a large disturbance event has occurred, and the full Bfast algorithm may be a good choice if there are multiple times in the time series when change has occurred.

8. Select bfastmonitor as the algorithm.
9. You can explore different bands (including spectral bands e.g. b1) along with the different algorithms.

.. figure:: images/BFAST_visualization.png
   :alt: Additional BFAST visualization.
   :align: center



10. You can also download all the time series data by clicking the blue **Data** button. All the data will be downloaded as a .CSV, ordered by the acquisition date.
11. You can also download the time series plot as an image, by pressing the blue **Plot** button. A window will appear offering some raster (.JPEG, .PNG) and a vectorial (.SVG) image output formats.

.. note::
   The black and white flashing is normal.


Part 2. TimeSync and LandTrendr
---------------------------------

Here we will briefly review TimeSync and LandTrendr, two options available outside of SEPAL that may be useful to you in the future. It is outside of the scope of this manual to cover them in detail but if you’re interested in learning more we’ve provided links to additional resources.

**TimeSync**

TimeSync was created by Oregon State University, Pacific Northwest Research Station, the Forest Service Department of Agriculture, and the USFS Remote Sensing Applications Center.

From the TimeSync User manual version 3:

  "TimeSync is an application that allows researchers and managers to characterize and quantify disturbance and landscape change by facilitating plot-level interpretation of Landsat time series stacks of imagery (a plot is commonly one Landsat pixel). TimeSync was created in response to research and management needs for time series visualization tools, fueled by rapid global change affecting ecosystems, major advances in remote sensing technologies and theory, and increased availability and use of remotely sensed imagery and data products..."

TimeSync is a Landsat time series visualization tool (both as a web application and for desktops) that can be used to:

* Characterize the quality of land cover map products derived from Landsat time series.
* Derive independent plot-based estimates of change, including viewing change over time and estimating rates of change.
* Validate change maps.
* Explore the value of Landsat time series for understanding and visualizing change on the earth’s surface.

TimeSync is a tool that researchers and managers can use to validate remotely sensed change data products and generate independent estimates of change and disturbance rates from remotely sensed imagery. TimeSync requires basic visual interpretation skills, such as aerial photo interpretation and Landsat satellite image interpretation.”

From TimeSync’s Introduction materials, here is an example output:

.. figure:: images/TimeSync_example.png
   :alt: An example from TimeSync.
   :align: center



For more information on TimeSync, including an online tutorial (for version 2 of TimeSync), go to: https://www.timesync.forestry.oregonstate.edu/tutorial.html. There you can register for an account and work through an online tutorial with examples and watch a recorded TimeSync training session. You can also find the manual for version 3 of TimeSync here: http://timesync.forestry.oregonstate.edu/training/TimeSync_V3_UserManual_doc.pdf, and an introductory presentation here: https://timesync.forestry.oregonstate.edu/training/TimeSync_V3_UserManual_presentation.pdf.


**LandTrendr**

LandTrendr has much the same functionality as TimeSync, but runs in Google Earth Engine. It was created by `Dr. Robert Kennedy <https://ceoas.oregonstate.edu/people/robert-kennedy>`_’s lab with funding from the US Forest Service Landscape Change Monitoring System, the NASA Carbon Monitoring System, a Google Foundation Grant, and U.S. National Park Service Cooperative Agreement. Recent contributors include David Miller, Jamie Perkins, Tara Larrue, Sam Pecoraro, and Bahareh Sanaie (Department of Earth and Environment, Boston University). Foundational contributors include Zhiqiang Yang and Justin Braaten in the Laboratory for Applications of Remote Sensing in Ecology located at Oregon State University and the USDA Forest Service’s Pacific Northwest Research Station.

From Kennedy, R.E., Yang, Z., Gorelick, N., Braaten, J., Cavalcante, L., Cohen, W.B., Healey, S. (2018). Implementation of the LandTrendr Algorithm on Google Earth Engine. Remote Sensing. 10, 691.:

  "LandTrendr (LT) is a set of spectral-temporal segmentation algorithms that are useful for change detection in a time series of moderate resolution satellite imagery (primarily Landsat) and for generating trajectory-based spectral time series data largely absent of inter-annual signal noise. LT was originally implemented in IDL (Interactive Data Language), but with the help of engineers at Google, it has been ported to the GEE platform. The GEE framework nearly eliminates the onerous data management and image-preprocessing aspects of the IDL implementation. It is also light-years faster than the IDL implementation, where computing time is measured in minutes instead of days."

From LandTrendr’s documentation, here’s an example output in the GUI. However, LandTrendr has significant non-GUI data analysis capabilities. For a comprehensive guide to running LT in GEE visit: https://emapr.github.io/LT-GEE/landtrendr.html.

.. figure:: images/LandTrendr.png
   :alt: The LandTrendr interface
   :align: center



**Congratulations! You have completed this introduction to time-series analysis tools.**
