# Sagebrush Ecosystem Modeling with Hyperspectral Data

This repository tests the ability of hyperspectral data to visualize sagebrush presence and distribution. The completed workflow includes code for an endmember sensitivty analysis and unsupervised endmember extraction. While I could not validate these results against insitu data, the extracted endmembers are compared to isolated spectral signatures for greater sage brush, *Artemsia tridentata*, and cheatgrass, *Bromus tectorum* using Pearson's Correlation Coefficient. All endmembers are visualized with abundance maps, but particular focus is placed on endmembers correlating significantly to the isolated spectral signatures of the focal species. While this workflow focuses on identifiying sagebrush and cheatgrass in a known sagebrush environment at a National Ecological Obervatory Network (NEON) site in Utah (ONAQ), it is adaptable to any other NEON site and focal species/landcover types with known spectral signatures. 
  
This repository is part of a three-part project developed in collaboration with Nature Serve to examine the efficacy of publicly availble remote sensing data to reconstruct sagebrush ecosystems. The three components of this project test the following for their sensitivity to sagebrush ecosystems:

LIDAR Canopy Height Models, workflow developed by users @kessb and @sarahmjaffe and hosted <a href= "https://github.com/kessb/sagebrush-ecosystem-modelinghere" target="blank"> here</a> 
LANDSAT 8 Multispectral, developed by @sarahmjaffe and hosted at her <a href ="https://github.com/sarahmjaffe/sagebrush-ecosystem-modeling-with-landsat8"> Sagebrush Ecosystem Modeling with LANDSAT8 </a> repository. 
NEON's Hyperspectral, developed by @kessb and hosted here. 

This workflow identified spectral signatures with 99% and 90% correlation to sagebrush and cheatgrass, respectively, using unsupervised endmember extraction. The resulting abundance maps indicate the abundance and distrbution of sagebrush and cheatgrass on site. While the results of this workflow can be interpreted alone, they are meant to be compared with @sarahmjaffe's LANDSAT workflow. The use of remote sensing data to model sagebrush ecosystems has not been extensively explored, and, along with visualizing the abundance/distribution of our focal species, we hoped to test the efficacy of different spatial/spectral resolutions. Consequently, these workflows in combination allow the comparison of the 1x1m, 426 bands of NEON data with the 30x30m, 7 bands of LANDSAT data.

Additional code is in progress to 1) subset larger NEON hyperspectral datasets to insitu plot centroids with xarray - in a workflow inspired by Joe McGlinchy's <a href="https://github.com/earthlab/neon-headwall-data" > NEON-headwall-data </a> repository and 2) extract spectral signatures from single pixels. Both approaches offer potential ways to validate data though they are limited by the lack of *insitu* data documentating vegetation coordinates.

# Relevance
Sagebrush ecosystems cover much of the western United States and parts of southwestern Canada. Sagebrush ecosystems provide essential forage and habitat for approximately 350 other species of plants an animals, some of which, like the Greater Sage Grouse, are found only in sagebrush habitat. Sagebrush ecosystems are increasingly fragmented through anthropogenic land use and invasive species, with ranges expected to shift and shrink as warming temperatures force sagebrush populations north. While sagebrush still covers much of the western United States, only 10% of current habitats are considered unaffected by fragmentation. Consequently, many plants and animals associated with sagebrush are losing essential habitat and some qualify as endangered or threatened species per the Endangered Species Act. Conservation efforts targeted to sagebrush ecosystems are costly as they require the surveillance and upkeep of millions of acres of public and private land.

This repository offers an alternative to traditional land monitoring strategies through its unique focus on and analyses of sagebrush ecosystems. 

# Workflow Requirements
## Required Packages
All required packages are included in the repo's environment.yml. To activate the environment and install required packages, fork and clone the repository into the desired local directory and use conda activate nature-serve-env. 

## Data Sources and Formats
This workflow uses data from NEON and USGS Spectral Library. The required data for this workflow are hosted on @kessb and @sarahmjaffe's figshares, and the workflows will download the required data programatically. However, users are welcome to peruse NEON's page for <a href= "https://data.neonscience.org/data-products/DP3.30006.001" target="blank"> Spectrometer Orthorectified Surface Directional Reflection - Mosaic </a> (Hyperspectral) data or search the Spectral Library's <a href="https://crustal.usgs.gov/speclab/AV14.php" target="blank" > Convolved to 2014 specifications of AVIRIS </a>records to substitute in their own desired areas and landcover types. The table below represents all data we retrieved to create our blog (found in the 'presentations' folder).

| PRODUCTS                                                               | File Format  | NEON PAGE             | PURPOSE                         |
|------------------------------------------------------------------------|--------------|-----------------------|---------------------------------|
| NEON Spectrometer Orthorectified Surface Directional Reflection-Mosaic | .hdf5 files  | Data Portal (DP3.30006.001)   | Aerial Hyperspectral Tile for Endmember Extraction          |
| USGS Spectral Library                                                  | .txt files   | Convolved to 2014 Specifications of AVIRIS  | Wavelength and Resolution (Reflectance) Values to Create Spectral Signatures for Endmember Validation |

## Functions
The functions for these workflow have been adapted from NEON's tutorial for <a href= "https://www.neonscience.org/classification-endmember-python" target="blank"> Unsupervised Endmember Extraction</a> and are saved in the neon_helper_functions.py. They are imported with the library imports in the workflow and help open and clean the .hdf5 hyperspectral files.

## Layout and Run Instructions
This repo is divided into two directories: scripts and presentations. The presentation folder includes a copy of my abridged results in both .html and .ipynb format. The unabridged workflows for the endmember sensistivity analysis and NEON hyperspectral tile endmember extraction are in the scripts directory with a .py file containing required helper functions. An additional directory, test_scripts, is also located in the scripts folder and contains code currently under development. To run these workflows, the environment.yml must be forked, cloned, and activated. Once the requisite libraries are available, the scripts directory can be run to download, process, and analyze data. Once the data is downloaded, the contents of the presentation directory can be run - though these are best suited for viewing rather than analyses.
