# Assignment 6
This USEME includes information on how to run the JAR file, a complete list of functions supported by our program, and example runs.

## How to Use the Program

## Script Commands
### Initial Commands (must be used in order to start the program)
### Layering Commands
### Individual Image Commands

## Example Runs
Script 1:
make 8 8: Makes a model with an 8x8 canvas
add: Adds a blank layer
add: Adds a blank layer
add: Adss a blank layer
create checkerboard 2 4: Attempts to create a 2x2 checkerboard image with each square being 4x4 pixel. This will return a message saying that it was unsuccessful as nothing was set to current
current 1: Sets layer 1 as current
create rainbow 90 90: Attempts to create a rainbow image in layer 1. This will return a message saying the desired rainbow is too large to fit into a layer
create checkerBOARD 2 4: Attempts to create a 2x2 checkerboard image with each square being 4x4 pixels in layer 1. This will succeed
sepIa: Applies sepia filter to current layer (layer 1)
MONOCHROME: Applies monochrome filter to current layer (layer 1)
copy 1: Copies the first layer and places the copy on the top of the layered image
delete 0: Deletes layer 0
add: Adds a blank layer
current 3: Sets layer 3 as current
create checkerboard 2 4: Attempts to create a 2x2 checkerboard image with each square being 4x4 pixels in layer 3. This will succeed
invisible 3: Makes layer 3 invisible
BLUR: Applies blur filter to current layer (layer 3)
visible 3: Makes layer 3 visible
blur: Applies blur filter to current layer (layer 3)
renAmE image 3
current 2: Sets layer 2 as current
sharpen: Applies sharpen filter to current layer (layer 2)
create checkerboard 2 4
sharpen
delete 0
delete 1
add
current 2
blur
import Shirt.ppm
rename light
save first export.ppm
SAVE all jpeg locationOfAllImages.txt

Script 2:
make 100 100
upload script2ImportAllLocations.txt
rename hi
current 2
blur
make 49 49
create rainbow 49 7
visible 0
add
add
add
current 0
BLUR
create RAINbOW 49 7
sepia
COPY 0
delete 5
delete 4 current 1
import notAValidfile.ppm
Shirt.ppm
sePIa
invisible 2
visible 20
current 1
rename helloImage
q
add
add

