.. UCSC IFCB Classifier documentation master file, created by
   sphinx-quickstart on Wed Jul 26 09:10:53 2023.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to UCSC IFCB Classifier's Documentation!
================================================

.. note::
   .. image:: /images/model_schema.png
      :width: 650
      :align: center
      :alt: IFCB classification diagram
   
   This diagram shows how IFCB model data is pre-processed for classification and how classification results are interpreted.

The UCSC IFCB Classifier is a trained classification model used for classifying images collected by an Imaging FlowCytobot (IFCB). The model is trained on images collected from IFCBs deployed at the Santa Cruz Wharf (SCW) and the Power Buoy (PB) in Monterey Bay.

The model is a depthwise Convolutional Neural Network (CNN) based on the Xception architecture [`Chollet, F., 2017 <https://arxiv.org/abs/1610.02357>`_] with 134 layers using weights pretrained on ImageNet. 

**Version 1.0** - 51 distinct taxanomic classes are defined by the model. A description of the classes can be found in the :ref:`classes section <classes>`.

.. caution::
   This classifier is still under development and should be applied with a healthy dose of sketpicism. There may be regional and deployment specific biases that are not well described when applying the model to new data.


.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Performance/validation
   Classes/classes
   Usage/usage


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
