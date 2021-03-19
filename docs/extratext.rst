Part 1. Setting up a training project
--------------------------------------

1. Navigate to https://sepal.io/ceo. You may need to log into SEPAL.
2. Click **Add project.**
3. Type in a unique name for your training dataset, such as “Amazon training data”.
4. Use **TRAINING DATA** as the **Type.**

  * The **Training Data** option enables you to create a project from scratch. To use this method, you will need to identify a set of land cover classes to classify (code list) and you will need to add imagery that will be used to identify the types of land cover. You will then manually place your training data on the map and classify them.
  * **CEP** stands for Collect Earth Project and it contains a collection of training data points that have already been generated and just need to be classified based on the classes defined within the project. It typically contains a customized method for classifying training data that incorporates % cover.

5. Once you select the training data option, you will notice a new parameter: **Scale (m).** This scale refers to the spatial resolution of the imagery you will be classifying to create your map product. Type in 30, as that is the spatial resolution of Landsat. This will create a plot that is 30 m by 30 m.
6. Click the **\+** button to the right of the section that says **Code List.** When you click the **\+** button, an empty row is added to the Code List. You need two rows.

   Add “Forest” and “Non Forest” to the Code List.

.. image:: images/training_data_project_setup.png
   :alt: Training data project setup.
   :align: center

|

7. Add imagery to the CEO project by clicking on **Add a layer.** This is where you can select the background imagery you will use to collect the training data. You can add multiple different types of imagery, as well as different band combinations of the same imagery.

   Select Google Earth Engine (Assets) from the drop down menu.

.. image:: images/add_imagery_layers.png
   :alt: Adding imagery layers.
   :width: 400
   :align: center

|

8. Add your Earth Engine Asset mosaic. We will add a true-color set of bands first.

  a. Name your layer. Try ‘Landsat 8 RGB.’
  b. Paste the link to your mosaic in GEE (see Part 2 in Exercise 2.2).
  c. Type in ‘red, blue, and green’ for bands.
  d. Use 0 and 3000 for min and max. You can alter these values slightly based on band min/max in the Landsat 8 satellite.

9. Add your Earth Engine Asset mosaic, but type in ‘swir1,nir,red’ to get SWIR, NIR, and red bands. Use a min and max of 300 and 3200.
10. You can also add additional band combinations. If you would like to add other versions of this mosaic with different band combinations, repeat steps 5-6, but use different bands and adjust the name according to the bands. For example, try NIR, red, green.
11. There are a number of other imagery options in the **Add a layer** drop down menu. Feel free to experiment with these.

.. note::
   Digital Globe imagery no longer exists.

.. image:: images/GEE_asset_setup.png
   :alt: Google Earth Engine Asset setup
   :align: center

|

12. When you’ve set up the project, click on the **Submit** button.

    Notice that the project is now listed. You can click edit if you want to adjust any of the settings for the project.


    Part 3. Export data As CSV
    ---------------------------

    Now we will download the training data we have collected.

    1. Above your training data points you will see a blue Download CSV button.

    .. image:: images/training_data_points.png
       :alt: Training data points.
       :width: 450
       :align: center

    |

    2. Click the CSV button to download the reference data as a comma separated values format.

      a. You will either be prompted by your browser to choose a location to save the data to.
      b. Or the data will be automatically downloaded to the folder your browser uses for downloads, usually your Downloads folder.

    3. Once downloaded, examine your data by opening it in an application which can view tables, such as Microsoft Excel.

       There are 4 different columns in the table:

      a. id—this is the same unique ID that you can see on the right side of the CEO-SEPAL interface.
      b. YCoordinate and XCoordinate—locational information for all of the training data (in the WGS 84, EPSG 4326, coordinate reference system).
      c. class—land cover class in integer form. Again, 1=Forest and 2=Non-Forest.

    .. image:: images/sample_training_data.png
       :alt: A sample training data file.
       :width: 450
       :align: center

    |

    **Congratulations! You have successfully completed this exercise. You now know how to use SEPAL’s version of Collect Earth Online to create training data for a supervised classification.**

    Part 0. [Optional] Merging Asset Tables
    ----------------------------------------

    To get a more accurate training dataset, consider combining multiple training datasets. For example, if you’re completing these exercises as part of a group training, try combining your training data set with your neighbors’. We will show you how to do this using your .csv files, however if you are more familiar with GEE you can also combine files using code in GEE.

    1. Navigate to your GEE table information as in Exercise 2.3 Part 4.

    .. image:: images/info_page_table_id.png
       :alt: The GEE table information where you can find your asset table id.
       :width: 450
       :align: center

    |

    2. Click on Share.

    .. image:: images/share_asset_table.png
       :alt: The sharing interface for your asset table
       :width: 450
       :align: center

    |

    3. Fill in your neighbor’s email address, set them as a **Reader** or **Writer,** and click **Add.**
    4. Now copy the link and email it to your neighbor. Ask them to send you the link to their table.
    5. Once you have their table’s address, click the table link that you were sent.

      a. Download the fusion table as a CSV just as you did with your own.
      b. Once you have your and their CSVs downloaded, open them in Microsoft Excel.
      c. Copy and paste the contents of your neighbor’s CSV to your own training data CSV.

        i. Do not include their column header.
        ii. Only copy and paste the data.

      d. Save the CSV to your desired location and give it a unique name.

      
  Part 4. [Optional] Uploading your CSV to Google Earth Engine
--------------------------------------------------

For classification, you can either use the CSV we just downloaded or upload your CSV to  Google Earth Engine. To upload it into Google Earth Engine:

1. Navigate to https://code.earthengine.google.com/.

  a. Log into GEE using your account and then navigate to the Assets tab.
  b. Click **New.**
  c. Select **CSV file (.csv)** under the **Table Upload** section.

.. image:: images/GEE_asset_upload.png
   :alt: The Google Earth Engine interface for uploading assets.
   :width: 450
   :align: center

|

2. In the new window that pops up, fill in the requested information.

  a. Select your **CSV file** from your local machine.
  b. Optionally, **rename** the asset.
  c. Choose the **asset id path.** This is the where the asset will be saved once uploaded
  d. Add XCoordinate and YCoordinate to the Advanced options **X column and Y columns.**

.. image:: images/X_Y_fields.png
   :alt: Filling out the X and Y column fields.
   :width: 450

|

3. Click Upload to initiate the upload.

   You may need to rename your csv if the filename has spaces. Do this in your computer’s file system and try again.

4. After a few minutes your upload should be complete!

  a. Check the path where you uploaded your asset to confirm it has successfully uploaded.
  b. Click on the file name.
  c. Make note of your **TableID,** which you will need for Exercise 2.4.

.. image:: images/info_page_table_id.png
   :alt: The information page with your table id.
   :width: 450
   :align: center

|
