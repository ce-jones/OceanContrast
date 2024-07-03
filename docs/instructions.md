# auto_SAR_Ocean_Contrast \(autonomous Ocean Contrast Estimation for SAR Images\)
# Instructions
[Input files](https://github.com/ce-jones/OceanContrast/edit/main/docs/instructions.md#1-input-files)  
[Instructions for running the code](https://github.com/ce-jones/OceanContrast/edit/main/docs/instructions.md#2-instructions-for-running-the-code)  
[Output files](https://github.com/ce-jones/OceanContrast/edit/main/docs/instructions.md#3-output-files)  
[Sample data](https://github.com/ce-jones/OceanContrast/edit/main/docs/instructions.md#4-sample-data)  

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
The code also works with a NetCDF file in the [NOAA CoastWatch](https://coastwatch.noaa.gov/cwn/data-access-tools/coastwatch-data-portal.html) file format.  This file contains the calibrated image with land masked and an incidence angle layer.

*Information on the NOAA CoastWatch file format is [here](https://www.star.nesdis.noaa.gov/socd/coastwatch/cwf/cw_cf_metadata.pdf).  We make no commitment that this description is up-to-date so check the [sample input data file](https://github.com/ce-jones/OceanContrast/edit/main/docs/instructions.md#4-sample-data) to see the contents.*

**Optional Land Mask**  
In the mask, values 0=water and 1=land.  The land mask is a flat binary file in real*4 format (32-bit real). An ENVI .hdr file is required to specify the dimensions of the grid.  There has to be a 1:1 correspondence between the land mask grid and the NRCS file grid.  

## 2. Instructions for running the code

The Jupyer Notebook auto_calc_contrast_in_ocean.ipynb contains the code for the algorithm and shows example output with debug mode enabled.  Here in the first code block the user sets the working directory (parameter *wd*) and whether to display additional plots at intermediate steps in the processing \(debug = True\).

A config.yaml file is used to describe input data and select processing options. The directory [prototypes/ FIX THIS LINK](github.com/ce-jones/OceanContrast/edit/main/prototypes) contains example files for each input data format, which can be edited and renamed to config.yaml for running the code.  The config.yaml file needs to be in the working directory (top level).

**config.yaml**
a. A config.yaml file is used to inform the  
a. The user needs to modify the working directory at the top of the code \(wd\) to point to the directory containing the input imag\
e files and the config.yaml file.
**Jupyter Notebook \(.ipynb\) or Python \(.py\)**


## 3. Output files
The code generates two main output files or layers, several JPG images visualizing the results, and one JPG showing the statistical distribution of the ocean NRCS values and the threshold chosen automatically for identifying "radar-dark" pixels. 

Presently, this code can handle ENVI, GeoTIFF, and NetCDF formats on the input side.  The output can either be the same format or ENVI format.  No protection is written for invalid output formats -- the code will just crash.

<img width="394" alt="Screenshot 2024-07-03 at 11 38 06 AM" src="https://github.com/ce-jones/OceanContrast/assets/20935561/fdcf604c-9a42-4f45-a01b-cd958121924f">

### a. GeoTIFF output

#### Output: Contrast ratio file <br> This file contains the contrast ratio for all pixels in the scene.
  *filename*_JPL*N*_*qp*DR_contrast_ratio.tif<br>
  *filename* = input file name<br>
  *N* = code version number<br>
  *pq* = polarization<br>

### Output: Cumulative distribution
#### This files contains the ranking of the pixels identified as radar-dark (distinct from clean/bright water) on a scale from 0 to 1 based upon the contrast ratio.  Smaller values correspond to lower contrast ratios.
  *filename*_JPL*N*_*pq*DR_cumulative.tif
  
## 4. Sample data
Sample input and output files for each input format option are available at ****
