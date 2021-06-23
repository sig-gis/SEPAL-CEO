=================================
Module N. SMFM Deforest
=================================


The DEnse FOREst Time Series (deforest) tool is a method for detecting changes in forest cover in a time series of Earth observation data. As input it takes a time series of forest probability measurements, producing a map of deforestation and an 'early warning' map of unconfirmed changes. The method is based on the 'Baysian time series' approach of `Reiche et al. (2018) <https://www.sciencedirect.com/science/article/abs/pii/S0034425717304959?via%3Dihub>`_.

The tool was designed as part of the Satellite Montioring for Forest Management (SMFM) project. The SMFM project (2017 - 2020) aimed to address global challenges relating to the montioring of tropical dry forest ecosystems, and was conducted in partnership with teams in Mozambique, Namibia and Zambia. For more informaton, see https://www.smfm-project.com/.

Full documentation is hosted at http://deforest.rtfd.io/.

This module should take you approximately **some amount of time**.

----------------------------------------
Exercise N.1. Data preparation
----------------------------------------

For this exercise we will be using the sample data that is included with the tool. Additionally, instructions are given on how to create an time serries of forest probability using tools with the SEPAL platform.

.. csv-table::
   :header: "Objectives","Prerequisites"
   :widths: 20, 20

   "Learn how to use the SMFM Deforest tool", "SEPAL account"
   "","Completed SEPAL modules on mosaics, classification, & time series"

Part 0. (Optional) Jupyter notebook basics
-------------------------------------------

If you are unfamiliar with Jupyter notebooks this section is meant to get you aquatinted enough with the system to successfully run the SMFM Deforest tool. A notebook is significantly different than most SEPAL applications, but they are a powerful tool used in data science and other disciplines.

1. Cells

   Every notebook is broken into *cells*. Cells can come in a few formats, but typically they will be either **markdown** or **code**. Markdown cells are the descriptive text and images that accompany the coded to help a user understand the context and what the code is doing. Conversely, code cells run code or a system operation. There are many different languages which can be used in a Jupyter notebook. For this tool we will be using Python. 


.. figure:: images/notebook_cell.png
   :alt: Example of a Jupyter Notebook cell.
   :width: 450
   :align: center



2. Running cells
   
   To run a cell, click on the cell then locate and click the *Run* button in the upper menu. You can run a cell more quickly using the keyboard shortcut **shift-enter**.

.. figure:: images/notebook_run.png
   :alt: Example running a Jupyter Notebook cell.
   :width: 450
   :align: center


3. Kernel
   
   The kernel is the computation engine that executes the code in the jupyter notebook. In this case it is a python 3 kernel. For this tutorial you do not need to know much about this, but if you notebook freezes or you need to reset for any reason you can find kernel operations on the tool bar menu.

   Restarting the kernel:
     a. Navigate to the tool bar at the top of the notebook and select *Kernel*.
     b. From the dropdown menu, select *restart Kernel and Clear Outputs*

.. figure:: images/notebook_kernel.png
   :alt: Example restarting Jupyter Notebook kernel.
   :width: 450
   :align: center


Part 1. Preparing you data
--------------------------------------------

.. warning::
   SMFM Deforest is still in the process of being adapted for use on SEPAL. The forest probability time series will be derived from existing methods to produce a satellite time series implemented on SEPAL. 


This tutorial will use the demo data that is packaged with the SMFM Deforest tool, but steps are presented on how to use the current SEPAL implementation with the tool. Note though, that the data preparation steps in SEPAL can take many hours to complete. If you are unfamiliar with any of the preparations steps, please consult the relevant modules.

If you already have a times series of percent forest coverage feel free to use that.

A. Download demo data

   1. Navigate to your SEPAL **Terminal**
   2. Start a new instance or  join your current instance
   3. Clone the deforest github repository to you SEPAL account useing the following command
   
   ``` git clone https://github.com/smfm-project/deforest ``` 
   
B. SEPAL workflow

   1. Create an optical mosaic for your area of interest
   2. Save the mosaic as a recipe
   3. Open a new classification and point to the optical mosaic recipe as the image to classify
   
      1. Select the bands you want to include in the classification
      2. Add forest/non-forest training data
 
         1. Sample points directly in SEPAL
         2. Optionally, use Earth Engine asset 
   
      3. Apply the classifier
      4. Select the **%forest output**
      5. Save the classification as a recipe
   4. Open a new time-series
      1.  Select the same area of interest as your mosaic 
      2.  Choose a date range for the time series 
      3.  In the 'SRC' box select satellites you used in the previous steps and the classification to apply
      4.  Then you can download the time series to your SEPAL workspace
.. note::
   It will take many hours to download the classified time series to your account depending upon how large your area of interest is.

Part 2. Setup
--------------------------------------------

1. Click and run the first cell under the **Setup** header
   
   1. If the help text is outputted beneath the cell move onto the 3rd step. If there is an error continue to step 2.

.. figure:: images/notebook_1_setup.png
   :alt: Successful setup.
   :width: 450
   :align: center

   Successful setup.

2. Install the package via the SEPAL Terminal
   
   1. Navigate to your SEPAL **Terminal**
   2. Start a new instance or  join your current instance
   3. Clone the deforest github repository to you SEPAL account
    ``` git clone https://github.com/smfm-project/deforest ``` 
   4. Return to the SMFM notebook and repeat step 1.



.. figure:: images/clone_deforest.png
   :alt: Cloning a repository via the SEPAL terminal.
   :width: 450
   :align: center

   

3. Take a moment to read through the help document of the deforest tool. In the next part we will explain in more detail some of the parameters.



Part 3. Process the time series
---------------------------------

Processing the time series imagery can be done with a single line of code using the Deforest change.py command line interface.

1. To use the demo imagery you do not need to change any of the inputs, but if you are using a custom time serries you will need to make some modifications. To change the command to point to a custom time series of of percent forest images you will need to update the path to your time serries. 

Original::

   !python3 ~/deforest/sepal/change.py ~/deforest/sepal/example_data/Time_series_2021-03-24_10-53-03/0/ -o ~/ -n sampleOutput -d 12-01 04-30 -t 0.999 -s 6000 -v 

Example path to time serries updated::

   !python3 ~/deforest/sepal/change.py  ~/downloads/PATH_TO_TIME_SERIES/0/ -o ~/ -n sampleOutputT -d 12-01 01-08 -t 0.999 -s 6000 -v 


.. note::
   By default the time series should be downloaded to a **downloads** folder in your home directory and should have another folder in it named **0**. 

2. Parameters

.. csv-table::
   :header: "Name","Switch","Description"
   :widths: 10, 10, 20

   "Output location","-o","output location where images will be saved on SEPAL account"
   "Output name","-n","Output file name prefix"
   "Date range","-d","A date range filter. Dates need to be formatted as '-d MM-DD MM-DD' "
   "Threshold","-t","Set a threshold probability to identify deforestation (between 0 and 1). High thresholds are more strict in the identification of deforestation. Defaults to 0.99."
   "Scale","-s","Scale inputs by a factor of 6000. In a full-scale run this should be set to 10000, here it's used to correct an inadequate classifcation."
   "Verbose","-v","Prints information to the console as the tool is run."

If you would like to use a time frame other than the example update the **date range** switch. 


3. Run the **Process the time series** cell.

   1. By default the tool is set to use verbose (-v) output. With this switch selected as each image is processed a message is sent back to inform us of the progress. 

   This cell runs two commands:
      a. The first line is running the SMFM Deforest change detection algorithm (change.py)
      b. After processing the images we print them out to ensure the program ran successfully.

   .. note::
      The exclamation mark (**!**) is used to run commands using the underlying operating system. When we run *!ls* in the notebook it is the same as running *ls* in the terminal.

Part 3. Data visualization
---------------------------

Now that we have run the deforestation processing chain, we can visualize our output maps. The outputs of the SMFM tool are two images **confirmed** and **warning**. We will look at the confirmed image first.

1. Run the first **Data visualization** cell.

   a. If you changed the name of you output file be sure to update the path on line 8 for the variable *confirmed*

.. figure:: images/confirmations.png
   :alt: Example of a Jupyter Notebook cell.
   :width: 450
   :align: center

   
   The confirmed image shows the years of change that have been detected in the time series. Stable forest is colored green, and non forest is colored yellow, and the change years colored by a blue gradient. 

   It is recommended that the user discards the first 2-3 years of change, or uses a very high quality forest baseline map to mask out locations that weren't forest at the start of the time serries. This is needed since our input imagery is a a forest probability time series which initially considers the landscape as forest.

Next, well check out the deforest warning output.

2. Run the second **Data visualization** cell
   

.. figure:: images/warnings.png
   :alt: Example of a Jupyter Notebook cell.
   :width: 450
   :align: center

   
   This image shows the combined probability of non-forest existing at the end of our time series in locations that have not yet been flagged as deforested. This can be used to provide information on locations that have not yet reached the threshold for confirmed changes, but are looking likely to possible. 



**Congratulations! You have completed this introduction to SMFM Deforest time-series analysis tools.**
