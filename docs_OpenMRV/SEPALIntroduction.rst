.. Andrea, add metadata here!

---------------------------------------
An introduction to SEPAL
---------------------------------------

1. Background
--------------

The System for Earth Observation Data Access, Processing, & Analysis for Land Monitoring (SEPAL) is a web based cloud computing platform that enables users to create image composites, process images, download files, create stratified sampling designs, and more all from your browser. SEPAL is a system for earth observations, data access, processing & analysis for land monitoring, which is a cloud-based computing software designed by the United Nation’s Food and Agricultural Organization (FAO) to aid in remote sensing applications in developing countries. SEPAL is part of the Open Foris suite of tools. Geoprocessing is possible via Jupyter, JavaScript, R, R Shiny apps, and Rstudio. SEPAL also integrates with Collect Earth Online (CEO) and the Google Earth Engine (GEE).

SEPAL provides a platform for users to access satellite imagery (Landsat and Sentinel-2) and perform change detection and land cover classifications using a set of easy-to-use tools. SEPAL was designed to be used in developing countries where internet access is limited and computers are often outdated and, thus, inefficient for processing satellite imagery. It achieves this by drawing on a cloud-based supercomputer, which enables users to process, store, and interpret large amounts of data. Many more advanced functions than what we will cover here are available in SEPAL for more advanced users.

SEPAL integrates with CEO and GEE. CEO, is a free and open-source image viewing and interpretation tool, suitable for projects requiring information about land cover and/or land use. CEO enables simultaneous visual interpretations of satellite imagery, providing global coverage from MapBox and Bing Maps, a variety of satellite data sources from Google Earth Engine, and the ability to connect to your own Web Map Service (WMS) or Web Map Tile Service (WMTS). The full functionality is implemented online, no desktop installation is necessary. CEO allows institutions to create projects and leverage their teams to collect spatial data using remote sensing imagery. Use cases include historical and near-real-time interpretation of satellite imagery and data collection for land cover/land use model validation.

GEE combines a multi-petabyte catalog of satellite imagery and geospatial datasets with planetary-scale analysis capabilities and makes it available for scientists, researchers, and developers to detect changes, map trends, and quantify differences on the Earth's surface. The code portion of GEE (called Code Editor) is a web-based IDE for the Earth Engine JavaScript API. Code Editor features are designed to make developing complex geospatial workflows fast and easy. The Code Editor has the following elements: JavaScript code editor; a map display for visualizing geospatial datasets; an API reference documentation (Docs tab); Git-based Script Manager (Scripts tab); Console output (Console tab); Task Manager (Tasks tab) to handle long-running queries; Interactive map query (Inspector tab); search of the data archive or saved scripts; and geometry drawing tools.

2. Learning objectives
-----------------------

In this tutorial, you will be introduced to the SEPAL interface. You will learn how to access SEPAL’s features to facilitate the remote sensing tasks.

* Navigate the SEPAL interface
* Learn about the functionality of SEPAL
* Set up accounts for SEPAL, CEO, and GEE

2.1 Pre-requisites
===================

* Internet access


3. Tutorial: An introduction to SEPAL
--------------------------------------

3.1 Sign up to SEPAL
=====================

|

.. image:: images/sepal_splash_page.png
   :alt: Sepal splash page.
   :align: center

|

You can request an account by visiting `sepal.io <sepal.io>`_ and clicking “Sign Up”. This will take you to a Google Doc signup form to fill out. You will be set up with an account within a day or so.

.. image:: images/request_sepal.png
   :alt: Request access to sepal.io
   :align: center

|

1. If you do not have a SEPAL account, you can request access here: http://tinyurl.com/fao-sepal.

2. To request access to SEPAL, you will simply need to enter your email address, name, institution or country and a brief explanation of why you want to use SEPAL.

3.2 Sign up to CEO
===================

1. In your browser window, navigate to https://collect.earth/. CEO supports Google Chrome, Mozilla Firefox, and Microsoft Edge.

2. Click **Login/Register** on the upper right.

3. To set up a new account, click on **Register a new account** and follow the instructions.

4. When you have an account, login with your email and password.

5. If you forget your password, click on **Forgot your password?** and follow the instructions.

3.3 Sign up to GEE
===================

Signing up for Google Earth Engine is required in order to properly export images and data products from SEPAL.

1. You will need to have a Google email in order to sign up. If you don’t have one already, you can set one up here: http://mail.google.com/mail/signup.

2. To request a GEE account, please visit https://earthengine.google.com/new_signup/.

3. Once you have a Google Earth Engine account, you can access GEE here: https://code.earthengine.google.com/.

3.4. Open SEPAL
================

1. Navigate to `https://sepal.io/ <https://sepal.io/>`_ to open SEPAL.
2. Type in your **Username** and **Password** and click **Login**.

.. image:: images/sepal_login.png
   :alt: SEPAL login page
   :align: center

|

.. note::
   When working in SEPAL, do not click your browser’s back button. This will go back to the previous webpage. Use the buttons within SEPAL to navigate to previous pages. There may also be an arrow in the upper left or right-hand corner of the SEPAL interface to navigate to a previous window.

3.5 SEPAL interface
====================

1. Once you are logged in, you will see the following screen. Notice that your username is displayed in the bottom right of the window.

.. image:: images/sepal_home.png
   :alt: SEPAL home screen
   :align: center

|

2. There are four main navigation tabs in the dock on the left side of the screen.

  a. **Process:** select imagery and create mosaics.
  b. **Files:** navigate through your personal SEPAL folders. This is where you can download or delete data, as well as visualize it using the Data Visualization link.
  c. **Terminal:** access to the command line for the LINUX server.
  d. **Apps:** links to a variety of pre-loaded tools.

3. At the lower left is the red **Tasks** tab. Clicking on this brings up a list of currently running tasks.

4. **Account Information** can be found in the bottom right of the webpage by clicking the button that shows your username. This opens an overlay that displays important user account information.

5. You can edit your user account info, including Name, Password, Email and Organization here.

   Click **Save** to make those changes permanent. However, you cannot edit your Username in this interface.

   Change the Google Account associated with your SEPAL account by clicking **Use my own Google Account** and following the instructions. SEPAL relies on Google Drive as a storage space for data accessed through the platform. Any imagery tiles or mosaics that you “retrieve” will first be saved to a Google Drive account before you can visualize and process them in SEPAL.

.. note::
   Be sure to connect your Google Account in order to be able to Retrieve Mosaics. You should use the same account you used to sign up for Google Earth Engine.

6. Next to your **Account Information** is a section called **User Report**, represented by the **$ X/h**. This shows you the allotted budgets you have. An instance refers to any of the various processes that you can perform in SEPAL. If you are running any processes in your current session, they will show up here under Sessions.

.. image:: images/user_report_panel.png
   :alt: User Report panel.
   :width: 350px
   :align: center

|

3.6 The Process tab
====================

1. Click the **Process** tab on the left side of the window.

.. image:: images/process_tab_location.png
   :alt: Arrow pointing out the process tab location
   :align: center

|

2. You should now see four options in the center of the screen.

  a. **Optical Mosaic** allows you to create a mosaic using Landsat and/or Sentinel 2 data.
  b. **Radar Mosaic** allows you to create a mosaic using Sentinel 1 data.
  c. **Classification** allows you to use a random forest model to classify images from SEPAL or GEE.
  d. **Time Series** allows you to download time series information to your SEPAL storage.

3. When you click on one of these options, it will open a new tab with the GUI interface that allows you to specify your desired options.

3.7 The Files tab
==================

1. Click the green **Files** tab on the left side of the window. This will display all of your files in SEPAL.

2. For example, click the **downloads** folder to expand it. This will display the folders containing any of the data you have downloaded in SEPAL. If you have not downloaded mosaics in SEPAL yet, then this folder will be empty.

.. image:: images/files_menu.png
   :alt: The files menu
   :align: center
   :width: 350

|

3. Notice that there are four buttons at the top right of the window. The three rightmost buttons are inactive, but activate when you select a file.

  a. The left button will show hidden files (files and folder names starting with ‘.’).
  b. The second button will download selected data to your local computer.
  c. The third button will delete the selected folder or file.
  d. The last button will clear your selection.

3.8 The Terminal tab
=====================

1. Click the **Terminal** tab on the left side of the screen.

2. This links you to the Linux command line that you can use in a variety of ways to manage data, load data from an outside location or process data using a series of commands.

3. When you initially load the Terminal, you will see information about your usage and the available types of instances you can initialize.

4. One of the most important features of the Terminal is the ability to increase your instance size. The default instance is not sufficient for analyzing large amounts of data, for example running a classification on a large area.

  a. To increase the size of your instance, first examine the “Available instance types” table. This is updated periodically but an example from September of 2020 is shown below.
  b. Choose an instance Type that fits your needs. Frequently a t2 or m2 is sufficient and cost effective.
  c. Next to the “Select (t1):” text, type in ‘t2’ or your chosen instance type.
  d. Press Enter on your keyboard.
  e. Wait for the new instance to start. This will take several minutes.

.. image:: images/terminal.png
   :alt: The terminal page, including an example of changing the instance
   :align: center
   :width: 450

|

3.9 The Apps tab
-----------------

1. Click the **Apps** tab on the left side of the screen. This will open up a screen that shows applications that you can access through SEPAL.

.. image:: images/apps_interface.png
   :alt: The Apps interface
   :align: center

|

2. This will bring up a list of apps you can run in SEPAL. More information about each app is found by clicking on the “i” on the right hand side. Some of the apps include:

  * **R Studio:** provides access to R environment where you can run processing scripts and upload data to your SEPAL folder.
  * **Stratified Area Estimator- Design:** tool for creating stratified designs to estimate areas.
  * **Stratified Area Estimator- Analysis:** tool for analyzing the results of your stratified design sampling to estimate areas.
  * **Geo Processing- Beta:** offers a selection of easy-to-use change detection and segmentation tools.
  * **BFAST Explorer:** tool for performing pixel-based time series analysis of Landsat Surface Reflectance data.


4. References
--------------

* The SEPAL wiki, found online at https://github.com/openforis/sepal/wiki
* Gomes, V.C., Queiroz, G.R. and Ferreira, K.R., 2020. An overview of platforms for big earth observation data management and analysis. Remote Sensing, 12(8), p.1253.

=======================

.. Andrea, insert footer information here!
