# Spatial_final_assignment
Repository for the spatial assignment - Sea voyages in the 18th and 19th century. 

## ------ SCRIPT DESCRIPTION ------
This repository contains a R-markdown script that takes data from CLIWOC and Globcurrents to asses sea routes and how effeciency they are in choosing routes that sail with the surface currents of the ocean.

## ------ REQUIREMENTS ------
**Program requirements**
- R v. 4.1.1
- R-Studio v.1.4.1717

**Package requirements**
- tidyverse v. 1.3.1
- sf v. 1.0-4
- raster v. 3.5-2
- geojsonsf v. 2.0.1
- rgdal v. 1.5-27
- ncdf4 v. 1.19
- RColorBrewer v. 1.1-2
- maptools v. 1.1-2
- ggplot2 v. 3.3.5
- scales v. 1.2.0

## ------ DATA ------
This script mainly utilises two datasets.

**Cli**matological Database for the **W**orld's **Oc**eans, or **CLIWOC** for short, contains ca. 287.000 different logbook entries across 8 nations from 1662-1855. However, that vast majority of these are from british, dutch, french and spanish ships from 1750-1850, and the script filters out all other nations. The original EU-funded project was created in the early 2000's as a cooperation across a range of different unversities. Although it was intended to be used to, as the name might suggest, map and research climatological behavior and changes, it has since been used for a wide range of different purposes. As might have bee expected from a project created in the early 2000's, it is however not very accesiable as it requires the use of programs such as MS ACCESS. Thankfully the database has been updated by others and can now in more modern formats. The table explaining each variable found on the original website, is however still of immense value.
- Link to original database: https://webs.ucm.es/info/cliwoc/
- Link to updated database: https://www.historicalclimatology.com/cliwoc.html


**GlobCurrent** provided that files needed to create the currents raster. While the original files also had the direction of ocean currents, that information was lost when converted to a raster file. As the north-south current raster was deemed unusable, <ins>route effiecieny is based exclusivly on east-west currents!</ins> The data used was the total surface currents on the first of january 1993. As ocean currents have been observed to be accelerating in recent years, it was important to use the oldest data available to best model currents that might match those 150+ years earlier. Access to the data requires a free and simple registration.
- Link to GlobCurrent: http://globcurrent.ifremer.fr
- Path to data: data/globcurrent/v3.0/global_025_deg/total_hs/1993/001/19930101-GLOBCURRENT-L4-CUReul_hs-ALT_SUM-v03.0-fv01.0.nc

Finally a geojson containing a shapefile of the currents was used to illustrate the shortcommings of the abovementioned currents raster.
- Link: https://data.amerigeoss.org/en/dataset/major-ocean-currents-arrowpolys-1m-104/resource/9ccf6bbb-c2d3-44be-bcd4-7e429a876e72

## ------ REPO STRUCTURE ------
"data" FOLDER:
- This folder contains all data used by the r-markdown
- The .RData files are created by the script, but can be downloaded instead, as the code needed to create them take 1.5-2.5 hours each.

"relevant_reading" FOLDER:
- This folder includes .pfd's of litterature relevant to this project.

## ------ SCRIPT USAGE ------
The code should work without any major input from the user. The only exception is if the user wants to run the code chunks that last 1.5+ hours instead of loading the pre-created data. In that case the user needs to uncomment the relevant codechucks and comment out the following "readRDS()" code.

## ------ RESULTS ------
In the age of sail ships had to navigate by the rules of nature. Even though the shortest and most direct routes to wealthy or important areas may seem like the most logical, ships often chose completely different and far longer routes. While still primarily sailing between the nations respective spheres of influence, Although the results of this assignment have been undercut by the lack of north-south currents, a clear tendency to choose efficient routes that follow currents can be observed. Especially the route between Indonesia and Europe, sailed primarily by the Dutch, can be noted for its high efficiency. 
