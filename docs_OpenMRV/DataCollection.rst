---
title: Data collection with data quality management approaches
summary: This tutorial will guide you through collecting reference data by visually interpreting land cover at sample locations. You will also learn how to create a data quality assurance plan that meets the needs and budgets of your specific mapping projects.
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
- High Resolution
- Sampling design
- Sample design
- Sample selection
- Sample
- Sampling frame
- Stratified
- Response design
- Survey
- Survey design
- Reference data
- Reference classification
- Reference observations

group:
- category: Collect Earth Online
  stage: Reference data collection
---

--------------------------------------------------------
Data collection with data quality management approaches
--------------------------------------------------------

1. Background
--------------

This tutorial will guide you through collecting reference data by visually interpreting land cover at sample locations using SEPAL.

However, to ensure accurate human interpretation of land cover, you will need to adopt data quality management approaches. Adopting data quality management approaches is important for ensuring that each sample location is assigned an accurate label. Examples include: three interpreters examine each sample location independently, or a subsample of the data points are cross checked by another interpreter.

2. Learning objectives
-----------------------

* Collect reference data by visually interpreting land cover.
* Create a data quality assurance plan that meets the needs and budgets of your specific mapping projects and management needs.

Much of this information is based on Standard Operating Procedures developed by Till Neeff at FAO for global application. Using this tutorial will help you abide by these guidelines and meet these standards of quality for the data collected.

2.1 Pre-requisites

* A SEPAL account. Please see the tutorial here on OpenMRV under tool "SEPAL" for an introduction to SEPAL.
* A previously generated map. Please see the tutorials here on OpenMRV under process "Classification" and tools "SEPAL" and "GEE".
* A classification scheme. Please see the tutorial here on OpenMRV under process "Training data collection" and tool "SEPAL".
* A sampling design and corresponding Collect Earth Online (CEO) project. Please see the tutorial here on OpenMRV under process "Sampling design" and tool "SEPAL". You can find more information about CEO, sampling design, sample selection and other tools under processes "Sampling design" and "Sample data collection" and tools "SEPAL", "QGIS", "AREA2", "GEE", "CEO", and "CE".


3. Tutorial: Data collection with data quality management approaches
---------------------------------------------------------------------

3.1 Review your classification scheme
======================================

“Classification scheme” is the name used to describe the land cover / land use classes adopted. It should cover all the possible classes that occur in interest. You will need to have a response design with consistent labelling protocols when collecting data for your area and error estimates.

Your classification scheme should be consistent between your stratification of a map and your data collection.

If you have not already done so, please create a response design using the tutorial here on OpenMRV under process "Training data collection" and tool "SEPAL" (we will use the classification scheme from this tutorial). If your classification was trained using training points that differ substantially from your classification scheme, you may need to collect new training data and re-run your classification (see process "Classification" here on OpenMRV). Alternatively, you can find more information about response design here on OpenMRV under process "Sample data collection" and tools "GEE", "AREA2", "CEO", and "CE".

We will use the classification scheme below, used to classify a Forest/Non-forest land cover map:

.. figure:: images/classification_scheme.png
   :alt: The classification tree.
   :width: 450
   :align: center



We defined Forest as an area with over 70% tree cover. We defined Non-forest as areas with less than 70% tree cover. This captured land covers including urban areas, water, and agricultural fields.

3.2 Planning data collection
=============================

Data collection efforts require planning, particularly for large efforts with many interpreters involved. We will discuss these planning aspects here.

In this part, you will assume the role of a coordinator and an interpreter for a small team working to validate the land cover classification (see process "Classification" and tool "SEPAL" here on OpenMRV). A coordinator is responsible for organizing the team and tracking compliance information. An interpreter is responsible for collecting data.

**Identify the reference data sources.**

Ideally, you would have plots revisited in the field. However, this is rarely attainable given limited resources. An alternative is to collect reference observations through careful examination of the sample units using high resolution satellite data, or moderate resolution if high resolution is not available. The more data you have at your disposal the better.

If you have no additional data, you can use remote sensing data, such as Landsat data, for collecting reference observations, as long as the process to collect the reference data is more accurate than the process used to create the map being evaluated. Careful manual examination can be regarded as being a more accurate process than automated classification.

Consider what additional data you might be able to include in your verification. Do you have access to satellite data at a finer resolution than Landsat? Could you incorporate additional datasets such as stump data or on the ground verifications?

Compile a list of your data sources and review it with your interpreters. Recording this information is important for documentation.

.. figure:: images/data_source_recording.png
   :alt: A data source recording document.
   :align: center



**Determine level of effort.**

1. Estimate the necessary level of effort for the data collection using the following formula:

   Minutes to interpret 1 sample unit * number of sample units = required level of effort for data collection

2. If information is available from previous inventories, use that experience to set the value on the time required for assessing sample units from previous experience using the same response design. Otherwise, carry out a test.

**Identify data collection participants.**

1. As coordinator, you will identify the persons who may be involved in the data collection. You should set up minimum qualifications for participating in the data collection, such as familiarity with the landscape, previous experience, etc.

  a. What qualifications do you think are important?
  b. What qualifications are essential, and which would be nice to have?
  c. How can you build capacity within your organization for data collection?

2. As coordinator, you will record names and contact information of all the participants in the data collection and training.

  a. Here’s a template:

+------+-----------------------------------+------------------+--------------------------+
| Name | Contact                           | Institution      | Role for data collection |
+======+===================================+==================+==========================+
| Name | Email address and/or phone number | Institution name | Coordinator              |
+------+-----------------------------------+------------------+--------------------------+
| Name | Email address and/or phone number | Institution name | Trainer                  |
+------+-----------------------------------+------------------+--------------------------+
| Name | Email address and/or phone number | Institution name | Sample interpretation    |
+------+-----------------------------------+------------------+--------------------------+
| Name | Email address and/or phone number | Institution name | Sample interpretation    |
+------+-----------------------------------+------------------+--------------------------+
| Name | Email address and/or phone number | Institution name | etc.                     |
+------+-----------------------------------+------------------+--------------------------+

  b. And a worked example:

+--------------+---------------------+---------------------------------+--------------------------+
| Name         | Contact             | Institution                     | Role for data collection |
+==============+=====================+=================================+==========================+
| Phạm Tuân    | example@example.org | Institute for Collecting Data   | Coordinator              |
+--------------+---------------------+---------------------------------+--------------------------+
| Sally Ride   | example@example.org | Training Specialists Institution| Trainer                  |
+--------------+---------------------+---------------------------------+--------------------------+
| Rodolfo Vela | example@example.org | Institute for Collecting Data   | Sample interpretation    |
+--------------+---------------------+---------------------------------+--------------------------+
| Yuri Gagarin | example@example.org | Institute for Collecting Data   | Sample interpretation    |
+--------------+---------------------+---------------------------------+--------------------------+

|

3. Based on this information, you will decide on the format and modality for the data collection and on a timeline.

  a. For example, the format of the data collection can be a mapathon set-up where a large group collects the data over a short amount of time or a smaller team that collects the data over long periods. The modality for the data collection concerns where the team collects the data, either in the same location or disparate locations eg. in a mapathon, the interpreters could be in the same room interpreting the data.
  b. If the data collection is set up in different locations, modes of communication should be specified to help improve the consistency in the data interpretation.
  c. Multiple re-measurements for all samples is another option.

4. The logistics manager (if different from the coordinator) will arrange logistics, including space for data collection, sufficient time for data collection, and salary arrangements.
5. With your fictional team (above) and your timeline laid out in the scenario, decide on the format and modality for the data collection and on a timeline.

  a. What other modalities of data collection can you think of?
  b. What are the pros and cons of these modalities?

**Organize training and calibration sessions.**

1. As a first step in the data collection, the coordinator and the trainer organize and prepare a training event for the interpreters who have confirmed their participation. The training should cover the following topics as a minimum:

  a. The response design and the interpretation key (detailing location specific examples from all the classes in the classification system with visualization from multiple data sources available),
  b. The software used for the data collection and how to ensure the data management and storage,
  c. The data sources available, and
  d. Quality management practices.

2. Knowing what you do now, consider a-d above and briefly fill in details for each topic in another document. Write this as if you were planning a training event before collecting verification data for your forest/non-forest classification. What other topics do you think should be in the training?

The trainer should then implement the training event following these basic principles:

1. Create an environment for active participation, where participants can share questions and opinions
2. Encourage communication between the interpreters
3. Record attendance of the interpreters, and
4. Assess the capacity of the interpreters at the end of the training and record the results.
5. Thinking about the basic principles for a training (a-d above) briefly write out how you might achieve these goals.

   Following the training, the coordinator and the trainer should prepare a report summarizing:

  a. The training actions taken,
  b. The attendance (example below), and
  c. The results of the assessment of capacity.

This information should be documented as part of the decision making process for the verification.

+---------------+---------+---------+
| Name          | Day 1   | Day N   |
+===============+=========+=========+
| Interpreter 1 | present | present |
+---------------+---------+---------+
| Interpreter X | present | present |
+---------------+---------+---------+

**Distribute and assign sample units to interpreters.**

1. As coordinator, you will decide on a fraction of sample units to be assessed multiple times by all interpreters for cross-checking. Using approximately 2.5% of plots for cross checks is a good starting point. The samples that are duplicated should have a unique identification, and/or be recorded in some way.

2. The coordinator should then allocate sample units to interpreters based on some system.

  a. Allocation modalities are the modalities by which sample units are allocated to each interpreter e.g. randomly, following experience in a specific area.
  b. What method might you prefer be used to allocate samples? Why?

3. The coordinator should use a standardized naming structure to distribute the samples to the interpreters.

  a. The coordinator should record the number of sample units, the interpreter assigned to assess those samples and the file location in a table like the one below.
  b. The naming structure can include metadata such as the date the samples are distributed, the name of the interpreter and the purpose of the data collection.
  c. Try preparing a document to distribute the sample units among interpreters like the table below:

+------------------------+------------------+--------------------------------------------+-----------------------------+
| Number of sample units | Interpreter name | File name                                  | File archive location       |
+========================+==================+============================================+=============================+
| X sample units         | Interpreter 1    | e.g. collection_data_date                  | Link to cloud storage or    |
|                        |                  | [year/month/day]                           | folder path to repository   |
|                        |                  | _versionnumber.csv                         |                             |
+------------------------+------------------+--------------------------------------------+-----------------------------+

|

3.3 Collecting data
====================

After training and sample allocation, it is time to collect data. Here, we will demonstrate collecting data in CEO to ensure compliance with SOP and oversight requiring interpreter names be collected for the points they collect. Please see the tutorial here on OpenMRV under process "Sampling design" and tool "SEPAL" (we will use the Collect Earth Online project created in this tutorial). More information about sampling design and sample data collection can be found here on OpenMRV under processes "Sampling design" and "Sample data collection", and tools "QGIS", "GEE", "AREA2", "CEO", and "CE".

**Data collection by interpreters.**

In general, data collection should include the following steps:

1. When interpreting the samples, use an interpretation key as a guide for assessing different land use classes and transitions. When possible, consult other interpreters and the coordinator if there are any doubts about the image interpretation.
2. The coordinator collects the data from all interpreters at defined intervals (intervals can be defined by number of samples or by time intervals) to perform quality assurance procedures, including auxiliary data checks, cold checks and hot checks, as defined in the quality assurance section.
3. During the data collection, the coordinator organizes regular discussions and group assessment of samples with all the interpreters to ensure a mutual understanding of the interpretation techniques.
4. Take notes of challenges and limitations during the data collection as well as potential sources of bias during the data collection. If working as part of a team of collectors pass this information along to the coordinator.

**Data collection in CEO**

1. To collect data in CEO, navigate to the project you created in the tutorial here on OpenMRV under process "Sampling design" and tool "SEPAL". Your screen should look like this:

.. figure:: images/data_collection_CEO.png
   :alt: The data collection interface in CEO
   :align: center

2. Click **Go to first plot.** This will take you to your first plot.
3. Answer all of the questions for your first plot by clicking on the appropriate answers.

  a. If you created multiple questions, you can navigate between questions using the numbers above your question text.
  b. Scroll in and out with your mouse wheel (or press the +/- buttons) to view the landscape context and see your plots properly.
  c. Click on **Save** to save your answers and move on to the next plot.

.. figure:: images/data_collection_process.png
   :alt: The data collection process in CEO
   :align: center

4. Continue answering questions until you reach the last plot.
5. When you have finished answering all of the questions, navigate to your Institution’s page.
6. Your project name should now be green, indicating that all plots have been completed. If it is yellow, click on the project name and answer the remaining questions.

.. figure:: images/ceo_sepal_manual.png
   :alt: A partly completed project.
   :align: center



7. Click on the S next to the project.
8. This will download your project’s sample data. Save it to your hard drive and note the location.

You can view a demonstration of collecting data on CEO on `YouTube <https://www.youtube.com/watch?v=gMJP17Ue6lQ>`_.


**Data assembly**

Data assembly is required ONLY when you have multiple data interpreters, each working on their own project. If you have used the CEO pathway described just above with multiple interpreters contributing to the same project, this step is not needed.

1. If you have multiple interpreters, after the data collection is completed the coordinator should create a consolidated database with all the collected sample data.

  a. The coordinator should check that all necessary metadata and sample information is archived and included in the final database.
  b. A description of the column names from the database should be archived with the database. A standardized naming structure is used for the compiled database and includes metadata in the folder and file name.

2. Each sample in the consolidated database notes the round of data collection. The database can be amended to include additional rounds of data collection. Multiple versions are recorded and explanations between versions are included in the documentation template.
3. In CEO, this is handled through the Institution’s Project interface.

3.4 Quality management and archiving - Quality Assurance
=========================================================

Quality assurance and control are fundamental in ensuring that your validation and resulting area estimates are as accurate as can be and are unbiased. This part will cover the steps of how to perform quality assurance.

For change detection maps, you will want to check for and exclude impossible transitions through logical checks. Make sure that the changes make sense. For example, having a transition from Water <= 20% to Aquaculture may make sense, but a transition from Water <= 20% to Developed High Intensity would not.

Also be sure to document all impossible transitions. These should be included in your response design tree as well.

Conduct ongoing hot, cold and auxiliary data checks during data collection and conduct regular review meetings among all interpreters. We’ll go through each of these now.

* Auxiliary data checks: use an external data source, such as externally created maps, to compare to the sample unit classification. Discrepancies between the two datasets can be flagged for rechecking. Confirmed differences between the two datasets can be documented to showcase why sample-based area estimation may give different results than other data sources.

  * Ask questions when comparing your map and auxiliary maps:

    * Where do you notice agreement between the two maps?
    * Where do you notice disagreement between the two maps?
    * What are some reasons you could attribute to the discrepancies between them?

* Cold checks: sample units that are randomly selected from the data produced by interpreters. The decisions made by the interpreters are reviewed by the coordinator or group of interpreters meeting together. If the error by the interpreter reflects a systematic error in their interpretation, it is discussed directly with the interpreter and the affected sample units are corrected.

  * Review the table below that was a result of a cold check you conducted on the plots analyzed by the interpreters.
  * Based on some of these answers, what can you conclude about the data?

    * What plots should likely be reviewed?
    * What other information could you gain from examining how the interpreters are performing?

* Cold checks can be created in CEO by creating multiple projects with the same sample plots. Multiple interpreters can each complete one of these projects, allowing for comparison.

+--------------+-----------------------+-----------------------+-----------------+
| Interpreter  | Plot 1 (Forest)       | Plot 2(Forest)        | Plot 3 (Water)  |
+==============+=======================+=======================+=================+
| Sally Ride   | Non Forest Vegetation | Non Forest Vegetation | Water           |
+--------------+-----------------------+-----------------------+-----------------+
| Rodolfo Vela | Forest                | Forest                | Built Up        |
+--------------+-----------------------+-----------------------+-----------------+
| Yuri Gagarin | Forest                | Forest                | Water           |
+--------------+-----------------------+-----------------------+-----------------+

* Hot checks: sample units that are flagged as low confidence. These marked sample units should be further reviewed by the coordinator or group of interpreters meeting together. Once reviewed, labels that are deemed to be incorrect on these sample units should be adjusted by the interpreter.

  * If you’re conducting this training with others, ask your colleagues about sample units that you’re unsure about.
  * Have your colleagues show you sample units that they are unsure about.
  * Discuss these sample units and make changes to the labels based on your discussion.


3.5 Quality management and archiving - Quality Control
=======================================================

Quality control refers to the quality of interpretation through cross-validation based on a set of samples that were assessed by two or more interpreters. See also the cold data check mentioned above. These checks can be conducted in CEO by creating multiple projects with the same sample plots. Multiple interpreters can each complete one of these projects, allowing for comparison.

1. Establish a reference interpretation for each of the cross-validation sample units.

  a. Choose a reference interpretation--this should be one of the interpreter’s class assignments.
  b. This reference interpretation will be the basis for establishing the performance of individual interpreters.

2. Calculate agreement for each interpreter based on the reference interpretation. For each pair of interpreters, create a confusion matrix and include it in your project documentation.

+------------------------+-------------------------+------------------------+------------------------+
|                        | Class 1 (reference)     | Class 2 (reference)    | Class k (reference)    |
+========================+=========================+========================+========================+
| Class 1 (interpreter)  | Counts of sample points |Counts of sample points |Counts of sample points |
+------------------------+-------------------------+------------------------+------------------------+
| Class 2 (interpreter)  | Counts of sample points |Counts of sample points |Counts of sample points |
+------------------------+-------------------------+------------------------+------------------------+
| Class k (interpreter)  | Counts of sample points |Counts of sample points |Counts of sample points |
+------------------------+-------------------------+------------------------+------------------------+

3. To work an example, pretend that you and another interpreter have both collected data on a set of sample units on this Amazon land cover classification. Here are the results:

+--------------+------------------------------+------------+
| Point number | Interpreter 1 (Interpreter)  | Reference  |
+==============+==============================+============+
| 1            | Forest                       | Forest     |
+--------------+------------------------------+------------+
| 2            | Forest                       | Forest     |
+--------------+------------------------------+------------+
| 3            | Forest                       | Non-forest |
+--------------+------------------------------+------------+
| 4            | Non-forest                   | Non-forest |
+--------------+------------------------------+------------+
| 5            | Non-forest                   | Forest     |
+--------------+------------------------------+------------+
| 6            | Forest                       | Forest     |
+--------------+------------------------------+------------+
| 7            | Non-forest                   | Non-forest |
+--------------+------------------------------+------------+
| 8            | Non-forest                   | Non-forest |
+--------------+------------------------------+------------+
| 9            | Non-forest                   | Forest     |
+--------------+------------------------------+------------+
| 10           | Forest                       | Forest     |
+--------------+------------------------------+------------+

4. Calculate the confusion matrix below:

+--------------------------+-------------------+------------------------+
|                          |Forest (reference) | Non-forest (reference) |
+==========================+===================+========================+
| Forest (interpreter)     |                   |                        |
+--------------------------+-------------------+------------------------+
| Non-forest (interpreter) |                   |                        |
+--------------------------+-------------------+------------------------+

5. Based on the confusion matrices, for each interpreter, overall agreement with the reference is to be calculated as follows:

   Agreement between interpreter and the majority = Sum of counts in all the diagonal cells / Sum of all counts

6. The overall agreement per interpreter can be reported as below:

+---------------+----------------------------------------------------------------+
| Interpreter   | Overall agreement                                              |
+===============+================================================================+
| Interpreter 1 | Sum of counts in all of the diagonal cells/ Sum of all counts  |
+---------------+----------------------------------------------------------------+
| Interpreter 2 | Sum of counts in all of the diagonal cells/ Sum of all counts  |
+---------------+----------------------------------------------------------------+
| Interpreter n | Sum of counts in all of the diagonal cells/ Sum of all counts  |
+---------------+----------------------------------------------------------------+


7. Using the table below, calculate the agreement between interpreters:

+------------------------+---------------------+---------------------+---------------------+
|                        | Class 1 (majority)  | Class 2 (majority)  | Class 3 (majority)  |
+========================+=====================+=====================+=====================+
| Class 1 (Sally Ride)   | 90                  | 8                   | 2                   |
+------------------------+---------------------+---------------------+---------------------+
| Class 2 (Sally Ride)   | 6                   | 84                  | 10                  |
+------------------------+---------------------+---------------------+---------------------+
| Class 3 (Sally Ride)   | 2                   | 6                   | 92                  |
+------------------------+---------------------+---------------------+---------------------+
| Class 1 (Rodolfo Vela) | 89                  | 9                   | 2                   |
+------------------------+---------------------+---------------------+---------------------+
| Class 2 (Rodolfo Vela) | 12                  | 88                  | 0                   |
+------------------------+---------------------+---------------------+---------------------+
| Class 3 (Rodolfo Vela) | 3                   | 0                   | 97                  |
+------------------------+---------------------+---------------------+---------------------+
| Class 1 (Yuri Gagarin) | 94                  | 6                   | 0                   |
+------------------------+---------------------+---------------------+---------------------+
| Class 2 (Yuri Gagarin) | 7                   | 86                  | 7                   |
+------------------------+---------------------+---------------------+---------------------+
| Class 3 (Yuri Gagarin) | 1                   | 4                   | 95                  |
+------------------------+---------------------+---------------------+---------------------+

+---------------+---------------------------------------------------------------+
| Interpreter   |  Overall agreement                                            |
+===============+===============================================================+
| Sally Ride    | Sum of counts in all of the diagonal cells/ Sum of all counts |
+---------------+---------------------------------------------------------------+
| Rodolfo Vela  | Sum of counts in all of the diagonal cells/ Sum of all counts |
+---------------+---------------------------------------------------------------+
| Yuri Gagarin  | Sum of counts in all of the diagonal cells/ Sum of all counts |
+---------------+---------------------------------------------------------------+

8. Per-class agreement amongst interpreters should be analyzed and reported as follows:

+---------------------+---------------------------+-----------------------------+------------------------------+---------+
|                     | All interpreters agreeing | One interpreter disagreeing | Two interpreters disagreeing | etc.    |
+=====================+===========================+=============================+==============================+=========+
| Class 1 (reference) | Percent                   | Percent                     | Percent                      | Percent |
+---------------------+---------------------------+-----------------------------+------------------------------+---------+
| Class 2 (reference) | Percent                   | Percent                     | Percent                      | Percent |
+---------------------+---------------------------+-----------------------------+------------------------------+---------+
| Class 3 (reference) | Percent                   | Percent                     | Percent                      | Percent |
+---------------------+---------------------------+-----------------------------+------------------------------+---------+
| Total               | Percent                   | Percent                     | Percent                      | Percent |
+---------------------+---------------------------+-----------------------------+------------------------------+---------+

For this example, consider the following case:

+--------------+---------------+---------------+---------------+------------+
| Point number | Interpreter 1 | Interpreter 2 | Interpreter 3 | Reference  |
+==============+===============+===============+===============+============+
| 1            | Forest        | Forest        | Forest        | Forest     |
+--------------+---------------+---------------+---------------+------------+
| 2            | Forest        | Forest        | Non-forest    | Forest     |
+--------------+---------------+---------------+---------------+------------+
| 3            | Forest        | Non-forest    | Non-forest    | Non-forest |
+--------------+---------------+---------------+---------------+------------+
| 4            | Non-forest    | Non-forest    | Non-forest    | Non-forest |
+--------------+---------------+---------------+---------------+------------+
| 5            | Non-forest    | Forest        | Forest        | Forest     |
+--------------+---------------+---------------+---------------+------------+
| 6            | Forest        | Forest        | Non-forest    | Forest     |
+--------------+---------------+---------------+---------------+------------+
| 7            | Non-forest    | Non-forest    | Non-forest    | Non-forest |
+--------------+---------------+---------------+---------------+------------+
| 8            | Non-forest    | Non-forest    | Non-forest    | Non-forest |
+--------------+---------------+---------------+---------------+------------+
| 9            | Non-forest    | Forest        | Non-forest    | Forest     |
+--------------+---------------+---------------+---------------+------------+
| 10           | Forest        | Forest        | Forest        | Forest     |
+--------------+---------------+---------------+---------------+------------+

Now calculate the per-class agreement. Note that percent should be calculated by #/10 points for this example.

+------------------------+------------------+-----------------+------------------+---------------------+
|                        | All interpreters | One interpreter | Two interpreters | Three interpreters  |
|                        | agreeing         | disagreeing     | disagreeing      | disagreeing         |
+========================+==================+=================+==================+=====================+
| Forest (reference)     | Percent          | Percent         | Percent          | Percent             |
+------------------------+------------------+-----------------+------------------+---------------------+
| Non-forest (reference) | Percent          | Percent         | Percent          | Percent             |
+------------------------+------------------+-----------------+------------------+---------------------+
| Total                  | Percent          | Percent         | Percent          | Percent             |
+------------------------+------------------+-----------------+------------------+---------------------+



4. Frequently Asked Questions (FAQs)
-------------------------------------

**How do I make a CEO account?**

In your browser window, navigate to https://collect.earth/. CEO supports Google Chrome, Mozilla Firefox, and Microsoft Edge. Click **Login/Register** on the upper right. To set up a new account, click on **Register a new account** and follow the instructions. Please also see the tutorial called "An introduction to SEPAL" under the SEPAL tool.

**What happens if I lose my CEO password?**

You can resent your password by navigating to https://collect.earth/ and clicking on **Forgot your password?**, and then following the instructions.

5. References
-------------

Much of this information is based on Standard Operating Procedures for sample-based area estimation which can be found here on OpenMRV.


======================================

.. figure:: images/cc.png

This work is licensed under a `Creative Commons Attribution 3.0 IGO <https://creativecommons.org/licenses/by/3.0/igo/>`_

Copyright 2021, World Bank

This work was developed by Karen Dyson under World Bank contract with Spatial Informatics Group, LLC for the development of new Measurement, Reporting, and Verification related resources to support countries’ MRV implementation.

| Attribution
Dyson, K. 2021. Data collection with data quality management approaches. © World Bank. License: `Creative Commons Attribution license (CC BY 3.0 IGO) <https://creativecommons.org/licenses/by/3.0/igo/>`_

.. figure:: images/wb_fcpf_gfoi.png
