# auto_SAR_Ocean_Contrast \(autonomous Ocean Contrast Estimation for SAR Images\)
# Instructions

## 1. Input files
The code requires a calibrated SAR image file and an incidence angle file or layer on the same grid as the image.  The input can be in one of the three following formats:

**Geotiff**

Band 1 - Calibrated SAR image (in linear units or dB)  
Band 2 - Incidence angle \(in degrees or radians\)  
Optional Band 3 - Latitude \(not used by this code\)  
Optional Band 4 - Longitude \(not used by this code\)  

**ENVI Binary Raster**  
This option is intended to work with UAVSAR geocoded .grd files from the UAVSAR PolSAR standard product, using the incidence angle .inc file provided.  This is a flat binary file in real*4 format (32-bit real). An ENVI .hdr file is required to specify the dimensions of the grid and the georeferencing, if provided.  The code works for data in radar coordinates or in geographical coordinates.

**NetCDF**  
The code also works with a NetCDF file in the NOAA CoastWatch file format.  This file contains the calibrated image with land masked and an incidence angle layer.

**Optional Land Mask**  
In the mask, values 0=water and 1=land.  The land mask is a flat binary file in real*4 format (32-bit real). An ENVI .hdr file is required to specify the dimensions of the grid.  There has to be a 1:1 correspondence between the land mask grid and the NRCS file grid.  

## 2. Instructions for running the code

**config.yaml**
a. A config.yaml file is used to inform the  
a. The user needs to modify the working directory at the top of the code \(wd\) to point to the directory containing the input imag\
e files and the config.yaml file.
**Jupyter Notebook \(.ipynb\) or Python \(.py\)**
The Jupyer Notebook auto_calc_contrast_in_ocean.ipynb contains the code for the algorithm and shows example output with debug mode enabled.  Here in the first code block the user sets the working directory (parameter *wd*) and whether to display additional plots at intermediate steps in the processing \(debug = True\).

## 3. Output files
The code generates two main output files and a number of JPG images visualizing the results and one JPL showing the statistical distribution of the ocean NRCS values and the threshold set for "radar-dark" pixels. 

Presently, this code can handle ENVI, GeoTIFF, and NetCDF formats on the input side.  The output can either be the same format or ENVI.  No protection is written for invalid output formats -- the code will just crash.

  | input \ ouput-> | ENVI | GeoTIFF | NetCDF |
  |-----------------+------+---------+--------|
  | ENVI            | Y    | N       | N      |
  | GeoTIFF         | Y    | Y       | N      |
  | NetCDF          | Y    | N       | Y      |

### 1. Contrast ratio file
  *filename*_JPL*N*_VVDR_contrastratio.\(tif/nc/dat\)
  *filename* = input file name
  *N* = code version number

### 2. Cumulative distribution


## 4. Sample data
Sample input and output files for each input format option are available at ****
