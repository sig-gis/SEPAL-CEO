---
title: Sample design and stratification
summary: We will use the SEPAL SAE-Design tool to create a stratified area estimate. The SAE-Design tool will generate a set of stratified random points that are placed in each of the different land cover classes represented in your map. The number of points in each class will be scaled to the area each class covers in the map. The total sample size, the number of points used to validate the map will depend on your expected overall accuracy.
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
- CEO
- Planet Labs
- Sampling design
- Sample design
- Sample selection
- Sample
- Sampling frame
- Stratified
- Simple Random
- Systematic
- Response design
- Survey
- Survey design
- Reference data
- Reference classification
- Reference observations

group:
- category: SEPAL
  stage: Sampling
- category: Collect Earth Online
  stage: Reference data collection
---

---------------------------------
Sample design and stratification
---------------------------------

1. Background
--------------

Stratified random sampling is an easy to use, easy to understand, and well supported sampling design (for more information, see Olofsson et al. 2014.). With stratified random sampling, each class (e.g. land use, land cover, change type) is treated as a strata. Then, a sample is randomly taken from each strata, either in proportion to area, in proportion to expected variance, or in equal numbers across strata.

2. Learning objectives
-----------------------

We will use the SEPAL SAE-Design tool to create a stratified area estimate. The SAE-Design tool will generate a set of stratified random points that are placed in each of the different land cover classes represented in your map. The number of points in each class will be scaled to the area each class covers in the map. The total sample size, the number of points used to validate the map will depend on your expected overall accuracy.

* Generate a stratified random sample.
* Create a CEO project using your stratified random sample.

2.1 Pre-requisites
===================

* A SEPAL account and a Collect Earth Online (CEO) account. Please see the tutorial here on OpenMRV under tool "SEPAL" for an introduction to SEPAL and CEO.
* A previously generated map. Here the process will be demonstrated for the output of the tutorial here on OpenMRV under process "Classification" and tool "SEPAL". This is made available to you as a GEE asset (ID: users/openmrv/Classification_Module2_Amazon), but you will need to first export it to your Google Drive, download it to your local machine, and then upload it to SEPAL following instructions below if you are going to use it in this tutorial. Information about the Export process can be found here on OpenMRV under process "Pre-processing" and tool "GEE".

3. Tutorial: Sample design and stratification
----------------------------------------------

3.1 [Optional] Uploading your classification map
=================================================

You will need to upload a classification map if you did not create a classification map in the tutorials here on OpenMRV under process "Classification" and tools "SEPAL" and "GEE". Alternatively, you can use the GEE asset 'users/openmrv/Classification_Module2_Amazon' (note: you will need to first export this asset to your Google Drive and download it to you local machine prior to uploading it to SEPAL).

There are two tools that can be used to upload files. The first is RStudio, and the second is the File transfer Management app.

1. For either approach, first select the purple wrench **Apps** button. If you have an existing tab open, you may need to click the **plus** sign in the top right.
2. To use RStudio, choose the **R Studio** application. You may be prompted to enter your SEPAL username and password to enter R Studio.

  .. figure:: images/apps_rstudio.png
     :alt: The apps screen, with RStudio shown.
     :align: center

  a. This will open an instance of RStudio, an IDE for the R programming language.
  b. You should see a ‘Files’ tab in the lower right window.

     If not, you may need to adjust the window layout. To do this, move your mouse to the right-hand side of the window where a four-way arrow will appear. Click and drag your mouse to the left to reveal the right pane.

  c. Click the **Upload** button that is located in the lower right side of the R Studio interface (see below).

  .. figure:: images/rstudio_interface.png
     :alt: The RStudio interface in SEPAL.
     :align: center

  d. In the **Upload Files** window, click **Choose File.**
  e. Navigate to the correct location on your drive, select your map and click Open.
  f. Once you’ve selected this file, click **OK** to complete the upload (see below).
  g. You will see your file appear in the list of files in the lower right-hand pane.
  h. You may now close the RStudio instance by clicking the tab’s **x.**

2. To use the File transfer manager, select the **File transfer management** application.

  a. Under Upload to Sepal, click on the drop down **Select table type** menu. Click on the correct file type for your map.
  b. Click on the paperclip icon.
  c. Navigate to the correct location of your map on your drive, select your map and click Open.
  d. Click **Import**

3.2 Creating a stratified random sample
========================================

We will use SEPAL to create a stratified random sample. We will use a raster of your classification either saved to SEPAL (please see the tutorial here on OpenMRV under process "Classification" and tool "SEPAL") or uploaded to SEPAL using the instructions in 3.1 above. This classification is a previously generated map.

If you have a large area you are stratifying, please first increase the size of your instance (if you need an introduction to SEPAL, see the tutorial here on OpenMRV under tool "SEPAL" to see how increase the size of your instace).

A well-prepared sample can provide a robust estimate of the parameters of interest for the population (percent forest cover, for example). The goal of a sample is to provide an unbiased estimate of some population measure (e.g. proportion of area), with the smallest variance possible, given constraints including resource availability. Two things to think about for sample design are: do you have a probability based sample design? That is, does every sample location have some probability of being sampled? And second, is it geographically balanced? That is, are all regions in the study area represented. These factors are required for the standard operating procedures when reporting for REDD+.

These directions will provide a stratified random sample of the proper sampling size.

1. First, navigate to https://sepal.io/ and sign in.
2. Select the **Apps** button (purple wrench).
3. Type ‘stratified’ into the search bar or scroll through the different process apps to find “Stratified Area Estimator--Design”
4. Select **Stratified Area Estimator-Design.** Note that loading the tool takes a few minutes.

.. figure:: images/stratified_area_estimator_design.png
   :alt: Stratified Area Estimator-Design tool.
   :align: center



.. note::
   Sometimes the tool fails to load properly (none of the text loads) as seen below. In this case, please close the tab and repeat the above steps.

   .. figure:: images/fail_stratified_estimator_tool.png
      :alt: Failure of the stratified area estimator tool.
      :align: center



5. When the tool loads properly, it will look like the image below. Read some of the information on the **Introduction** page to acquaint yourself with the tool.

  a. On the **Introduction** page, you can change the language from English to French or Spanish.
  b. The Description, Background, and "How to use the tool" panels provide more information about the tool.
  c. The Reference and Documents panel provides links to other information about stratified sampling, such as REDD Compass.

.. figure:: images/stratified_estimator_interface.png
   :alt: The stratified estimator interface.
   :align: center



6. The steps necessary to design the stratified area estimator are located on the left side of the screen and they need to be completed sequentially from top to bottom.
7. Select **Map input** on the left side of the screen.

  a. In the **Data type** section, click **Input.**
  b. In the **Browse** window that opens, navigate to the saved SEPAL classification or your uploaded classifiation and select it.
  c. Then click **Select.**
  d. Note that the **Output folder** section shows you where in your SEPAL workspace all the files generated from this tutorial will be saved.

8. Next, click **Strata areas** on the left side of the screen.
9. In the **Area calculation** section, select **OFT.** OFT stands for the Open Foris Geospatial Toolkit. R is slower but avoids some errors that arise with OFT.

   If you choose to use OFT, it will return values for the map that are incorrect if your map stored using certain formats (e.g. signed 8 bit). If this is the case, then please use the R option and it will work correctly. If using OFT, always compare the **Display map** with the **Legend labeling** values returned to make sure they match.

.. figure:: images/stratified_estimator_map_legend.png
   :alt: Stratified estimator tool showing the display map and legend and areas filled out.
   :align: center



10. The **“Do you want to display the map”** checkbox allows you to display your geotiff under “Display map”.

    The colors displayed in the SAE-Design tool in this section may be different than what you see elsewhere. Additionally, if your ‘no data’ class is 0, the tool will color this as well.

11. Click the **Area calculation and legend generation** button. This will take a few minutes to run. After it completes, notice that it has updated the **Legend labeling** section of the page.

  a. Next, you will need to adjust the class names in the **Legend labeling** section. Type in the following class names in place of the numeric codes for your Amazon:

     0 = No Data

     1 = Forest

     2 = Non-Forest

  b. Now click **Submit Legend.** The **Legend and Areas** section will now be populated with the map code, map area, and edited class name.
  c. You can now **Rename** and **Download** the area file if you would like. However it will save automatically to your Sepal workspace.

12. When you’re done, click on **Strata selection** on the left panel.
13. Now you need to specify the expected accuracies. You will do this for each class.

  a. You can get more information by clicking the **plus** button to the right of the box that says **What are the expected accuracies?**
  b. Specifying the expected user accuracy helps the program determine which classes might need more points relative to their area.
  c. Some classes are easier to identify--including common classes and classes with clear identifiers like buildings.
  d. Classes that are hard to identify include rare classes and classes that look very similar to one another. Having more classes with low confidence will increase the sample size.

    i. Select the value for classes with high expected user accuracy with **the first slider.** This is set to 0.9 by default, and we’ll leave it there.
    ii. Then, select the value for classes with low expected user accuracy with **the second slider.** This is set to 0.7 by default, and we’ll leave it there as well.

14. Now we need to assign each class to the high or the low expected user accuracy group.

  a. Think about your forest and non-forest classes. Which do you think should be high confidence? Which should be low confidence? Why?
  b. Click on the box under **“high confidence”** and assign your high confidence class(es). **For this tutorial, please assign both Forest & Non-forest to the high confidence class.**
  c. Then, click on the box under **“low confidence”** that appears and assign the corresponding class(es).
  d. If you make a mistake, there’s no way to remove the classes. However, just change one of the sliders slightly, move it back, and the class assignments will have been reset.

.. warning::
   DO NOT assign your No Data class to either high or low confidence.

.. figure:: images/high_low_expected_user_accuracy.png
   :alt: High and low expected user accuracy.
   :align: center



15. When you’re satisfied, click on **Sampling Size** on the left panel.

  a. Now we will calculate the required sample size for each strata.
  b. You can click on the “+” button to get more information.
  c. First we need to set the **standard error of the expected overall accuracy.** It is 0.01 by default, however for this tutorial we will set it to 0.05.

    i. This value affects the number of samples placed in each map class. The lower the value, the more points there are in the sample design. Test this by changing the error from 0.05 to 0.01, and then change it back to point 0.05. Alternatively, you can click the up/down button to the right of the number.
    ii. Note that you can adjust this incrementally with the up/down arrows on the right side of the parameter.

  d. Then determine the **minimum sample size per strata.** By default it is 100. For the purposes of this tutorial we will set it to 20, **but in practice this should be higher.**
  e. You can also check the “Do you want to modify the sampling size” box.
  f. If you would like, you can edit the name of the file & download a csv with the sample design. The file contains the table shown above with some additional calculations. However, SEPAL will automatically save this file.

.. figure:: images/stratified_estimator_sampling.png
   :alt: The stratified estimator sampling size and distribution of samples screen.
   :align: center



16. When you’re ready, click on **Sample allocation** to the left.

  a. The final step will select the random points to sample.
  b. Select **Generate sampling points** and wait until the progress bar in the bottom right finishes. Depending on your map, this may take multiple minutes. A map will pop up showing the sample points. You can pan around or zoom in/out within the sample points map.

    i. The resulting **distribution of samples** should look similar to the below image. These values will vary depending on your map and the standard error of expected overall accuracy you set.
    ii. Sometimes this step fails, no download button will appear, and you will need to refresh the page and restart the process.

.. figure:: images/stratified_estimator_map.png
   :alt: The stratified estimator tool's sample allocation screen.
   :align: center



17. Now fill out the four fields to the right.

  a. You can add additional data by specifying which country the map is in. Here, Leave the **Choose your country name…** section blank.
  b. Specify the **number of operators,** or people who will be doing the classification. Here, leave it set to 1.
  c. The **size of the interpretation box** depends on your data and corresponds to CEO’s sample plot. This value should be set to the spatial resolution of the imagery you classified (Landsat= 30 meters). Here, leave it at 30 m.

18. Click on **Download .csv**.

19. You can also download a .shp file to examine your points in QGIS, ArcGIS, or another GIS program. You can also create a CEO project using a .shp file, however that is outside of the scope of this tutorial.

You can view a demonstration of creating this stratification on `YouTube <https://www.youtube.com/watch?v=mbskeQNjj7A>`_.



3.3 Preparing your CSV for CEO
===============================

For projects with large sample sizes, where you want to have multiple people collecting validation data, or where you want to use specific validation imagery, you will want to create a project through Collect Earth Online (CEO). Note that the TOTAL number of plots you want to sample using a .csv must be 50,000 or less. If you have more plots, break it into multiple projects.

1. Make sure you have downloaded the .csv of your stratified random sample plots.
2. Open your downloaded .csv file in Excel or the spreadsheet program of your choice.
3. First, make sure that your data doesn’t contain a strata of ‘no data’. This can occur if your classification isn’t a perfect rectangle, as seen in this example of Nepal (the red circles are samples that the tool created in the ‘no data’ area). **If you have ‘no data’ rows, return to the SEPAL stratified estimator, and be sure to not include your no data class in the strata selection step.**

.. figure:: images/example_data_sepal_classification.png
   :alt: Example data from the SEPAL classification.
   :align: center



4. Now we need to add the correct columns for CEO. Remember that Latitude is the Y axis and longitude is the X axis. For CEO, the first three columns must be in the following order: longitude, latitude, plotid. The spelling and order matter. If they are wrong CEO will not work correctly.

  a. Rename ‘id’ to PLOTID. You can also add a new PLOTID field by creating a new column labeled PLOTID, and fill it with values 1-(number of rows).
  b. Rename the ‘XCoordinate’ column to ‘LONG’ or ‘LONGITUDE’.
  c. Rename the ‘YCoordinate’ column to ‘LAT’ or ‘LATITUDE’.
  d. Reorder the columns in Excel so that LAT, LONG, PLOTID are the first three columns, in that order.

5. Save your updated .csv, making sure you save it as a .csv and not as an .xlsx file.

You can view an example of preparing the .csv for CEO on `You Tube <https://www.youtube.com/watch?v=6xBjc8wYSNw>`_.

3.4 Creating a CEO project using your CSV
==========================================

1. Navigate to https://collect.earth.

  a. Creating a project in CEO requires you to be the administrator of an institution.
  b. Login to your CEO account. If you’re already the administrator of an institution, navigate to your institution’s landing page by typing in the institution’s name and then clicking on the Visit button.
  c. If you’re not an admin, go ahead and create a new institution.
  d. Click on create new institution from the homepage, then fill out the form & click create institution.

2. When you’re on the institution’s page, click on the “Create New Project” button.
3. This will go to the Create Project interface. We’ll now talk about what each of the sections on this page does.

  a. **TEMPLATE:** This section is used to copy all the information—including project info, area, and sampling design—from an existing published project to a new project.

    i. This is useful if you have an existing project you want to duplicate for another year or location, or if you’re iterating through project design. You can use a published or closed project from your institution or another institutions’ public project.
    ii. The project id is found in the URL when you’re on the data collection page for the project.

  b. Enter the project’s **Name** and **Description.**

    i. The **Name** should be short and will be displayed on the Home page as well as the project’s Data Collection page.
    ii. You should keep the **Description** short but informative.
    iii. The **Privacy Level** radio button changes who can view your project, contribute to data collection, and whether admins from your institution or others creating new projects can use your project as a template.
    iv. Click on any **Project Options** you would like.

  c. **Imagery Selection** allows you to select any of the public or your institutional imagery. The default public imagery includes MapBox and Planet NICFI data.

  d. **AOI:** Under **Plot design**, The project area of interest (AOI) determines where sample plots will be drawn from for your project. This is the first step in specifying a sampling design for your project. There are two main approaches for specifying an AOI and sampling design.

    i. First, using CEO’s built in system.
    ii. Second, creating a sample in another program and importing it into CEO. **This is what we have done.**

  e. **Sample Plot Design:** Here, click the radio button next to .csv.

    i. Click on **Upload,** and upload the .csv of your stratified random sample. Note that the number of plots you want to sample must be 5000 or less.
    ii. Select if you would like round or square plots, and specify the size. For example, you might specify square plots of 30m width in order to match Landsat grid size.

  f. **Sample Point Design:** Under the Sample Design header is really determining the sample point design within each sample plot.

    i. You can choose Random or Gridded, and how many samples per plot or the sample resolution respectively. You can also choose to have one central point.
    ii. Using CEO's built in system, the maximum number of sample points per plot is 200. The maximum total number of sample points for the project across all plots is 50000.

  g. **Survey Design:** This is where you design the questions that your data collectors/photo interpreters will answer for each of your survey plots. Each question creates a column of data. This raw data facilitates calculating key metrics and indicators and contributes to fulfilling your project goals.

    i. **Survey Cards** are the basic unit of organization. Each survey card creates a page of questions on the Data Collection interface. You can preview your survey questions in the right hand pane.
    ii. The basic workflow is: Create new top-level question (new survey card) THEN populate answers THEN create any child questions & answers THEN move to next top-level question (new survey card) & repeat until all questions have been asked.
    iii. You can ask multiple types of questions (including the button—text questions from the Simple interface). You can also add survey rules in the Survey Rules Design panel.
    iv. Broadly, there are four question types and three data types. They are combined into 10 different component types.
    v. The four question types are:

      * Button: This creates clickable buttons, allowing users to select one out of many answers for each sample point.
      * Input: Allows users to enter answers in the box provided. The answer text provided by the project creator becomes the default answer.
      * Radiobutton: This creates radiobuttons, allowing users to select one out of many answers for each sample point.
      * Dropdown: Allows users to select from a list of answers.

    vi. The three data types allowed are:

      * Boolean: Use this when you have two options for a question (yes/no).
      * Text: Use this when you have multiple options which are text strings. They may include letters, numbers, or symbols.
      * Number: Use this when you have multiple options that are numbers, which do not contain letters or symbols.

    vii. First, type in your question in the New question box, such as “Is this forest or non-forest?"
    viii. Then click add survey question.
    ix. A new survey card (Survey Card Number 1) will pop up with your question in it.
    x. You can now add answers.
    xi. Create one answer for each of your land use types. **Here we will use 1 and 2 to match our “Forest” and “Non-forest” in our classification.** Be sure to include all your land use types.
    xiii. You can add additional survey questions if you’d like to experiment. An example of two survey cards is shown below.

.. figure:: images/example_survey_card.png
   :alt: An example survey card setup
   :width: 450
   :align: center



11. When you’re done, click [Create Project].

  a. If you’re successful, you’ll see the review project pane.
  b. The Project AOI will now show the location of a subset of your plots (a maximum number can be displayed).

12. Not shown are the Plot Review and Sample Design, which show a summary of the choices you made or the .csv and .shp files you uploaded. Survey Review shows all the Survey Cards you created, along with the corresponding Component Type, Rules, and Answers.
13. At this point, your project has been created, but it hasn’t been published so that other users can see it.

    There is also review project functionality. As an administrator, you review your unpublished project and make suggestions to the questions etc. before it is published for data collection.

14. You can either click [Publish Project] or [Configure Geo-Dash]. The option to Configure Geo-Dash will be available after you publish your project, as well.

  a. For now, let’s click on Configure Geo-Dash.
  b. A new window or tab will open and you’ll now see the blank Geo-Dash configuration page.
  c. Geo-Dash is a dashboard that opens in a second window when users begin to analyze sample plots. Geo-Dash provides users with additional information to help them interpret the imagery and better classify sample points and plots. The Geo-Dash tab can be customized to show information such as NDVI time series, forest degradation tools, additional imagery, and digital elevation data.
  d. If you click on Geo-Dash Help, You’ll access information about all of the Geo-Dash widgets. This information is also in the CEO user manual.
  e. Add any widgets that you would like for your project. For example, add a NDVI widget following these steps:

    i. Click on Add Widget, then select the Image Collection type.
    ii. Select your basemap imagery.
    iii. Now you’ll see the data dropdown menu. Select NDVI in this menu.
    iv. Now you’ll see the Title--give your widget a title that describes the data.
    v. Select the date range using the calendar widgets or by typing it in.
    vi. When you’re done, click Create.

  f. You can now move the widget by clicking and dragging from the center and resize it by clicking and dragging the lower right-hand corner.
  g. When you’re done adding widgets, close the Geo-Dash window.

15. On the project review page, click publish project.

  a. Collect earth will ask you to confirm, click OK.
  b. You can now visit your project from your institution’s page!

16. For instructions on collecting data, please see the tutorials here on OpenMRV under process "Sampling design" and tools "SEPAL" and "CEO".

You can view a demonstration of creating a CEO project using a .csv on `YouTube <https://www.youtube.com/watch?v=j8eTVqkEcDI>`_.



4. Frequently Asked Questions (FAQs)
-------------------------------------

**I need additional help setting up my CEO project.**

For more information, please see the Institutional Manual available on the collect.earth Support page https://collect.earth/support.

5. References
--------------

Gallego, F.J., 2004. Remote sensing and land cover area estimation. International Journal of Remote Sensing, 25(15), pp.3019-3047. https://doi.org/10.1080/01431160310001619607

GFOI. 2016. Integration of remote-sensing and ground-based observations for estimation of emissions and removals of greenhouse gases in forests: Methods and Guidance from the Global Forest Observations Initiative, Edition 2.0, Food and Agriculture Organization, Rome. Available online at https://www.fs.fed.us/rm/pubs_journals/2020/rmrs_2020_espejo_a001.pdf

Chapter 2 and Chapter 3 of: GFOI (2020) Integrating remote-sensing and ground-based observations for estimation of emissions and removals of greenhouse gases in forests: Methods and Guidance from the Global Forest Observations Initiative. Edition 3.0.  Available online at https://www.reddcompass.org/download-the-mgd

IPCC. 2006. Guidelines for national Greenhouse Gas Inventories. Volume 4: Agriculture, Forestry and Other Land Use. http://www.ipcc-nggip.iges.or.jp/public/2006gl/vol4.html

Olofsson, P., Foody, G.M., Herold, M., Stehman, S.V., Woodcock, C.E. and Wulder, M.A., 2014. Good practices for estimating area and assessing accuracy of land change. Remote Sensing of Environment, 148, pp.42-57. https://doi.org/10.1016/j.rse.2014.02.015

REDD Compass: https://www.reddcompass.org/


=======================================

.. figure:: images/cc.png

This work is licensed under a `Creative Commons Attribution 3.0 IGO <https://creativecommons.org/licenses/by/3.0/igo/>`_

Copyright 2021, World Bank

This work was developed by Karen Dyson under World Bank contract with the Food and Agriculture Organization and Spatial Informatics Group, LLC for the development of new Measurement, Reporting, and Verification related resources to support countries’ MRV implementation.

| Attribution
Dyson, K. 2021. Sample design and stratification. © World Bank. License: `Creative Commons Attribution license (CC BY 3.0 IGO) <https://creativecommons.org/licenses/by/3.0/igo/>`_

.. figure:: images/wb_fcpf_gfoi.png

|
