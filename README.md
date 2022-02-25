Project realised by Thomas Di Martino, Nathan Paillou and Thibault Taillade

Contact: nathan.paillou@centralesupelec.fr

# Ongoing Project, Sentinel-1 WV (WAVE) mode SLC Data process

This is the repository for the code allowing to process Sentinel-1 WV mode SLC Data. The main motivation of this contribution is driven by the fact that Level 1 WV mode is currently not well supported by SNAP (https://step.esa.int/main/download/snap-download/). This mode provides however higher resolution capabilities than the IW mode (Interferometric Wide Swath). Having a peculiar acquisition pattern that is prohibitive for large scale Land analysis, it might be nevertheless of interest for experimental studies in diverse applications. This is an ongoing project, some functions are still to be checked and others will be added.


## File Exploration

The most important files are:

 - WV_PROCESSING.ipynb notebook: this file contains the function used to unzip data and create a calibrated stack of the selected swath. The calibration procedure is based on the following document : "Radiometric Calibration of S-1 Level-1 Products Generated
by the S-1 IPF" (https://sentinels.copernicus.eu/documents/247904/685163/S1-Radiometric-Calibration-V1.0.pdf/66e69a62-11ae-4160-916b-f2b97cb8a350?t=1432307754000)
 - the shapefiles in the Shapefiles repository: it allows to see, using Google Earth Engine for example, the location of available data every 6 month. A jupyter notebook for online visualisation is being created and can be found in the repository Interactive_Shapefile_Project.


## Installation
I advise the use of Anaconda distribution to run the code of this project. An anaconda environment file has been generated and can be used to create a new working environment using the following command:
```
conda env create -f environment.yml
```


## Execution
To execute the main code of this project, you can start a jupyter notebook and then run the WV_PROCESSING.ipynb. The path and swath variables have to be edited.


## Available Data

Sentinel-1 WV data are located mostly over seas and oceans only in VV polarization. This mode offers a particular acquisition pattern described in the following link: https://sentinels.copernicus.eu/web/sentinel/user-guides/sentinel-1-sar/acquisition-modes/wave.  However, depending on the period, some data are available over land areas, as shown in this image (Google Earth screenshots with associated WV swaths).

<p align="center">
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Shapefiles/Areas_example.png" />
</p>

In the Shapefiles folder are available data for 8 periods. In each case, the footprints correspond to the data available between the date indicated and 12 days later, to take into account the revisit time of the Sentinel-1 satellite. The result is a global map of available data, as shown in the following image.
<p align="center">
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Shapefiles/Shapefile_Example.png" />
</p>

In a future version, a code will be available to obtain this map for a selected period.

## Data Download

The download has been made using Alaska Satellite Facility https://search.asf.alaska.edu/#/. By using filters to select L2 Ocean as File Type and WV as Beam Mode, one can see if data are available at a precise date and location. After that the desired data have to be downloaded, using the L1 Single Look Complex filter.

## Results  

The output of the main code is matlab matrices, two matrices per dates. For each date there is a complex matrix correspondong to the backscatter coefficients and a real matrix corresponding to sigma_0.

We compare here visualy the results obtained on a city near Manhattan. On the left is a calibrated WV image (multi-looked with a 5x5 window size) and on the right an IW image obtained on Google Earth Engine.

<p float="letf">
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Example/WV_MLC_55.png" width="400" height="300" />
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Example/NewIW.png" width="400" height="300"  />
</p>

By comparing visualy these two images, we can easily see that the WV data allows a better study of this area due to its better resolution. It is, for example, possible to try to detect roads on the WV image while they are not visible on the IW image. Before these two images can be accurately compared, it is necessary to geolocate the WV data. In a future version, this step will be performed.

## Future updates
- Jupyter notebook for shapefiles visualisation
- Jupyter notebook to obtain available data at a precise date
- Data Geolocalisation
- Stack coregistration

The expected final result after all these modifications is a calibrated, geolocated and calibrated data stack, as shown in this gif.

<p align="center">
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Example/Manhattan_region_VV_WV.gif" />
</p>

With such a time series, it is possible to perform temporal processing. The following image is a time average of the intensity over 20 dates.

<p align="center">
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Example/WV_Temporal_20.png" />
</p>

WV Sentinel 1 images may be of interest for dedicated study where higher resolution than IW mode is required, yet not exploited by the community.
Indeed, even though the WV mode acquisition pattern enable only the imaging of vignettes (20 x 20 km every 100km), its temporal consistency in some land areas may represent an interesting source of information.
