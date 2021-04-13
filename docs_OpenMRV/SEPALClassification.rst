===============================
Module 2. Image classification
===============================

The main goal of this Module is to construct a single-date land cover map by classification of a Landsat composite generated from Landsat images. Image classification is frequently used to map land cover, describing what the landscape is composed of (grass, trees, water, impervious surface), and to map land use, describing the organization of human systems on the landscape (farms, cities, wilderness). Learning to do image classification well is extremely important and requires experience. So here is your chance to build some experience. You will first consider the types of land cover classes you would like to map and the amount of variability within each class.

There are both supervised (uses human guidance including training data) and unsupervised (no human guidance) classification methods. The random forest approach used here uses training data and is thus a supervised classification method.

There are a number of supervised classification algorithms that can be used to assign the pixels in the image to the various map classes. One way of performing a supervised classification is to utilize a Machine Learning algorithm. Machine Learning algorithms utilize training data combined with image values to learn how to classify pixels. Using manually collected training data, these algorithms can train a classifier, and then use the relationships identified in the training process to classify the rest of the pixels in the map. The selection of image values (e.g., NDVI, elevation, etc.) used to train any statistical model should be well thought out and informed by your knowledge of the phenomenon of interest to classify your data (e.g., into forest, water, other, and clouds).

In this module, we will create a land cover map using supervised classification in SEPAL. We will train a random forest machine learning algorithm to predict land cover with a user generated reference data set. This data set is collected either in the field or manually through examination of remotely sensed data sources such as aerial imagery. The resulting model is then applied across the landscape. You will complete an accuracy assessment of the map output in Module 4.

Before starting your classification, you will need to create a response design with details about each of the land covers / land uses that you want to classify (Exercise 2.1); create mosaics for your area of interest (in Exercise 2.2 we will use a region of Brazil); and collect training data for the model (Exercise 2.3). Then, in Exercise 2.4 we will run the classification and examine our results.

The workflow in this module has been adapted from exercises and material developed by Dr. Pontus Olofsson, Christopher E. Holden, and Eric L. Bullock at the Boston Education in Earth Observation Data Analysis in the Department of Earth & Environment, Boston University. To learn more about their materials and their work, visit their github site at https://github.com/beeoda.

At the end of this module you will have a classified land use land cover map.

This module takes approximately 4 hours to complete.

-------------------------------------------------------------------
Exercise 2.3. Creating a classification & training data collection
-------------------------------------------------------------------

In this exercise, we will learn how to start a classification process and collect training data. These training data points will become the foundation of the classification in Exercise 2.4. High quality training data is necessary to get good land cover map results. In the most ideal situation, training data is collected in the field by visiting each of the land cover types to be mapped and collecting attributes. When field collection is not an option, the second best choice is to digitize training data from high resolution imagery, or at the very least for the imagery to be classified.

In general, there are multiple pathways for collecting training data. Using desktop GIS, including QGIS and ArcGIS, to create a layer of points is one common approach. Using GEE is another approach. You can also use CEO to create a project of random points to identify (see detailed directions in Module 4.1 Part 2). All of these pathways will create .csv or an GEE table that you can import into SEPAL to use as your training data set.

However, SEPAL has a built-in reference data collection tool in the classifier. In this exercise, we will use this tool to collect training data. Even if you use a .csv or GEE table in the future, this is a helpful feature to collect additional training data points to help refine your model.

In this assignment, you will create training data points using high-resolution imagery, including Planet NICFI data. These will be used to train the classifier in a supervised classification using SEPAL’s random forests algorithm. The goal of training the classifier is to provide examples of the variety of spectral signatures associated with each class in the map.

+--------------------------------------+---------------------------------+
| Objectives                           | Prerequisites                   |
+======================================+=================================+
| Create training data for your        | SEPAL account                   |
| classes that can be used to train a  |                                 |
| machine learning algorithm.          |                                 |
+--------------------------------------+---------------------------------+
|                                      | Land cover categories defined   |
|                                      | in Exercise 2.1.                |
+--------------------------------------+---------------------------------+
|                                      | Mosaic created in Exercise 2.2. |
+--------------------------------------+---------------------------------+

|



Part 1. Set up your classification
-----------------------------------

1. In the **Process** menu, click the green plus symbol and select **Classification.**
2. Add the Amazon optical mosaic for classification:

  a. Click **+ Add** and choose either **Saved Sepal Recipe** or **Earth Engine Asset** (recommended).

    i. If you choose **Saved Sepal Recipe**, simply select your Module 2 Amazon recipe.
    ii. If you choose **Earth Engine Asset**, enter the Earth Engine Asset ID for the mosaic. The ID should look like “users/username/Module2_Amazon”.

        Remember that you can find the link to your Earth Engine Asset ID via Google Earth Engine’s Asset tab (see Exercise 2.2 Part 2).

  b. Select bands: Blue, Green, Red, NIR, SWIR1, & SWIR2. You can add other bands as well if you included them in your mosaic.
  c. You can also include **Derived bands** by clicking on the green button on the lower left.
  d. Click **Apply,** then click **Next.**

.. warning::
   Selecting **Saved Sepal Recipe** may cause an error stating "Google Earth Engine error: Failed to create preview" at the final stage of your classification. This occurs because GEE gets overloaded. If you encounter this error, please retrieve your classification as described in Exercise 2.2.

3. In the Legend menu, click **+ Add** This will add a place for you to write your first class label.

  a. You will need two legend entries.
  b. The first should have the number 1 and a Class label of Forest.
  c. The second should have the number 2 and a Class  label of Non-forest.
  d. Choose colors for each class as you see fit.
  e. Click **Close**.

.. image:: images/classification_legend.png
   :alt: Classification legend.
   :align: center

|

Part 2. Collect training data points
-------------------------------------

Now that you have created your classification, you are ready to begin collecting data points for each land cover class.

In most cases, it is ideal to collect a large amount of training data points for each class that capture the variability within each class and cover the different areas of the study area. However, for this exercise, you will only collect a small number of points: around 25 per class. When collecting data points, make sure that your plot contains only the land cover class of interest (no plots with a mixture of your land cover categories).

.. To help you understand why the random forest algorithm might get some categories you are trying to map confused with others, you will use spectral signatures charts in CEO-SEPAL to look at the NDVI signature of your different land cover classes. You should notice a few things when exploring the spectral signatures of your land cover classes. First, some classes are more spectrally distinct than others. For example, water is consistently dark in the NIR and MIR wavelengths, and much darker than the other classes. This means that it shouldn’t be difficult to separate water from the other land cover classes with high accuracy.

Not all pixels in the same classes have the exact same values—there is some natural variability! Capturing this variation will strongly influence the results of your classification.

1. First, let’s become familiar with the SEPAL Interface.
2. In the upper right corner of the map is a stack of three rectangles. If you mouse over this icon, it says "Select layers to view."

   Available base layers include SEPAL (Minimal dark Sepal default layer), Google Satellite, and Planet NICFI composites.

  a. We will use the Planet NICFI composites for this example. The composites are available in either RGB or false color infrared (CIR). Composites are available monthly after September 2020 and for every 6 months prior back till 2015.
  b. Select RGB, Jun 2019 (6 months).
  c. You can also select "Show labels" to enable labels that can help you orient yourself in the landscape.

.. image:: images/layer_view.png
   :alt: The layers available.
   :align: center

|

3. Now click on the point icon. When you mouse over this icon, it says "Enable reference data collection."
4. With reference data collection enabled, you can start adding points to your map.
5. Use the scroll wheel on your mouse to zoom in to the study area. You can click-hold and drag to pan around the map. Be careful though, as a single click will place a point on the map.

   If you accidentally add a point, you can delete it by clicking on the red **Remove** button.

6. Now we will start collecting forest training data.

  a. Zoom into an area that is clearly forested. When you find an area that is completely forested, click it once.
  b. You have just placed a training data point!
  c. Click the **Forest** button in the training data interface to classify the point.

     If you haven’t classified the point yet, then you can just click somewhere else on the map instead of deleting the record.

.. image:: images/collecting_forest_data.png
   :alt: Collecting forest data in the SEPAL interface.
   :align: center

|

.. note::
   Ideally you should switch back to the Landsat mosaic to make sure that this forested area is not covered with a cloud. If you mistakenly classify a cloudy pixel as Forest, then the results will be impacted negatively if your Landsat mosaic does have cloud-covered areas.

   However, this interface does not allow for switching between the Base Layer imagery and your exported mosaic. If you are using another training data collection method, keep this point in mind.

7. If you need to modify classification of any of your data points, you can click on the point to return to the classification (or delete) options.
8. Begin collecting the rest of the 25 **Forest** training data points throughout other parts of the study area.

  a. The study area contains an abundance of forested land, so it should be pretty easy to identify places that can be confidently classified as forest. If you’d like, use the charts function to ensure that there is a relatively high NDVI value for the point.
  b. Ensure you are placing data points within the extent of the mosaic (Rondonia).

9. Collect about 25 points for the **Forest** land cover class.

   When you are done, zoom out to the full extent of the area. Did you place data points somewhat equally across the full region? Are all points clustered in the same region? It’s best to make sure you have data points covering the full spatial extent of the study region, add more points in areas that are sparsely represented if needed.

10. After you collect your training data for **Forest**, you may see the classification preview appear.

  a. To disable the classification preview to continue to collect training data, return to the map layer selector.
  b. Uncheck the "Classification" Overlay.

.. image:: images/classification_overlay.png
   :alt: Disabling the classification overlay.
   :width: 450
   :align: center

11. Once you are satisfied with your forested training data points, move on to the **Non-Forest** training points.

  a. Since we are using a very basic set of land cover classes for this exercise, this should include agricultural areas, water, and buildings and roads. Therefore, it will be important that you focus on collecting a variety of points from different types of land cover throughout the study area.
  b. **Water** is one of the easiest classes to identify and the easiest to model, due to the distinct spectral signature of water.

    i. Look for water bodies within Rondonia.
    ii. Collect 10-15 data points for Water and be sure to spread them throughout Lake Mai Ndombe, the water sources feeding into it, and a couple of the water bodies/rivers to the eastern side of the mosaic. Be sure to put 2-3 points on rivers.
    v. Some wetland areas may have varying amounts of water throughout the year, so it is important to check both Planet NICFI maps for 2019. (Jun 2019 and Dec 2019).

.. image:: images/data_points_water.png
   :alt: Collecting data points in water.
   :align: center

|

12. Let’s now collect some building and road non-forest Training Data.

  a. There are not very many residential areas in the region. However, if you look you can find homes with dirt roads, and there are some airports as well.
  b. Place a point or points within these areas and classify them as Non-forest. Do your best to avoid placing the points over areas of the town with lots of trees.
  c. Find some roads, and place points and classify as Non-forest. These may look like areas of bare soil. Both bare soil and roads are classified as Non-forest, so place some points on both.

.. image:: images/data_points_residential.png
   :alt: Collecting residential and other human settlement area data points.
   :align: center

|

13. Next, place several points in grassland/pasture, shrub, and agricultural areas around the study area.

  a. Shrubs or small, non-forest vegetation can sometimes be hard to identify, even with high-resolution imagery. Do your best to find vegetation that is clearly not forest.
  b. The texture of the vegetation is one of the best ways to differentiate between trees and grasses/shrubs. Look at the below image and notice the clear contrast between the area where the points are placed and the other areas in the image that have rougher textures and that create shadows.

.. image:: images/data_points_low_vegetation.png
   :alt: Collecting low vegetation data
   :align: center

|

.. note::
   If you are using QGIS etc. to collect training data, you should also collect **cloud** training data in the **Non-forest** class, if your Landsat has any clouds. If there are some clouds that were not removed during the Landsat mosaic creation process you will need to create training data for the clouds that remain so that the classifier knows what those pixels represent. Sometimes clouds were detected during the mosaic process and were mostly removed. However, you can see some of the edges of those clouds remain.

   Note that you may not have any clouds in your Landsat imagery.

14. Continue collecting Non-forest points. Again, be sure to spread the points out across the study area.
15. Once again when you are done collecting data for these categories, zoom out to the full extent of the study region.

  a. Did you place data points somewhat equally across the full region?
  b. Are all points clustered in the same area?
  c. It’s best to make sure you have data points covering the full spatial extent of the study region, add more points in areas that are sparsely represented if needed.

**Congratulations! You have learned how to collect training data in SEPAL's classification interface.**

-----------------------------------------------------------------------------------------
Exercise 2.4. Classification using machine learning algorithms (Random Forests) in SEPAL
-----------------------------------------------------------------------------------------

|

.. image:: images/random_forest_model_outcome.png
   :alt: The outcome of a random forest model.
   :align: center

|

As mentioned in the Module introduction, the classification algorithm you will be using today is called random forest.  The random forest algorithm creates numerous decision trees for each pixel. Each of these decision trees votes on what the pixel should be classified as. The land cover class that receives the most votes is then assigned as the map class for that pixel. Random forests are efficient on large data and accurate when compared to other classification algorithms.

To complete the classification of our mosaicked image you are going to use a random forests classifier contained within the easy-to-use Classification tool in SEPAL. The image values used to train the model include the Landsat mosaic values and some derivatives, if selected (such as NDVI). There are likely additional data sets that can be used to help differentiate land cover classes, such as elevation data.

After we create the map, you might find that there are some areas that are not classifying well. The classification process is iterative, and there are ways you can modify the process to get better results. One way is to collect more or better reference data to train the model. You can test different classification algorithms, or explore object based approaches opposed to pixel based approaches. The possibilities are many and should relate back to the nature of the classes you hope to map. Last but certainly not least is to improve the quality of your training data. Be sure to log all of these decision points in order to recreate your analysis in the future.

+-----------------------------------------+------------------------------------+
| Objectives                              | Prerequisites                      |
+=========================================+====================================+
| Run SEPAL’s classification tool.        | SEPAL account                      |
+-----------------------------------------+------------------------------------+
|                                         | Land cover categories defined in   |
|                                         | Exercise 2.1.                      |
+-----------------------------------------+------------------------------------+
|                                         | Mosaic created in Exercise 2.2.    |
+-----------------------------------------+------------------------------------+
|                                         | Training data created in Exercise  |
|                                         | 2.3.                               |
+-----------------------------------------+------------------------------------+

Part 0. [Optional] Add training data collected outside of sepal
------------------------------------------------------------------

1. If you collected training data using QGIS, CEO, or another pathway, you will need to add the Training Data we collected in Exercise 2.3 in the **TRN tab.**

  a. Click on the green **Add** button.

    i You can upload a CSV file.
    ii. Or you can select Earth Engine Table and enter the path to your Earth Engine asset in the EE Table ID field.

  b. Click **Next**.
  c. For **Location Type**, select "X/Y" coordinate columns" or "GEOJSON Column" depending on your data source. GEE assets will need the GEOJSON column option.
  d. Click **Next**.
  e. Leave the **Row filter expression** blank. For **Class format**, select "Single Column" or "Column per class" as your data dictates.
  f. In the **Class Column** field select the column name that is associated with the class.
  g. Click **Next**.

2. Now you will be asked to confirm the link between the legend you input previously and your classification. You should see a screen as follows. If you need to change anything, click the green plus buttons. Otherwise, click **Done**, then click **Close**.

.. image:: images/link.png
   :alt: link between legend and classification
   :align: center

|

Part 1. Review additional classification options
-------------------------------------------------

1. Click on **AUX** to examine the auxiliary data sources available for the classification.

  a. Auxiliary inputs are optional layers which can be added to help aid the classification. There are three additional sources available: Latitude - Includes the latitude of each pixel; Terrain - Includes elevation of each pixel from SRTM data; Water - Includes information from the JRC Global Surface water Mapping layers.
  b. Click on **Water** and **Terrain**.
  c. Click **Apply.**

  10. Select **Terrain** and **Water.**

2. Click on **CLS** to examine the classifier being used.

  a. The default is a random forest with 25 trees.
  b. Other options include classification and regression trees (CART), Naive Bayes, support vector machine (SVM), minimum distance, and decision trees (requires a CSV).
  c. Additional parameters for each of these can be specified by clicking on the **More** button in the lower left.
  d. For this example, we will use the default random forest with 25 trees.

3. If you turned off your classification preview previously to collect training data, now is the time to turn it back on.

  a. Click on the "Select layers to show" icon.
  b. Select "Classification"
  c. Make sure Classification now has a check mark next to it, indicating that the layer is now turned on.

.. image:: images/classification_preview.png
   :alt: A preview of a classification.
   :align: center

4. Now we’ll save our classification output.

  a. First, rename your classification by typing a new name in the tab.
  b. Click **Retrieve classification** in the upper right hand corner (cloud icon).
  c. Choose 30 m resolution.
  d. Select the Class, Class probability, Forest % and Non-forest % bands.
  e. Retrieve to your **SEPAL Workspace.**

     You can also choose **Google Earth Engine Asset** if you would like to be able to share your results or perform additional analysis in GEE. However with this option, you will need to download your map from GEE using the Export function.

  f. Once the download begins, you will see the spinning wheel in the bottom left of the webpage in **Tasks.** Click the spinning wheel to observe the progress of your export.
  g. When complete, if you chose SEPAL workspace, the file will be in your SEPAL downloads folder. (Browse > downloads > classification name folder). If you chose GEE Asset the file will be in your GEE Assets.

.. image:: images/retrieval_interface.png
   :alt: The retrieval interface.
   :width: 450
   :align: center

|

Part 2. QA/QC considerations and methods
-----------------------------------------

Quality assurance and quality control, commonly referred to as QA/QC, is a critical part of any analysis. There are two approaches to QA/QC: formal and informal. Formal QA/QC, specifically sample-based estimates of error and area are described in Module 4. Informal QA/QC involves qualitative approaches to identifying problems with your analysis and classifications to iterate and create improved classifications. Here we’ll discuss one approach to informal QA/QC.

Following analysis you should spend some time looking at your change detection in order to understand if the results make sense. We’ll do this in the classification window. This allows us to visualize the data and collect additional training points if we find areas of poor classification. Other approaches not covered here include visualizing the data in Google Earth Engine or in another program, such as QGIS or ArcMAP.

With SEPAL you can examine your classification and collect additional training data to improve the classification.

.. image:: images/examine_classification_map.png
   :alt: Examining your change detection map
   :align: center

|

1. Turn on the imagery for your Classification and pan and zoom around the map.
2. Compare your Classification map to the 2015 and 2020 imagery. Where do you see areas that are correct? Where do you see areas that are incorrect?
3. If your results make sense, and you are happy with them, great! Go on to the formal QA/QC in Module 4.
4. However, if you are not satisfied, collect additional points of training data where you see inaccuracies. Then re-export the classification following the steps in Part 3.

**Congratulations! You now know how to produce map classifications in SEPAL.**
