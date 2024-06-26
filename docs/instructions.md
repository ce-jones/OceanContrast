# auto_SAR_Ocean_Contrast \(autonomous Ocean Contrast Estimation for SAR Images\)

## 1. Input files
The code requires a calibrated SAR image file and an incidence angle file or layer on the same grid as the image.  The input can be in the following formats:

**Geotiff**

Band 1 - Calibrated SAR image (in linear units or dB)
Band 2 - Incidence angle \(in degrees or radians\)
Optional Band 3 - Latitude \(not used by this code\)
Optional Band 4 - Longitude \(not used by this code\)

**Binary Raster**
This option is intended to work with UAVSAR geocoded .grd files from the UAVSAR PolSAR standard product, using the incidence angle .inc file provided.  This is a flat binary file in real*4 format (32-bit real). An ENVI .hdr file is required to specify the dimensions of the grid.

**NetCDF**
The code also works with a NetCDF file in the NOAA CoastWatch file format.  This file contains the calibrated image with land masked and an incidence angle layer.

**Optional Land Mask**
In the mask, values 1 indicate land and 0 indicates water. CHECK THIS

## 2. Instructions for running the code

a. A config.yaml file is used to inform the  
a. The user needs to modify the working directory at the top of the code \(wd\) to point to the directory containing the input imag\
e files and the config.yaml file.
The Jupyer Notebook auto_calc_contrast_in_ocean.ipynb contains the code for the algorithm and shows example output with debug mode enabled.

## 3. Output files

## 4. Sample data
Sample input and output files for each input format option are available at ****
