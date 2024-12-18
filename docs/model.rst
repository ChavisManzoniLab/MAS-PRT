Models and How to change them
=======

.. Note::
   Changing the model requires basic knowledge in developpement and may be a leap in complexity

Summary
----------

MAS is using 2 differents inferences : 

MAS uses a `DeepLabCut <http://www.mackenziemathislab.org/deeplabcut>`_ detection of both the pup and the dam, and an automated detection of the nest using `Detectron2 <https://github.com/facebookresearch/detectron2?tab=readme-ov-file#learn-more-about-detectron2>`_

Change maDeepLabcut model
---------------------------

| First, take a look at how to train a multianimal Deeplabcut model : 
| https://deeplabcut.github.io/DeepLabCut/docs/maDLC_UserGuide.html

| It is highly recommended to follow the next step to not mess up the pipeline

| Install the DeepLabCut GUI and create a new maDeepLabCut project

.. note::
   Installing the DeepLabCut GUI in another environnement might be a good idea to avoid conflict

.. _code_directive:

.. image:: https://i.imgur.com/ZFAeJ70.jpeg

Open the config.yaml with any text editor. It should look like this

.. _code_directive:

.. image:: https://i.imgur.com/2hDlBf2.jpeg

| Now, delete everything below the red line.
| Copy and paste the layout.yaml located `here <https://github.com/ChavisManzoniLab/MAS/tree/main/MAS/DLC/Layout>`_ into your config.yaml
| **DO NOT** erase the part before the red line

| Now, you can extract some frames, and try to start label frame.

| If your manipulation was good, the keypoint selection in Napari (down right) should look like the picture  

.. _code_directive:

.. image:: https://i.imgur.com/YpshHaL.jpeg

| This is how frames were labeled
| Dam is the dam
| single is the pup
| The point names are self-explanatory, as shown in the image below

.. _code_directive:

.. image:: https://i.imgur.com/Gy43Vtb.png
   :width: 400

.. _code_directive:

.. image:: https://i.imgur.com/Ct0Gdy1.png
   :width: 600

.. _code_directive:

.. image:: https://i.imgur.com/IldAwqe.png
   :width: 400


.. Note::
   Don't be afraid if you have differents colors than on the pictures, it may vary

| Now, it's up to you! Happy training !
| See how to train a maDLC model : https://deeplabcut.github.io/DeepLabCut/docs/maDLC_UserGuide.html
| Once the model is satisfying, the new DLC model must be referenced in the code. 
| This can be done in the config.py
| You should change the pathway from DLCDETECTOR



Change Nest detection model
----------------------------

To train another Detectron2 model, I would strongly suggest to use the method offered by LabGym. 

https://github.com/umyelab/LabGym?tab=readme-ov-file#2-use-trained-detectors

| Extracting 2 frames per videos should be enough, depending on the quantity of videos you have
| Once your model is satisfying, you must modify the detectorPath accordingly with yours. 
| This can be done in the config.py
| You should change the pathway from NESTDETECTOR

| Now that you have LabGym on your computer, feel free to try it out ! 
| It's a formidable tool for quantifying behavior on videos :)

