# SANDD protocol

## Image pre-processing
1.	Import images into Photoshop for isolation of the nucleated epidermis. 
2.	Duplicate the background layer and hide the original layer for preservation of the original image in the case that starting over is needed. 
3.	Using the eraser tool, remove all negative space surrounding the tissue section, as well as dermis, endothelium, and cornified layers. 
4.	Erase any areas of folding or those out of focus. The minimum number of nuclei used in testing this protocol was 2000. 
5.	Once only the nucleated epidermis remains in the image, apply the Selective Color adjustment under Image > Adjustments. Navigate to the “blue” channel and set the yellow slider within the blue channel to -100. This step enhances the hematoxylin counterstain and increases the contrast between the chromogen and hematoxylin. 
6.	Image > size > image size > double the size of the image by doubling the width or height pixel number, make sure “preserve details 2.0 (enlargement)” is on
7.	Crop the image so that the epidermis is bounded with minimal negative space. 
8.	Save the image as a TIFF, ensuring run-length encoding (RLE) layer compression, bit interleaved by pixel, and no image compression options are selected. For ease of use, it is strongly recommended to save the images in the same directory or folder where the code file is located. It is also recommended to use short filenames that do not contain spaces and to document relationships between short and long identifiers as needed. 

## Python IDE setup
* The SANDD program files are available as Jupyter notebook files but can be used in any preferred Python IDE. Directions for downloading and setting up Anaconda are below:
* Download Anaconda here: https://www.anaconda.com/products/distribution
1.	In the Anaconda Navigator, create an environment using the “Create” button in the “Environments” tab, naming it as desired and selecting Python version 3.9.12.  
2.	With the new environment selected, a search bar in the top right corner allows one to parse through available Python packages. Installation is only necessary upon first use, given that one is using the same environment for every session. Search the following terms and proceed with installation: 
  *	Jupyterlab 
  *	Numpy 
  *	Opencv 
  *	Matplotlib 
3.	Selecting the green play button next to the environment name provides the option to open Jupyter Notebook within the environment and opens a new browser window resembling a Finder or File Manager window. Navigating to the directory in which a notebook file (such as the source code for this protocol) is located allows the option to open and fully interact with that notebook file. 

## Running the program
1.	Open the code file in Jupyter Notebook. 
2.	In the final line of code, insert the name of the processed image file between the quotation marks so that the line reads: runTotal(‘your_file.tif”). 
3.	In the header bar, select the “Run” button. 
4.	The program will print out information and export images throughout the run process that confirms it is actively running, as well as an asterisk (*) in the square brackets in the top left adjacent to the first line of the cell in Jupyter Notebook. On completion of the run, this asterisk is replaced with a number. 
5.	The result of the program will be a text print-out of the counts of total, positive, and negative nuclei, as well as an image with positive and negative nuclei outlined in red and blue, respectively. 
6.	Create a folder in your working directory with the name of your sample and put all image readouts in there so that nothing is overwritten.
7.	Keep track of the counts in Excel for downstream data analysis.
