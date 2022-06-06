# Spatial_final_assignment
Repository for the spatial assignment - Sea voyages in the 18th and 19th century. 

## ------ SCRIPT DESCRIPTION ------
This repository contains a R-markdown script that takes data from CLIWOC and Globcurrents to asses sea routes and how effeciency they are in choosing routes that sail with the surface currents of the ocean.

## ------ METHODS ------


## ------ DATA ------
This script mainly utilises two datasets.

**Cli**matological Database for the **W**orld's **Oc**eans**, or **CLIWOC** for short, contains ca. 287.000 different logbook entries across 8 nations from 1662-1855. However, that vast majority of these are from british, dutch, french and spanish ships from 1750-1850, and the script will filter out all other nations. The original EU-funded project was created in the early 2000's as a cooperation across a range of different unversities. Although it was intended to be used to, as the name might suggest, map and research climatological behavior and changes, it has since been used for a wide range of different purposes. A might have been expect from a project created in the early 2000's, it is however not very accesiable as it requires the use of programs such as MS ACCESS. Thankfully the database has been updated by others and can now in more modern formats. The table explaining each variable found onn the original website, is however still of immense value.
- Link to original database: https://webs.ucm.es/info/cliwoc/
- Link to updated database: https://www.historicalclimatology.com/cliwoc.html

**GlobCurrent** provided that files needed to create the currents raster. While the original files also had the direction of ocean currents, that information was lost when converted to a raster file. As the north-south current raster was deemed unusable, the __route effiecieny is based exclusivly on east-west currents__

## ------ REPO STRUCTURE ------
"src" FOLDER:
- This folder contains the .py scripts to create the image classification model and to predict images.
- The precreated / pretrained model created from the model creation script

"in" FOLDER:
- This is where the data used in the scripts should be placed. In other words this is where the movie posters train and test data should be placed.
- Any posters that you wish to predict using the poster_prediction.py script should be placed in the "Prediction_images" folder.

"out" FOLDER:
- This is where the model, history plot and classification report will be saved

"utils" FOLDER:
- This folder should include all utility scripts used by the main script.

## ------ SCRIPT USAGE ------
- The model_creation.py script requires you to give the arguments "-e" / "--epoch" (how many epochs you want it to train) and "-b" / "--batch" (for batchsize). The pretrained model was created with 10 epochs and batchsize 128

- The poster_prediction.py script requires you to give the argument "-i" / "--image" (the name of the image you want to predict)

## ------ RESULTS ------
Even with the different optimisations of the model, it did not become good at predicting whether or not a movie is good or bad based on its poster. There is almost as if there is a 50 / 50 chance of it guessing correctly or wrong. Notable critically appraised movies such as Batman (2022) or Dune were categorized as bad.

Another issue with the model is that it suffers from an apperant overfitting, as the val_accuracy of the model is stable, the val_loss is rising while train_accuracy is rising and train_loss is falling.

In short: a model can't predict what this model is trying to predict. This follows in line with other models that have tried to do the same thing (such as https://www.kaggle.com/code/phiitm/can-we-judge-a-movie-by-it-s-poster).
