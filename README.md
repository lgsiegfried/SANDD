# SANDD
standard algorithm for nuclear DAB detection in keratinocytes

## Objective
* To automate nuclear diaminobenzidine staining (IHC) of epidermal nuclei with minimal subjectivity and improved accuracy

## Pre-processing
* High-resolution brightfield images must be pre-processed using Adobe Photoshop to isolate only the viable epidermis.
* Use the eraser tool to remove any dermis, endothelium, cornified or nonviable tissue, and negative space so that only the epidermis is present on a transparent background.
* Crop the image appropriately to center the epidermis.
* Use the "Selective Color" tool in Photoshop to remove all blue from the red channel. 
* Export the image in full resolution in the desired format into a directory or subdirectory located with the code file. For the development of this code, all images used were in TIFF format.

## Code functionality
* The image is split into nuclei and cytoplasm, and the nuclei are then located and counted.
* For each nucleus that meets the size constraints, each pixel within the boundary of the nucleus is analyzed for color to determine if the pixel is brown, relative to the cytoplasm.
* More than 40% positive pixels sets a nucleus to positive. 
* The final output includes total, positive, and negative nuclei counts, as well as images for localization.

## Functions
### imagePrepare
* Parameters: pre-processed image of viable epidermis
* Reads in image file, converts to RGB and LAB color spaces
* Binary thresholding to separate nuclei and cytoplasm

### contourFinder
* Parameters: binary image of nuclei only
* Locates nuclei contours, returns an image for visualization and an array of contour coordinates

### cytoColor
* Parameters: binary image of whole epidermis, binary image of nuclei only, original image in LAB color space
* Identifies the cytoplasm and calculates the average color as red/blue ratio for relative comparison to the nuclei color to account for variability of IHC staining.
* Optimization for different stainings may not require this function. In developing this application, this function was used for pGR quantification but not used for cMyc quantification due to different staining approaches.

### maskMaker
* Parameters: binary image of nuclei only, color image in LAB color space, array of contour coordinates
* Creates a mask within the bounds of the contours identified for the given nucleus and determines nucleus size characteristics.

### colorCalc
* Parameters: array of contour coordinates, color image in LAB color space, original image, binary image of nuclei only, and cytoplasm color
* Iterates through each pixel within each contour, calculates the color, records counts of positive and negative nuclei, and returns image with nuclei outlined in blue or red to designate positive and negative, respectively.

### runTotal
* Parameters: string filename of the pre-processed image.
* Calls the preceding functions in order to coordinate image analysis.
