This folder contains what is needed to obtain (thanks to a jupyter-notebook code and a list of shapefiles over 12 days) an interactive visualisation allowing us to see which WV SLC data are available and their name so that one can easily download them.

WV_Image_01_2019_All.zip is an example of shapefiles obtained from the .xml files of Sentinel-1 WV data for 12 days from 1 January 2019 to 12 January 2019. Thanks to a code that will soon be available on this Github, all these shapefiles have been created from a downloaded stack of .xml files.

The jupyter notebook Interactive_Map.ipynb takes the folder containing the shapefiles as input. There is a **createValidatedShapefiles** parameter that allows using only shapefiles on land. To do this, run the program once and select zero for this parameter. Thus, in addition to the interactive map, we will obtain a vector stored in **ValidatedShapefiles.npy**, which contains the indices of the shapefiles located on the earth. When the program is used afterwards with 1, only the shapefiles on the land are used, allowing for a lighter and faster program.

The following images are obtained with the dataset provided, with a value of 0 then 1 for the **createValidatedShapefiles** parameter. In this example, the ratio between the number of shapefiles used in total and on land is about 25.

<p align="center">
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Interactive_Shapefile_Project/InteractiveMapFull.png" />
</p>

<p align="center">
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Interactive_Shapefile_Project/InteractiveMapFullLand.png" />
</p>

When the mouse cursor browses a marker, an identifier is obtained, allowing the corresponding data to be downloaded. The last number corresponds to the swath number of the WV SLC data. The rest of the identifier corresponds to the mission data-take identifier and the unique product identifier. With this information and the acquisition date, it is possible to find the corresponding data and download it easily. It is easy to download the time stack above this area by retrieving the path and frame of this data.

<p align="center">
  <img src="https://github.com/NathanPaillou/Sentinel_1_WV_SLC/blob/main/Interactive_Shapefile_Project/InteractiveMapHovering.png" />
</p>
