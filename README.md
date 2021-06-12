# Assignment 5

Our model design boils down to three layers of abstraction. The first layer, which is intended for client use, is the model. The model has-a manager object. The manager has-a image object. In each layer of abstraction, we aimed to keep functions short, choosing to delegate to other layers if possible. Every field in our design is private to ensure encapsulation.

## MODEL
Our model interface is called IPModel (IP stands for Image Processing). This interface extends our IPModelState, which acts as a ViewModel. IPModelState does not contain any methods that modify the model and it was created in anticipation of the View. On the other hand, IPModel contains methods that mutate the model and were explicitly specified in the assignment. The implementation of IPModel is SimpleIPModel. The SimpleIPModel has one field, the manager. The manager holds an image and keeps track of relevant information about the state of the manager (i.e. whether an image exists in the manager, name of the image, etc). The methods within SimpleIPModel are very straightforward and only have one purpose.

## MANAGER
The manager delegate is the most powerful class in our model implementation, hence why we decided to not give the client direct access. The manager interface is called IPManager. The IPManager contains methods that mutate the state of the manager. The methods in this interface are abstracted and heavily rely upon function objects to allow for easy extension. The majority of exceptions are thrown by the manager to allow for simplistic functions in the model. The implementation of this interface is SimpleIPManager. The SimpleIPManager only holds one image at a time. It also contains a boolean flag, indicating whether an image exists in the manager. Finally, it contains a String representation of the image currently in the manager, which may be changed. 

## IMAGE REPRESENTATION
We decided to call our representation of an image BitmapImage after the bits used in images. This class implements the ImageRepresentation interface, which includes functions that directly modify an image and reveal characteristics about an image. The BitmapImage has a pixelMap (named after PPM files) which is a 2D ArrayList of pixels. Each BitmapImage also has a height, width, and maximum value for RGB components. 

### PIXEL
Pixel is our class to represent a pixel in space. Each pixel contains an x and y coordinate and a color. All fields, except for color, are final to ensure invariance. 

## FUNCTION OBJECTS 
We decided upon the use of function objects for abstraction purposes. We had four different types of function interfaces, one for each type of operation we had to support.

In the Effects package, we have two function interfaces that directly manipulate images. The two interfaces, FilterEffect and ColorTransformationEffect, each have one method, getKernel(), which returns the 2D ArrayList(or matrix) provided in the assignment. We decided to separate the two functions since kernel size can vary in the filter, but not in the color transformation. For FilterEffect, Blur and Sharpen implement the interface and method. For ColorTransformation, Sepia and Monochrome implement the interface and method.

In the FileType package, we have the Filetype interface, which is intended to represent a different file type (i.e. PPM, JPG, PNG). There are two methods in the Filetype interface, import and export. Import will import a file of that type into an image representation, while export will export the image representation into the file type. The only class that implements this interface is PPMFile, as it is the only file type that is supported currently.

In the PixelCreator package, we have the CreatePixelInterface. This interface represents the types of images that can be created programmatically. The only method is createImage, which returns a pixelMap that represents the image. CreateCheckerBoard and CreateRainbow implement this interface. As their names suggest, CreateCheckerBoard creates a checkerboard image and CreateRainbow creates a rainbow image.

## MISC.
We have a factory class (ImageRepresentationCreator) that creates an instance of an ImageRepresentation depending on the enum passed into the static method. We also have a Utils class that contains some functions that we continuously reused across several classes.

BOTH IMAGES USED IN THIS PROJECT ARE OWNED BY ANIA MISIOREK. I AUTHORIZE THE USE OF MY IMAGES FOR THIS PROJECT.


