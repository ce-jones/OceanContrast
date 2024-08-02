# auto_SAR_Ocean_Contrast \(autonomous Ocean Contrast Estimation for SAR Images\)

# Installation

## 1. Requirements
The GeoTIFF interface requires *libgdal 3.8.4* or later.  There are many ways 
to install this on your system, e.g., macports (*port install gdal*).  This should happen automatically when following the instructions below.

## 2. Installation without using Conda environments)

To install the libraries for this package, after 'git pull ...', run this from the auto\_SAR\_Ocean\_Contrast directory:
  
    git clone https://github.com/nasa-jpl/auto_SAR_Ocean_Contrast.git
    cd auto_SAR_Ocean_Contrast
    pip install -e . 

## 3. Installation in new conda environment

If you use conda, then do this:
  
    conda create --name NEW-ENV python=<version no.>
    conda activate NEW-ENV
    conda install gdal
    git clone https://github.com/nasa-jpl/auto_SAR_Ocean_Contrast.git
    cd auto_SAR_Ocean_Contrast
    pip install -e .

Note: The code was tested on an M1 Mac and worked with python 3.9.
