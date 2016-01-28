######CSR / Conflict Urbanism Aleppo 
##Tutorial 3: Creating a Basic Map

In this tutorial, you will be making a basic map of Aleppo, Syria through the use of *Open Source* GIS software, [QGIS](http://www.qgis.org/en/site/). You will download *Country level* Geographic Open Data from [Humanitarian Response](https://www.humanitarianresponse.info/) and [Humanitarian Data Exchange](https://data.hdx.rwlabs.org/). Next, you will bring in  *Neighborhood Level Data* of Aleppo from the [CSR](http://www.c4sr.columbia.edu/) Data Repository, along with *Street Level Data* from [OpenStreetMap](http://www.openstreetmap.org). You will then design a *Map* with Legend and Scale and Export it as a PDF. Optionally, you can stylize it, in [Adobe Illustrator](http://www.adobe.com/products/illustrator.html). 

### Tools:
For this tutorial, we will be using the following tools:
* [QGIS](http://www.qgis.org/en/site/)
* [Adobe Illustrator](http://www.adobe.com/products/illustrator.html)

### Datasets:
For this tutorial, we will be using the following datasets:
* Aleppo.zip, Download [here](/Tutorials/Tutorial3/Data/Aleppo.zip)
* Aleppo_Dem.zip, Download [here](/Tutorials/Tutorial3/Data/AleppoDem.zip)
* Neighborhood.zip, Download [here](/Tutorials/Tutorial3/Data/Neighborhood.zip)
  
### Datasets Overview:
This section provides detailed explanation of each data source. You can skip this section, if you would like to continue with the tutorial. However, it is recommended that you familiarize yourself with these sources, as they will asssist you in your research.

##### Country Level Data:
*Country Level Data* used to be provided by [Humanitarian Response](https://www.humanitarianresponse.info/en/applications/data); a respository maintained by UN OCHA to support humanitarian operations globally. The **Common Operational Datasets (CODs)** are critical datasets that are used to support the work of humanitarian actors across multiple sectors. They are considered a de facto standard for the humanitarian community and should represent the best-available datasets for each theme. The **Fundamental Operational Datasets (FODs)** are datasets that are relevent to a humanitarian operation, but are more specific to a particular sector or otherwise do not fit into one of the seven COD themes.</br>

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12637883/b46b94ce-c566-11e5-815b-a84ea83369fa.png)
Note: In order to note the availability of Country Level Data, it is recommended to get an overview from the Humanitarian Response website. You can follow the links for each individual download. Alternatively, you can shift to HDX website. 

**Humanitarian Data Exchange**, [HDX](https://data.hdx.rwlabs.org) is a good place for open data as it presents a *consolidated repository* of data collected through multiple sources. The goal of the Humanitarian Data Exchange (HDX) is to make humanitarian data easy to find and use for analysis. If you are interested in exploring datasets from multiple Humanitarian Agencies, it is recommended that you register yourself on the HDX website. You can select regions and organisations of interest and explore the vast collection of datasets. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12638623/b49177e2-c56c-11e5-9dca-7885710c4bc9.png)
Note: The Country Overview provides visualization of key datasets along with a list of browsable sources. As of Jan 2016, there are 174 datasets for Syria. 

We will be using the following files from HDX:
* Syria: Administrative Boundaries
  * SYR_UNCS-OCHA_20130519_SHP_UTF8.ZIP
  * Oringinally Downloaded [here](https://data.hdx.rwlabs.org/dataset/syrian-arab-republic-administrative-boundaries-populated-places)
* Syria: Waterways
  * WATERWAYS_LINE_OSM.ZIP
  * Oringinally Downloaded [here](https://data.hdx.rwlabs.org/dataset/syrian-arab-republic-water-bodies)
* Syria: Elevation Model
  * SYR_ASTER_DEM.TIF.ZIP
  * Oringinally Downloaded [here](https://data.hdx.rwlabs.org/dataset/syrian-arab-republic-elevation-model)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12638628/bfa62092-c56c-11e5-8b71-05effc48373c.png)
HDX provides additional information on each data source including *layers*, *data source* and *contributor*. It often provides data in *multiple formats*. For our purpose, we will download the shape files. If you prefer to work in [ArcGIS](https://www.arcgis.com), you are welcome to download the geo database (.gdb file). 

##### Neighborhood Level Data:
*Neighborhood Level Data* is a dataset prepared by CSR. It uses the Neighborhood Map published in the [Aleppo City Profile Report](http://unhabitat.org/city-profile-aleppo-multi-sector-assessment/), pg.24 published by UN-Habitat in May 2014. We digitized the map based on Google Earth satellite imagery, and added Arabic tranlations for the neighborhood names. In a case, where a neighborhood was divided in parts, we've used roman numerals. A neighborhood map was also developed by [UNITAR/UNOSAT](http://www.unitar.org/unosat/), in early 2015, which slightly varies from the one initially produced by [UN Habitat](http://unhabitat.org/).  

### Creating a Basic Map of Aleppo:

##### Steps:
  * 01. QGIS: Installation and Introduction
  * 02. QGIS: Setting Up Project with Data
  * 03. QGIS: Analyzing and Styling Data
  * 04. QGIS: Setting Up Print Composer
  * 05. AI: Styling and Editing Map SVG

##### 01. QGIS: Installation and Introduction
**Installtion**: 
QGIS is a user friendly Open Source Geographic Information System (GIS) licensed under the GNU General Public License. It is an official project of the Open Source Geospatial Foundation (OSGeo). It runs on Linux, Unix, Mac OSX, Windows and Android and supports numerous vector, raster, and database formats and functionalities. 
Please Download QGIS [here](https://www.qgis.org/en/site/forusers/download.html). You can access documentation [here](http://www.qgis.org/en/docs/index.html).

**Introduction**:
When QGIS starts, you are presented with the GUI as shown in the figure below. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12638635/cfd7830c-c56c-11e5-9eea-ab1ff987107d.png)

**1: Menu Bar**: The menu bar provides access to various QGIS features using a standard hierarchical menu.
**1: Menu Bar**:
**1: Menu Bar**:
**1: Menu Bar**:

##### 02. QGIS: Setting Up Project with Data

##### 03. QGIS: Analyzing and Styling Data

##### 04. QGIS: Setting Up Print Composer

##### 05. AI: Styling and Editing Map SVG 

##### 06. WEB: Embed Map in Case Study

