Usage
++++++++++++++++++++

Accessing the Model
===================
The easiest way to access the model is to clone the latest version from the HF repository:

.. code-block:: bash

    git clone https://huggingface.co/patcdaniel/phytoClassUCSC


Running the Classifier
======================
.. note:: Test the model out in a `Colab Notebook <https://colab.research.google.com/drive/1hbwq8NfAhjax7K4YZcdZ3AKvMbyqg17c?usp=sharing>`_

The trained model (the model weights, architecture, training configuration, optimizerm, etc) is saved as a ``.h5`` file.

A mapping of class names to columns is saved in the ``class_list.json`` file.

The model can be loaded using easily:

.. code-block:: python

    from tensorflow import keras
    model = keras.models.load_model("phytoClassUCSC/phytoClassUCSC.h5")

The model expects an image as an array of the shape ``(299, 299, 3)`` (width, height, channels). Although images should be converted into greyscale, the model still expects three channels. 

Here is an example of image preprocessing:

.. code-block:: python

    import keras_preprocessing.image as keras_img

    def prep_image(fname):
    """ Load and prep images for model, reshape and normalize rgb to greyscale """

        target_size=(224,224)
        img = keras_img.img_to_array(
                keras_img.load_img(fname, target_size=target_size)
        )
        img /= 255
        img = img.reshape((1, img.shape[0], img.shape[1], img.shape[2]))

    return img

Classification is done using the ``model.predict`` method:

.. code-block:: python
    
    img = prep_image("test_image.jpg")
    pred = model.predict(img)

The output of ``model.predict`` is an array of probabilities for each class. The index of the highest probability is the predicted class.

.. note::  See :ref:`Caveats Section <caveats>` for why this may not be a good idea.


Making Sense of Results
=======================
The output of ``model.predict`` is an array of probabilities that the image belongs to each of the given classes. Across all of the classes, the probabilities sum to 1. If we assume that the index of the highest probability is the predicted class, then we can use the ``class_list.json`` file to map the index to the class name.

Example of how to find the highest probability index and the corresponding class name:

.. code-block:: python

    import json
    with open("phytoClassUCSC/class_list.json") as f:
        class_list = json.load(f)

    pred_class = class_list[str(pred.argmax())]

Caveats
=======
.. _caveats:

