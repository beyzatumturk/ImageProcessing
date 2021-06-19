# Assignment 6

A README file in the root submission folder (that contains src, test, and res). The README file should document which parts of the program are complete, and design changes and justifications.

# Overview

Our program is a simple image processing application. Using our program, a user can import photos, manipulate photos, and export photos.

# Features

All the features listed below are completed.

## Layering
The user can layer images and stack them on top of one another. Layers can be deleted, set to visible and invisible, copied, and exported as a collection of files. 

## Single Image Processing
The user can individually manipulate images in layers. To manipulate the image in a layer, the user can set a layer as the "current". When a layer is made current, the user can blur and sharpen the image, and apply a sepia and monochrome color transformation. The user also has the option to create an image into this current layer. Images that can be created include checkerboards and rainbows.

## Importing and Exporting
The user can load images into a layer from a file. Image file types that are currently supported include ppm, jpeg, and png. All other image types cannot be read by our program. The user also has the option to upload an entire layered image by passing in a txt file that contains the locations of all the layers. The user has the option to export a single image (the topmost visible layer of a layered image) or export the entire layered image (visible layers only) into a collection of files. The user can choose to export images into a ppm, jpeg, or png file.

## Scripting
To run our program, the user has the option to either upload a .txt file that contains the script, or interactively input instructions. After each instruction, the program will either return feedback of how the model has changed or if the user input was not valid.

# Design

We based our design on the MVC design pattern. As per the architecture, the model handles all image data, the controller handles user input and I/O, and the view displays feedback to the user. A brief overview of completion and design changes is included below. 

## Model
The model used by this program was the SimpleIPLayerModel. This model implemented the IPLayerModel, which extended the old IPModel. The IPLayerModel includes extra functionality that supports layering. The SimpleIPLayerModel also extends the SimpleIPModel, which only supported operations to modify one image. The functionality (and delegate) from SimpleIPModel is used to modify the "current layer". The SimpleIPLayerModel contains a List of IPManagers, which represent layers in an image. It also has a List of booleans that represent the layers' visibility. The pictureManager which was inherited from SimpleIPModel represents the "current layer". SimpleIPLayerModel contains a boolean flag that represents whether pictureManager is currently pointing to a layer, or if nothing is set to the "current layer". Finally, each SimpleIPLayerModel is initialized with a canvas width and canvas height which is used to ensure that all layers are the same size.

*Design change: We originally had our model handle IO (allowed for importing and exporting images), but this was taken out of IPModel after learning that model should not handle IO at all).*

### IPManager
*Design change: We originally had our IPManager handle IO (allowed for importing and exporting images), but this was taken out since the model would not be using IO. Instead, we made a FileManager that handles IO.*

### Image Representation
*Design change: Added cropping feature to the interface since we felt it would be a waste of memory to create an entirely new interface and new class just for this one method*

### Function Objects
*Design change: Moved the Filetype interface and function objects to the controller package since they handle IO.*

### Misc.
*Design change: Throughout our program, we initialized ArrayLists as ArrayList<>. We went back into our program and changed them all to List<>.*

## Controller
The controller used by this program is the SimpleIPLayerController. This controller uses a command design pattern to read a script. The script may either be put in interactively or read from a file. Depending on the input, the controller will delegate to a function object that represents a command. This class extends the AbstractIPController, which was included to support a program that may not support layering. The commands included in AbstractIPController are exclusive to the original IPModel.

### FileManager
*Design change: Following the feedback that we should not include I/O in the model, we created a FileManager that supports operations for file importing and exporting.* The commands that require importing and exporting files will contain a FileManager. This FileManager will determine filetypes from user input and accordingly import and export files of this type.

### FileCreator
The FileCreator is a class that creates File objects and FileOutputStreams since our export only takes in an OutputStream. This class was created to simplify exporting and handle exceptions related to creating a file.

## View
The view is the only aspect of our program that is partially completed. The view used by our program is the SimpleIPTextView, which implements the IPView. The IPView contains two methods, updateMessage and updateModel. At present, the SimpleIPTextView only uses updateMessage, as we did not change anything in the view when the model changed. However, to accommodate for future views that require notification of when the model changes, we included the updateModel.

# Assumptions
We assumed that the user will only want to use the SimpleIPLayerModel, as opposed to the SimpleIPLayer model. Since the assignment specified that the script should contain all the working commands so far, we used the most advanced model. We also assumed that once a model is made in the program, the user cannot override this model to create a new one. In other words, one model per program.
