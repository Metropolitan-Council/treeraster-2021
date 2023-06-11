# Introduction

This GitHub repository hosts raster tile layers for interactive mapping. Currently, it is not possible to host raster tiles using the Council's ESRI/ArcGIS tools (only vector tiles), but fortunately there is a work around with GitHub! Hosting raster tiles will probably become increasingly common as mapping resolution improves in a variety of applications. 

This repo specifically hosts **tree canopy tiles for the year 2021**. This tile layer is integral to [Growing Shade](www.GrowingShade.com). 

This is how to use (and create) raster tile hosting using GitHub in conjuction with Google Earth Engine (to date, the best tool for large (planetary!) scale and/or detailed processing of satellite imagery and remote sensing analyses):
1) Use Google Earth Engine (or other) to [create and export raster tiles to Google Cloud storage](https://developers.google.com/earth-engine/apidocs/export-image-tocloudstorage). I'd reccomend a minimum tile zoom of 9 and a maximum zoom of 17. 
2) [Download/install gsutil](https://cloud.google.com/storage/docs/discover-object-storage-gsutil?_ga=2.130204239.-1967626043.1669658852) in order to access the files from the cloud. 
3) Select the tile folder you want to access within your Google Cloud storage bucket, and select "download." Copy and paste the pop-up code into the terminal to start download. (you may need to authenticate gsutil; type $ gcloud auth login). 
4) Once the tiles are downloaded on your machine, create a new GitHub repository (yes, the repo has to be fresh/can't contain other elements). Slowly(!!) upload the different tile folders up to GitHub. 
5) Create a GitHub page (settings, pages, deploy from branch, main branch, /root) and wait for it to deploy.
6) In leaflet, you can now fetch the GitHub hosted raster map tiles! (be sure to copy the GitHub pages url, add the folder the map tiles are within, and then add "{z}/{x}/{y}" at the end of the url) 
```
leaflet() %>%
addTiles("https://metropolitan-council.github.io/treeraster-2021/GrowingShadeTealTrees_2021_toCloud/{z}/{x}/{y}")
```
