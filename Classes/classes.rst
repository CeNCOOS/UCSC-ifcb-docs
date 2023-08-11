Model Classes
+++++++++++++++
.. _classes:

Class Description
=================
.. csv-table:: UCSC IFCB Classifier Classes
   :file: /_files/UCSC_IFCB_Classifier_v1.csv
   :header-rows: 1



Class-Specific Thresholds
=========================
.. _thresholds:

Class-specific thresholds are an important processing step for accounting for bias in the training dataset. Nonuniformity in the training data reflect both practical desicions made by the creators of the data set and the natural distribution of observered phytoplankton classes. In plain terms, the result is that the model is more likely to guess that something belongs to the more commonly observed classes. In that case, we require a high threshold in that predication in order to assign confidence. Conversely when a less common class is observed, it makes sense to have a lower threshold to assign confidence.

Thresholds can be generated for each class by incrementally increasing a threshold from 0 to 1 and calculating the resulting metrics. In this case, the F-score was used to balance recall and percision. The threshold values where F-score begins to decrease (diff > 0.005) are the class-specific thresholds. Thresolds are calculated for each class and are shown in the table below.

.. note::
    .. image:: /images/threshold_sensitivity_byclass.png
        :width: 70%
        :align: center
        :alt: Thresholds

    REPLACE WITH UP-TO-DATE
    Each curve shows the accuracy as the threshold is increased (up to .99). The point where the curve begins to decrease is the threshold value for that class. 

.. csv-table:: Class-specific thresholds
    :file: /_files/class_threshold_v1.0.csv
    :header-rows: 1