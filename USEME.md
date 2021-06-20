# Assignment 6
This USEME includes information on how to run the JAR file, a complete list of functions supported by our program, and example runs.

## How to Use the Program
The programs requires commands either in form of a file input or a script. There are currently 17 commands that the programs supports. If a user chooses to read the inputs from a file, after the file is read the program will quit. If the users provides the commands via the terminal, they will need to press "q" in order to quit the program. The currently supported commands inlcude blur, sharpen, monochrome, sepia, create, add, copy, current, delete, save first, save all, import (single image), upload (multiple images), invisible, make, rename, and visible. The user an use the program by typing the commands and the needed inputs for the commands. A model is not created by default users must use the "make" command to create a model.  If a command is given but can't be applied, controller retuns an informational message.

## How to run the jar file
To run the jar file, the user should open up the terminal and open the jar file using java -jar NameOfJARFile.jar. The files included in /res are necessary to run the scripts for this jar. To run the jar interactively, the user should begin by typing "make" followed by two integers that represent the canvas of the layered image. If the uder decides to do this command, they will be unable to upload a script. If the user want to upload a script and have commands read from this script, they should type "read" followed by the file name. The two example script files are named script1.txt and script2.txt. To run the jar, these scripts and their supplementary material (one.jpeg, three.png, Sunset.ppm, shirt.ppm) must exist in the same folder.

### Initial Commands (must be used in order to start the program)
The program doesn't create a model for the user, the user must use "make" command with two integers represnting canvas width and height. Alternatively, a user can also upload a file with the "make" command. If any of the other commands are given without providing a model, the controller will inform the user that a model is needed. Make commands can only be called once. If a user wants to change the size of the canvas tehy must quit and restart the program.

### Layering Commands
To add a new layer to the model, the user must use the "add" command. This command only requires the model to be not null. When a new layer created it gives a confirmation message and informs the current number of layers.<br/>
Example run: <br/>
make 20 20: creates a 20x20 canvas <br/>
add: adds a blank layer <br/>

To delete a layer, the user must use the "delete" command and give the layer index. Delete must requires the model to be not null and it requires the given layer index to exist in the model. <br/>
Example run: <br/>
make 20 20: creates a 20x20 canvas <br/>
add: adds a blank layer <br/>
delete 0: deletes the empty layer just created.  <br/>

To copy a layer, the model must not be null, an existing layer index must be specified and the layer with specified index must have an image. Copying a layer requires a layer index. <br/>
Example run: <br/>
make 20 20: creates a 20x20 canvas <br/>
add: adds a blank layer <br/>
create chechkerboard 5 4: create a 5x5 checkerboard image with each square being 4x4 pixel <br/>
copy 0: copies the top most layer. Creates a new layer with the same image  <br/>

To make a layer visible/invisible, the model must not be null, an existing layer index must be specified and the layer with specified index must have an image. 
These commands require a layer index to be given. <br/>
Example run: <br/> 
make 20 20: creates a 20x20 canvas <br/>
add: adds a blank layer <br/>
create chechkerboard 5 4: create a 5x5 checkerboard image with each square being 4x4 pixel <br/>
Invisible 0: makes the checkboard image in layer 0 invisible <br/>
Visible 0: makes the checkboard image in layer 0 visible <br/>


To upload multiple images to the model, the model must not be null. Also the model must not have any layers present. Upload command requires a valid filePath of a text file that stores the filepaths of the imported images.  <br/>
Example run: <br/>
make 20 20: creates a 20x20 canvas <br/>
upload res/script2ImportAllLocations.txt : uploads all the images that has their filepath in the text file.

To export all the images, the users must provide the command "save all", a file type and a textfile filepath. The program will export all the images in the model with the given file type and extension. It store teh images' file paths in the given text file.<br/>
Example run:<br/>
make 7 7: creates a 7x7 canvas<br/>
add: adds a blank layer <br/>
add: adds a blank layer <br/>
current 0 : makes the current image, image 0<br/>
create rainbow 7 1: Attempts to create a rainbow with width of 7 pixels, and each color with the height of 1 pixel.<br/>
current 1 : makes the current image, image 0<br/>
create rainbow 7 1: Attempts to create a rainbow with width of 7 pixels, and each color with the height of 1 pixel.<br/>
current 2 : makes the current image, image 0<br/>
create rainbow 7 1: Attempts to create a rainbow with width of 7 pixels, and each color with the height of 1 pixel.<br/>
save first rainbow.png: exports the rainbow to a file named rainbow.png as a png file.<br/>
save all ppm locationsHere.txt : saves all the images in the model as a ppm file. Stores all the images' filepaths in the locationsHere.txt file.



### Individual Image Commands

To blur and sharpen an image and to apply monochrome and sepia filter, the model must not be null, there must be a selected current layer, and the layer must have an image. This commands doesn't require any other inputs.<br/>
Example run: <br/>
make 20 20: creates a 20x20 canvas <br/>
add: adds a blank layer <br/>
current 0 : makes the current image, image 0 <br/>
create checkerboard 10 2: Attempts to create a 10x10 checkerboard image with each square being 2x2 pixel.<br/>
blur/sepia/monochrome/sepia: applies the color transformation/filtering to the current layer <br/>

To create (currently supported images are rainbow or checkherboard), the he model must not be null and there must be a selected current layer. The newly created image must have the same size as the canvas otherwise, the program returns an informational message. The image type must be supported by the model. The layer may or may not have an image already since this commands replaces the old image automatically. This command needs the name of the image created, and 2 integers to determine the size. If the given integers are negative or 0, controller will provide an informational message.<br/>
Example run:<br/>
make 7 7: creates a 7x7 canvas<br/>
add: adds a blank layer<br/>
current 0 : makes the current image, image 0<br/>
create rainbow 7 1: Attempts to create a rainbow with width of 7 pixels, and each color with the height of 1 pixel.<br/>

To rename an image, ther user must need to provide the command: "rename" and the new name of the image. For renaming, the model must not be null, there must be a selected current layer and in the selected layer there must be an image. <br/>
Example run:<br/>
make 7 7: creates a 7x7 canvas<br/>
add: adds a blank layer<br/>
current 0 : makes the current image, image 0<br/>
create rainbow 7 1: Attempts to create a rainbow with width of 7 pixels, and each color with the height of 1 pixel.<br/>
rename rain: names the rainbow image created to "rain"<br/>


To import a singular image, users can use the command "import". This command requires a filePath to a valid file. If the file given was not valid, the controller will ask for a valid file again. To import image, the model must not be null, there must be a selected current layer and the imported image must be a file type supported by the program (currently .ppm, .png, .jpeg is supported). Import image works with all size canvas because the image will be automatically cropped<br/>
Example run:<br/>
make 7 7: creates a 7x7 canvas<br/>
add: adds a blank layer<br/>
current 0 : makes the current image, image 0<br/>
import res/example.ppm: if res/example.ppm is a valid file, it will import the image to the current layer.<br/>

To export the top most image, the users must provide the command "save first" and a filename with a supported extension (currently .ppm, .png, .jpeg is supported).
The program exports the top most image to the given file name. To import image, the model must not be null and the top most layer must have an image. <br/>
Example run:<br/>
make 7 7: creates a 7x7 canvas<br/>
add: adds a blank layer<br/>
current 0 : makes the current image, image 0<br/>
create rainbow 7 1: Attempts to create a rainbow with width of 7 pixels, and each color with the height of 1 pixel.<br/>
save first rainbow.png: exports the rainbow to a file named rainbow.png as a png file.<br/>



## Example Runs
Script 1:.<br/>
make 8 8: Makes a model with an 8x8 canvas.<br/>
add: Adds a blank layer.<br/>
add: Adds a blank layer.<br/>
add: Adss a blank layer.<br/>
create checkerboard 2 4: Attempts to create a 2x2 checkerboard image with each square being 4x4 pixel. This will return a message saying that it was unsuccessful as nothing was set to current.<br/>
current 1: Sets layer 1 as current.<br/>
create rainbow 90 90: Attempts to create a rainbow image in layer 1. This will return a message saying the desired rainbow is too large to fit into a layer.<br/>
create checkerBOARD 2 4: Attempts to create a 2x2 checkerboard image with each square being 4x4 pixels in layer 1. This will succeed.<br/>
sepIa: Applies sepia filter to current layer (layer 1).<br/>
MONOCHROME: Applies monochrome filter to current layer (layer 1).<br/>
copy 1: Copies the first layer and places the copy on the top of the layered image.<br/>
delete 0: Deletes layer 0.<br/>
add: Adds a blank layer.<br/>
current 3: Sets layer 3 as current.<br/>
create checkerboard 2 4: Attempts to create a 2x2 checkerboard image with each square being 4x4 pixels in layer 3. This will succeed.<br/>
invisible 3: Makes layer 3 invisible.<br/>
BLUR: Applies blur filter to current layer (layer 3).<br/>
visible 3: Makes layer 3 visible.<br/>
blur: Applies blur filter to current layer (layer 3).<br/>
renAmE image 3 : renames the current layer's image to image (layer 3).<br/>
current 2: Sets layer 2 as current.<br/>
sharpen: Applies sharpen filter to current layer (layer 2).<br/>
create checkerboard 2 4 : creates a checkerboard with 2x2 checkerboard image with each square being 4x4 pixel and replaces the current image with this image.<br/>
sharpen : sharpen the current layer's image (layer 2).<br/>
delete 0 : deletes layer 0.<br/>
delete  1 : deletes layer 1.<br/>
add: Adds a blank layer.<br/>
current 2 : sets the current layer to layer 2.<br/>
blur : Attempts to blur the image in layer 2 however, it is empty. <br/>
import Shirt.ppm : Imports the image with the file path Shirt.ppm to the current layer (layer 2) <br/>
rename light : renames the current layers' image (Shirt.ppm) to light <br/>
save first export.ppm : Exports the top most layer of the model's image to a file named export.ppm. The image is a ppm file<br/>
SAVE all jpeg locationOfAllImages.txt : Exports all images in the model as jpeg images. The file path of teh images are stored in a file called locationOfAllImages.txt.<br/>

Script 2: <br/>
make 100 100 : Makes a model with an 100x100 canvas.<br/>
upload res/script2ImportAllLocations.txt : uploads all the images taht has tehir filepaths written in the res/script2ImportAllLocations.txt file.<br/>
rename hi : Attems to rename an image to hi, but there is not current iamge selected .<br/>
current 2 : Sets teh current image to layer 2 .<br/>
blur : blurs the image in layer 2 .<br/>
make 49 49 : skips this command because there is already a model .<br/>
create rainbow 49 7 : Attempts to create a rainbow however, the size of the rainbow is not the same as the size of the canvas .<br/>
visible 0 : makes the layer 0 visible .<br/>
add : Adds a blank layer.<br/>
add : Adds a blank layer.<br/>
add : Adds a blank layer.<br/>
current 0 :Sets the current layer to 0.<br/>
BLUR : blurs the image in layer 0 .<br/>
create RAINbOW 49 7 : attempts to create a rainbow however, the size of the rainbow is not the same as the size of the canvas .<br/>
sepia : applies the sepia filter to image in layer 0.<br/>
COPY 0 : creates a copy of layer 0 and adds it to the model.<br/>
delete 5 : deletes layer 5 off the model.<br/>
delete 4 current 1 : deletes layer 4 off the model and sets the current layer to layer 1.<br/>
import notAValidfile.ppm : Attempts to import a file however, the given file path doesn't exist.<br/>
res/Shirt.ppm : imports the file with the file path res/Shirt.ppm and replaces the image in layer 1. <br/>
sePIa: applies the sepia filter to the image in layer 1. <br/>
invisible 2 : makes the image in layer 2 invisible. <br/>
visible 20 : attempts to make the ayer 20 visible but layer 20 doesn't exist. <br/>
current 1 : sets the current layer to layer 1.<br/>
rename helloImage : renames the image in layer 1 to helloImage.<br/>
save all png allImagesSavedPNG.txt : saves all the images in the model as png images. Saves the filepath's of the images into the text file called allImagesSavedPNG.txt. <br/>
q : quits reading the file .  <br/>
add
add

