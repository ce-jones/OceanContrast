# auto_SAR_Ocean_Contrast \(autonomous Ocean Contrast Estimation for SAR Images\)

[![Language](https://img.shields.io/badge/python-3.6%2B-blue.svg)](https://www.python.org/)
[![Latest version](https://img.shields.io/badge/latest%20version-v1.0-yellowgreen.svg)](https://github.com/leiyangleon/autoRIFT/releases)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/leiyangleon/autoRIFT/blob/master/LICENSE)
[![Citation](https://img.shields.io/badge/DOI-PUTHERE-blue)](https://doi.org/ADD)

### Update Notes:

```diff
+ 
```


**A Python module for estimating the contrast in a SAR image of the ocean surface, relative to clean water pixels.  The code is primarily intended to identify oil slicks, but can be used to identify any radar-dark feature in a scene that is not entirely radar-dark. The entires scene cannot be radar-dark.**

**The contrast is defined as $\sigma^{clean}(\theta)\over\sigma(\theta)$, where $\sigma(\theta)$ is the calibrated Normalized Radar Cross Section (NRCS), which depends upon the incidence angle, $\theta$. The algorithm identifies high confidence clean sea pixels based on the statistics of the SAR intensity to calculate the ratio, as described in \[Jones, 2023\].**

**autoSAROceanContrast is a standalone Python module that has been tested with SAR images acquired in L-, S-, C-, and X-band and in polarizations modes VV, HH, HV, and VH.  It works on images in radar coordinates or on a georeferenced grid, and requires a map of the incidence angle for each pixel in the scene.  If land is in the scene, the user can mask it out in the provided NRCS data or optionally can specify that a user-provided land mask file be used.**

**There are two output files, one containing the contrast ratio and the other containing the cumulative distribution function's value for those pixels that are identified as being radar-dark relative to the identified as likely clean water pixels, i.e., having a contrast ratio significantly higher than that of the clean water peak, which is centered about a value of 1.  This threshold is set adaptively based upon the statistics of the contrast ratio for the scene.  Various png figures are also output.**

Copyright (C) 2024 California Institute of Technology.  Government Sponsorship Acknowledged.

Link: https://github.com/nasa-jpl/autoSAROceanContrast

Citation: TBD https://doi.org/...


## 1. Authors

Cathleen E. Jones (JPL/Caltech; cathleen.e.jones@jpl.nasa.gov) developed the algorithm, which is described in (Jones, 2013), developed the first version in MATLAB, and tested and refined it for SAR data from UAVSAR, FSAR, ISRO/ASAR, Sentinel-1, TerraSAR-X, and Radarsat-2.

Peter Mao (JPL/Caltech; peter.mao@jpl.nasa.gov) translated the MATLAB code to Python, further optimized the algorithm, and developed its sister module autoSpillID for oil spill classification.

**Reference:** 

***1.***Jones, C. E. (2023). An automated algorithm for calculating the ocean contrast in support of oil spill response. Marine Pollution Bulletin, 191, 114952.

## 2. [Installion](/docs/install.md)


## 3. [Instructions](/docs/instructions.md)

## 1. Input files
The code requires a calibrated SAR image file and an incidence angle file or layer on the same grid as the image.  The input can be in the following formats:

**Geotiff**

Band 1 - Calibrated SAR image (in linear units or dB)
Band 2 - Incidence angle \(in degrees or radians\)
Optional Band 3 - Latitude \(not used by this code\)
Optional Band 4 - Longitude \(not used by this code\)

**2. Binary Raster**
This option is intended to work with UAVSAR geocoded .grd files from the UAVSAR PolSAR standard product, using the incidence angle .inc file provided.  This is a flat binary file in real*4 format (32-bit real). An ENVI .hdr file is required to specify the dimensions of the grid.

**3. NetCDF**
The code also works with a NetCDF file in the NOAA CoastWatch file format.  This file contains the calibrated image with land masked and an incidence angle layer.

**4. Optional Land Mask
In the mask, values 1 indicate land and 0 indicates water. CHECK THIS

## 2. Instructions for running the code

a. A config.yaml file is used to inform the  
a. The user needs to modify the working directory at the top of the code \(wd\) to point to the directory containing the input imag\
e files and the config.yaml file.
The Jupyer Notebook auto_calc_contrast_in_ocean.ipynb contains the code for the algorithm and shows example output with debug mode enabled.

## 3. Output files

## 4. Sample data
Sample input and output files for each input format option are available at ****

## 5. [Algorithm](/docs/algorithm.md)

## 6. [Related Open Source Code](/docs/related.md)

NOTE: We intend to add open source code to classify the radar-dark pixels in the scene based upon damping ratio, to aid in identifying the thickest oil in a slick for emergency response.

## 7. Acknowledgement

This effort was funded by the NASA 2018 *A.37 Earth Science Applications: Disaster Risk Reduction and Response* call's  Marine Oil Thickness (MOST) project, P.I. Francis Monaldo (NOAA).




