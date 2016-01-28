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

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12638628/bfa62092-c56c-11e5-8b71-05effc48373c.png)
HDX provides additional information on each data source including *layers*, *data source* and *contributor*. It often provides data in *multiple formats*. For our purpose, we will download the shape files. If you prefer to work in [ArcGIS](https://www.arcgis.com), you are welcome to download the geo database (`.gdb file`). 

##### Neighborhood Level Data:
*Neighborhood Level Data* is a dataset prepared by CSR. It uses the Neighborhood Map published in the [Aleppo City Profile Report](http://unhabitat.org/city-profile-aleppo-multi-sector-assessment/), pg.24 published by UN-Habitat, in May 2014. We digitized the map based on Google Earth satellite imagery, and added Arabic tranlations for the neighborhood names. In a case, where a neighborhood was divided in parts, we've used roman numerals. A neighborhood map was also developed by [UNITAR/UNOSAT](http://www.unitar.org/unosat/), in early 2015, which slightly varies from the one initially produced by [UN Habitat](http://unhabitat.org/).  

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
When **QGIS** starts, you are presented with the GUI as shown in the figure below. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12638635/cfd7830c-c56c-11e5-9eea-ab1ff987107d.png)

**1: Menu Bar**: 
The `Menu Bar` provides access to various QGIS features using a standard hierarchical menu.

**2: Tool Bar**: 
The `Toolbar` provides access to the menus, plus additional tools and plugins for interacting with the map. `Right-Click` on the toolbar to *Add / Remove* functions.

**3: Layer Panel**:
The `Layer Panel` lists all the layers in the project. The `checkbox` in each legend entry can be used to show or hide the layer. A `layer` can be selected and dragged up or down in the legend to change the Z-ordering which is the hierarchy in which the layers are visualized in the map view.

**4: Map View**:
The `Map View` displayed in this window will depend on the *vector* and *raster* layers you have chosen to load. The map view can be panned, shifting the focus of the map display to another region, and it can be zoomed in and out. 

**5: Status Bar**:
The `Status Bar` shows you your current position in `Map Coordinates`, along with the `Scale` and the `Project Projection`. You can read more about *Projections* [here](https://docs.qgis.org/2.2/en/docs/user_manual/working_with_projections/working_with_projections.html). 

##### 02. QGIS: Setting Up Project with Data
**Adding Files**: 
* A *shapefile* is actually made up of 5 or 6 individual files with different extensions.
  * .shp - The main file that stores the feature geometry (required)
  * .shx - The index file that stores the index of the feature geometry (required)
  * .dbf - The dBASE table that stores the attribute information of features (required)
  * .sbn and .sbx - The files that store the spatial index of features.
  * .prj - The file that stores the coordinate system information.

* To add *shapefiles* go to `Menu > Layer > Add Vector Layer > New Shapefile Layer`and add `filename.shp` 

* After adding all the *shapefiles*, please organize them in the following order in the Layers Panel. Please note that layers are *hierarchical* and drawn based on their position in the `layers panel`. 
  * Aleppo_Neighborhood
  * Waterways_line_OSM.shp
  * syr_admin4_point.shp
  * syr_admin3.shp
  * syr_admin2.shp
  * syr_admin1.shp
  * syr_admin4_point.shp

* **Plug In: OpenLayers**
QGIS allows you to bring data directly from OpenStreetMaps and other satellite data as an underlay. In order to access Imagery within the QGIS Environment, please add the following Plugin.  [OpenLayers](https://plugins.qgis.org/plugins/openlayers_plugin/). To add a plugin, please go to `Menu > Plugins > Manage` and Install Plugins. More documentation on installing and managing plugins can be found [here](http://docs.qgis.org/2.0/ca/docs/training_manual/qgis_plugins/fetching_plugins.html). Once the PlugIn is added it can be accessed through `Menu > Vector > OpenStreetMap`. This is a good way to add an underlay satellite image or OSM data. This tool is also helpful in *Georeferencing Data*.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12649824/3031639e-c5ae-11e5-8946-3229aac86df3.png)

* **Plug In: OpenStreetMap**
QGIS allows you to bring geometry data directly from OpenStreetMaps into your QGIS Environment. In order to do so, please download the [OpenStreetMap plugin](http://wiki.openstreetmap.org/wiki/QGIS_OSM_Plugin), from the method shown above. You can also go to the [OpenSteetMap](https://www.openstreetmap.org/#map=12/36.1961/37.1692) and download data through the *Export* toolbar. You can import the `filename.osm` directly into QGIS. Note: If your download fails, it is because the area selected is larger than can be processed.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12656141/9d8ec780-c5ca-11e5-8c9e-5fbbafda01f2.png)

You can set Aleppo to the extent required in the map window. In options select: `From Map Canvas` and add a *filename* for `output`. Depending on the `tags` in the region, you will be getting point, line and polygon data as *separate layers*. Select all for now as you can switch off and remove unwanted layers later.

##### 03. QGIS: Analyzing and Styling Data
**Styling Data**
* **Attributes Table** 
  `Right click - Open Attributes Table`to access attributes table, which maintains the data in each file.

Layer Projection Stuff
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12649828/3040c7d0-c5ae-11e5-88ae-a5e4fc4b9c1e.png)


* **Properties**
  `Right click - Properties`to access properties tab. 
    * General: Use to review or change layer Projection 
    * Style: Use to Stylize each Layer's Content
    * Label: Use to add a particular field as a label
  
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12649825/30326c44-c5ae-11e5-9abd-225124784c81.png)

##### 04. QGIS: Setting Up Print Composer
First, before creating a `Print Composer` check to see you are working in the right projection. Porjections will be discussed further in the coming weeks, but basically map projections are ways of transforming locations on a sphere (the Earth) to locations on a plane (a 2D map). There are many types of projections and each one of them has a specific purpose and a specific area of relevance.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12649826/303321f2-c5ae-11e5-9151-70c5a92c9aa1.png)

The `Print Composer` is where you will format your map for its final output. Here you will specify the output size, you will add a legend, a scale bar, a north arrow (if needed) and any additional text (titles, sources, explanations and credits). Although the `Print Composer` exists as its own window it will still be linked to the map `Project` we have been working on.
* First, create a new `Print Composer` in `Project` `New Print Composer`.
* Give it a name if you want, although this is not necessary.
* Once you are in the `Print Composer` you need to add a new map. Think of it as if you had a blank piece of paper and you were adding a window onto the map you've been working on. That window is a link to your `Project` and if you change things in the `Project` those changes will still be reflected in the `Print Composer`.
* To add a new map, click on the button `Add new map` on the left-hand panel and draw a rectangle on the blank page.
* Once you add the map you can adjust its size and position by dragging it from its corners.
* You might notice that if you change the size of the map it doesn't necessarily update. To avoid this, on the right-hand panel, where it says `Main properties`, click on `Update preview`. Or, you can also click on the drop-down menu where it says `Cache` and change it to `Render` so that it is constantly updating.

##### 05. AI: Styling and Editing Map SVG 
The last step is to export the map as a PDF file. Use the `Export as PDF` button on the top toolbar and save your final map.


##### 06. WEB: Embed Map in Case Study
You will now embed the `Map_of_Syria.pdf` as a link in the Case Study. The map opens in a separate window, for which the dimensions are passed within the argument. 

```html
<a href="Map_of_Syria.pdf" target="popup" onclick="window.open('Map1.pdf', 'About', 'width=1200,height=800'); return false;"> <h4> Map Of Syria </h4></a>
```
Next, you will embed the `Map_of_Aleppo.pdf` as an image in the Case Study.  

```html
<IMG SRC="Map_of_Aleppo.png" ALT="Map of Aleppo" WIDTH=800 HEIGHT=800>
```

### Deliverable: 
Kindly update you link with the `Map_of_Syria.pdf`as a link and `Map_of_Aleppo.pdf` and an embedded image in the case study.
