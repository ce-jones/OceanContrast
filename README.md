# auto_SAR_Ocean_Contrast \(autonomous Ocean Contrast Estimation for SAR Images\)

[![Language](https://img.shields.io/badge/python-3.6%2B-blue.svg)](https://www.python.org/)
[![Latest version CHANGE LINK](https://img.shields.io/badge/latest%20version-v1-yellowgreen.svg)](https://github.com/leiyangleon/autoRIFT/releases)
[![License CHANGE LINK](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/leiyangleon/autoRIFT/blob/master/LICENSE)
[![Citation](https://img.shields.io/badge/DOI-PUTHERE-blue)](https://doi.org/ADD)

### Update Notes:

```diff
+ 
```


**A Python module for estimating the contrast in a SAR image of the ocean surface, relative to clean water pixels.  The code is primarily intended to identify oil slicks, but can be used to identify any radar-dark feature in a scene that is not entirely radar-dark. The contrast ratio is often referred to as the damping ratio in the scientific literature concerning mineral oil slicks.**

**The contrast is defined as $\sigma^{clean}(\theta)\over\sigma(\theta)$, where $\sigma(\theta)$ is the calibrated Normalized Radar Cross Section (NRCS), which depends upon the incidence angle, $\theta$. The algorithm identifies high confidence clean sea pixels based on the statistics of the SAR intensity to calculate the ratio, as described in \[Jones, 2023\].**

**autoSAROceanContrast is a standalone Python module that has been tested with SAR images acquired in L-, S-, C-, and X-band and in polarizations modes VV, HH, HV, and VH.  It works on images in radar coordinates or on a georeferenced grid, and requires a map of the incidence angle for each pixel in the scene.  If land is in the scene, the user can mask it out in the provided NRCS data or optionally can specify that a user-provided land mask file be used.**

**The outputs are 1\) the contrast ratio for all ocean pixels in the scene, and 2\) the cumulative distribution function's value for those pixels that are identified as being radar-dark, with 0 corresponding the the pixel with the lower contrast ratio and 1 corresponding to the pixel with the highest contrast ratio. Radar-dark pixels are those identified as having a contrast ratio significantly higher than that of the clean water peak, which is centered about a contrast ratio value of 1.  The threshold is set adaptively based upon the statistics of the contrast ratio for the scene.  Various png figures are also output.**

Copyright (C) 2024 California Institute of Technology.  Government Sponsorship Acknowledged.

Link: https://github.com/nasa-jpl/autoSAROceanContrast

Citation: TBD https://doi.org/...


## 1. Authors

Cathleen E. Jones (JPL/Caltech; cathleen.e.jones@jpl.nasa.gov) developed the algorithm, which is described in (Jones, 2013), developed the first version in MATLAB, and tested and refined it for SAR data from UAVSAR, FSAR, ISRO/ASAR, Sentinel-1, TerraSAR-X, and Radarsat-2.

Peter Mao (JPL/Caltech; peter.mao@jpl.nasa.gov) translated the MATLAB code to Python, further optimized the algorithm, and developed its sister module autoSpillID for oil spill classification.

**References:** 

1. Jones, C. E. (2023). An automated algorithm for calculating the ocean contrast in support of oil spill response. Marine Pollution Bulletin, 191, 114952.

## 2. [Installation](/docs/install.md)

## 3. [Instructions](/docs/instructions.md)

## 4. [Algorithm](/docs/algorithm.md)

## 5. Sample data
Sample input and output files for each input format option are available at ****

## 6. Related Open Source Code

NOTE: We intend to add open source code to classify the radar-dark pixels in the scene based upon damping ratio, to aid in identifying the thickest oil in a slick for emergency response.

## 7. Acknowledgement

This effort was funded by the NASA 2018 *A.37 Earth Science Applications: Disaster Risk Reduction and Response* call's  Marine Oil Thickness (MOST) project, P.I. Francis Monaldo (NOAA).

## 8. MOST Project
[NASA-NOAA tech will aid marine oil spill response](https://phys.org/news/2021-12-nasa-noaa-tech-aid-marine-oil.html)

[Hear about the MOST Project on YouTube](https://youtu.be/6brucBsqR-g)

[Detecting oil thickness to aid oil spill response](https://appliedsciences.nasa.gov/our-impact/news/detecting-oil-thickness-aid-oil-spill-response)

[A profile of MOST PI, Frank Monaldo](https://appliedsciences.nasa.gov/our-impact/people/frank-monaldo-making-most-technology-detect-oil-spills)



