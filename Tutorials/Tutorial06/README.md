######CSR / Conflict Urbanism Aleppo 
##Tutorial 6: Designing a Simple Cluster Map

In this tutorial, you will be using, UNOSAT's Damage Analysis, *open data*, from the [Humanitarian Data Exchange] website, to design an Interactive Cluster Map, using Web tools, Mapbox and the Open Source Library Leaflet. You will use the .shp file provided by UNOSAT of damage locations marked and edit and export it as a .js file. You will then use *open source* library leaflet and its built in *cluster* function to design the interactive map. Lastly, you will edit the css, to change the look of the clusters. 

### Tools:
For this tutorial, we will be using the following tools:
* [QGIS](http://www.qgis.org/en/site/)
* [Sublime](http://www.sublimetext.com/)
* [Chrome](https://www.google.com/chrome/)


### Datasets:
For this tutorial, we will be using the following datasets:
* UNOSAT.zip, Download [here](https://www.dropbox.com/s/3dha98zai4wtcxg/UNOSAT.zip?dl=0)
* Tutorial6.zip, Download [here](https://www.dropbox.com/s/26yw21u74axmp9u/Tutorial6.zip?dl=0)

  
### Datasets Overview:
This section provides detailed explanation of the data source. You can skip this section, if you would like to continue with the tutorial. However, it is recommended that you familiarize yourself with these sources, as they will asssist you in your research.

##### Data set 1:

**Humanitarian Data Exchange**, [HDX](https://data.hdx.rwlabs.org) is a good place for open data as it presents a *consolidated repository* of data collected through multiple sources. The goal of the Humanitarian Data Exchange (HDX) is to make humanitarian data easy to find and use for analysis. If you are interested in exploring datasets from multiple Humanitarian Agencies, it is recommended that you register yourself on the HDX website. You can select regions and organisations of interest and explore the vast collection of datasets. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027498/786cd4b2-d252-11e5-90bc-74a7e2824e24.png)

You can search for *UNOSAT - UNITAR Aleppo - Damage assesment Aleppo*. Make sure you use the most recent file. (As of now, that is Data for May 2015). 

We will be using the following files from HDX:
* UNOSAT_DamageAssesment_OFDA-REACH_CE20130604SYR_shp.zip

*Geodata of Damage Assessment of Aleppo, Aleppo Governorate, Syria*
This map illustrates satellite-detected damage in a portion of the city of Aleppo, Syrian Arab Republic. Using satellite imagery acquired 01 May 2015, 26 April 2015, 23 May 2014, 23 September 2013, and 21 November 2010, UNITAR - UNOSAT identified a total of 5,170 affected structures within the extent of this map. Approximately 904 of these were destroyed, 2,641 severely damaged, and 1,625 moderately damaged. The city-wide analysis of Aleppo revealed a total of 14,034 affected structures, of which 2,878 were destroyed, 6,879 severely damaged, and 4,277 moderately damaged. While much of the city was damaged by 23 May 2014, 5,567 structures were newly damaged and 90 structures experienced an increase in damage between that date and 01 May 2015. This analysis was done of the REACH initiative for the U.S. Office of Foreign Disaster Assistance. This is a preliminary analysis and has not yet been validated in the field. Please send ground feedback to UNITAR - UNOSAT.

HDX provides additional information on each data source including *layers*, *data source* and *contributor*. It often provides data in *multiple formats*. For our purpose, we will download the shape files. If you prefer to work in [ArcGIS](https://www.arcgis.com), you are welcome to download the geo database (`.gdb file`). 

Likewise, UNITAR/UNOSAT maintains a good repository on their site and frequently updates the data that can be accessed [here](http://www.unitar.org/unosat). The data is all made available on HDX, which is likely where you will download from, but you can always check UNITARs site to see if they have an update. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027499/789fa28e-d252-11e5-92a6-55b09bc50e06.png)

You can also look at the static map to see how UNOSAT visualizes it.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027500/78ae924e-d252-11e5-8687-5685521a701f.png)

### Tutorial Title: Designing a Simple Cluster Map

##### Steps:
  * 01. QGIS: Explore UNOSAT dataset
  * 02. WEB: Export dataset .js format
  * 03. WEB: Design UNOSAT Cluster Map
  * 04. WEB: Change Clusters Appearance 
  * 05. WEB: Embed Map in your Case Study 

##### 01. QGIS: Explore UNOSAT dataset

First, bring your `.shp` files into QGIS. To do this, Go to `Menu > Layer > Add Layer > Add Vector Layer` and browse to the .zip file you downloaded. Then holding onto the `Shift` key, select the layers you want to Add. If you select all or bring layers that you require, just remove them form the layer panel, by Layer > Right Click > Remove. Just keep the 2 layers below. Note: Make sure you have the correct Dataset and the shape file is `2015`.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027502/863814a8-d252-11e5-9976-7fda757b07fd.png)

You will add:
*	CityBorder
*	Damage_sites_Update3_Aleppo_2015...

Uncheck the `City Border` file and `zoom to layer`, for the Damage Sites data. Open attributes table, by `Right-Click` and examine the fields in the dataset. You will see the following fields: 
*	SiteID
*	SensorDate
*	SensorID
*	Confidence
*	MainDamage
*	SensorDa_1
*	SensorID_2
*	Confiden_1
*	Main_Dam_1
*	Damage_Sta
*	SensorDa_2
*	SensorID_3
*	Confiden_2
*	Main_Dam_2
*	Damage_S_1
*	Grouped_Da
*	FieldValid
*	Notes
*	Settlement
*	Neighborhood
*	EventCode

Now `duplicate` your layer in Layers Panel and Go To attributes table again. This way you make sure you don't end up editing your main dataset. For the Cluster map, we just want to `Clusterize` the events. In this easy example, we will not be adding pop-ups and descriptions of each event. The `Clusters` will disaggregate into marked damaged points. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027505/8b1f5350-d252-11e5-9fce-f2dd3723324a.png)

We do not need all these fields in our visualization and to make our files simple and faster, it is recommended that you remove all unwanted data fields. In your attributes table, Go to the Third Last button from right Delete Column. In the pop up window select the unrequired fields and hit OK.  We will keep only the following: 

*	SiteID

It takes a while to process after which you have a file with a single column. If your system hangs, you can also delete columns at a time.

Our attribute table now has each event as a point with no associated information. In order to save the X-Y coordinate information in our attribute table, Go To `Menu > Vector > Geometry Tools > Export / Add Geometry Tables`. Then select your input data layer and `Save` as a new `shape file`. Check `Add` result to `Canvas` option. NO w you should see the X-Y Coordinate Columns added to your data. If you are seeing more columns in your attributes table, it is ok. As menioned earlier, you should try to delete as many as possible. But as long as you have these 3, you can proceed.

*	SiteID
*	XCOORD
*	YCOORD

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027507/8fced114-d252-11e5-97ad-8135e0a65d99.png) 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027506/8fcb2082-d252-11e5-91d2-005bad76d59e.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027508/8fee2474-d252-11e5-8b0d-6293b04d8ca4.png)

##### 02. WEB: Export dataset .js format

For this tutorial we are using an `open source` Javascript library called `leaflet`. You can access more details about it [here](http://leafletjs.com). It is a useful visualization library and provides many great functions that can be called in your code, through their API. 

*Leaflet:*
Leaflet is the leading open-source JavaScript library for mobile-friendly interactive maps. Weighing just about 33 KB of JS, it has all the mapping features most developers ever need. Leaflet is designed with simplicity, performance and usability in mind. It works efficiently across all major desktop and mobile platforms, can be extended with lots of plugins, has a beautiful, easy to use and well-documented API and a simple, readable source code that is a joy to contribute to. For more information on *clusterig*, you cna look [here](https://github.com/Leaflet/Leaflet.markercluster). 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027504/8b1e5536-d252-11e5-946f-6bfa3e0110d9.png)

To use with ClusterAPI, we need our data in Javascript format. To do this, Right Click on your Layer and Save As. Save your file in geoJSON format and make sure the Projection is set to EPSG:4326. You can check your saved layer in QGIS, to make sure the data appears the same. Now Close QGIS. 

Drag and Drop your Uno1.geojson file into *sublime editor*. On the right corner in sublime, select Javascript from drop down menu. You will see the color formatting change. Now, carefully follow the next step. In this file, you want to equate this data to a variable called uno1. To do so, you need to add the following on the first and last line of your code. Do not change anything else. 

First Line:
> First line: `var uno1 = `

Last Line:
> Last line: `;`

This is how the start and end of your file look like:

```javascript
{
"type": "FeatureCollection",
"crs": { "type": "name", "properties": { "name": "urn:ogc:def:crs:OGC:1.3:CRS84" } },
                                                                                
"features": [
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "2", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "2", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157763, "YCOORD": 36.203296 }, "geometry": { "type": "Point", "coordinates": [ 37.157763310000064, 36.203296022000075 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "2", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "2", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157559, "YCOORD": 36.203340 }, "geometry": { "type": "Point", "coordinates": [ 37.157559387000049, 36.203340185000059 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "2", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "2", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157484, "YCOORD": 36.203344 }, "geometry": { "type": "Point", "coordinates": [ 37.157484268000076, 36.203343533000066 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "1", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "1", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157663, "YCOORD": 36.203306 }, "geometry": { "type": "Point", "coordinates": [ 37.157663028000059, 36.203305740000076 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "1", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "1", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157566, "YCOORD": 36.202351 }, "geometry": { "type": "Point", "coordinates": [ 37.157565891000047, 36.202351430000078 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "1", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "1", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157418, "YCOORD": 36.202383 }, "geometry": { "type": "Point", "coordinates": [ 37.157417852000037, 36.202382938000085 ] } },
.
.
.
.
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": null, "SensorID_2": null, "Confiden_1": null, "Main_Dam_1": null, "Damage_Sta": null, "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "2", "Main_Dam_2": "1", "Damage_S_1": "3", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Villat Dahiyat al Asad", "EventCode": "CE20130604SYR", "XCOORD": 37.078120, "YCOORD": 36.177461 }, "geometry": { "type": "Point", "coordinates": [ 37.078120323000064, 36.177460598000039 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": null, "SensorID_2": null, "Confiden_1": null, "Main_Dam_1": null, "Damage_Sta": null, "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "2", "Main_Dam_2": "1", "Damage_S_1": "3", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Villat Dahiyat al Asad", "EventCode": "CE20130604SYR", "XCOORD": 37.081233, "YCOORD": 36.173247 }, "geometry": { "type": "Point", "coordinates": [ 37.081232894000038, 36.173247463000052 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": null, "SensorID_2": null, "Confiden_1": null, "Main_Dam_1": null, "Damage_Sta": null, "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "2", "Main_Dam_2": "1", "Damage_S_1": "3", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Villat Dahiyat al Asad", "EventCode": "CE20130604SYR", "XCOORD": 37.076590, "YCOORD": 36.173104 }, "geometry": { "type": "Point", "coordinates": [ 37.076590309000039, 36.17310371800005 ] } }
]
}
```

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027513/9be8a0d8-d252-11e5-8ded-cc5d81f398ed.png)

```javascript
var uno1 = {
"type": "FeatureCollection",
"crs": { "type": "name", "properties": { "name": "urn:ogc:def:crs:OGC:1.3:CRS84" } },
                                                                                
"features": [
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "2", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "2", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157763, "YCOORD": 36.203296 }, "geometry": { "type": "Point", "coordinates": [ 37.157763310000064, 36.203296022000075 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "2", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "2", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157559, "YCOORD": 36.203340 }, "geometry": { "type": "Point", "coordinates": [ 37.157559387000049, 36.203340185000059 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "2", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "2", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157484, "YCOORD": 36.203344 }, "geometry": { "type": "Point", "coordinates": [ 37.157484268000076, 36.203343533000066 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "1", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "1", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157663, "YCOORD": 36.203306 }, "geometry": { "type": "Point", "coordinates": [ 37.157663028000059, 36.203305740000076 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "1", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "1", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157566, "YCOORD": 36.202351 }, "geometry": { "type": "Point", "coordinates": [ 37.157565891000047, 36.202351430000078 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": "2014\/05\/23", "SensorID_2": "Worldview-2", "Confiden_1": "1", "Main_Dam_1": "1", "Damage_Sta": "New - damage", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "1", "Main_Dam_2": "1", "Damage_S_1": "0", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Farafira", "EventCode": "CE20130604SYR", "XCOORD": 37.157418, "YCOORD": 36.202383 }, "geometry": { "type": "Point", "coordinates": [ 37.157417852000037, 36.202382938000085 ] } },
.
.
.
.
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": null, "SensorID_2": null, "Confiden_1": null, "Main_Dam_1": null, "Damage_Sta": null, "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "2", "Main_Dam_2": "1", "Damage_S_1": "3", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Villat Dahiyat al Asad", "EventCode": "CE20130604SYR", "XCOORD": 37.078120, "YCOORD": 36.177461 }, "geometry": { "type": "Point", "coordinates": [ 37.078120323000064, 36.177460598000039 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": null, "SensorID_2": null, "Confiden_1": null, "Main_Dam_1": null, "Damage_Sta": null, "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "2", "Main_Dam_2": "1", "Damage_S_1": "3", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Villat Dahiyat al Asad", "EventCode": "CE20130604SYR", "XCOORD": 37.081233, "YCOORD": 36.173247 }, "geometry": { "type": "Point", "coordinates": [ 37.081232894000038, 36.173247463000052 ] } },
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDate": null, "SensorID": null, "Confidence": null, "Main_Damag": null, "SensorDa_1": null, "SensorID_2": null, "Confiden_1": null, "Main_Dam_1": null, "Damage_Sta": null, "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Confiden_2": "2", "Main_Dam_2": "1", "Damage_S_1": "3", "Grouped_Da": "Damaged Buildings", "FieldValid": "Not yet field validated", "Notes": null, "Settlement": "Aleppo", "Neighborho": "Villat Dahiyat al Asad", "EventCode": "CE20130604SYR", "XCOORD": 37.076590, "YCOORD": 36.173104 }, "geometry": { "type": "Point", "coordinates": [ 37.076590309000039, 36.17310371800005 ] } }
]
};
```

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027514/ab1d2196-d252-11e5-9b92-042da80e1f60.png)

Now save your file as `uno1.js`

##### 03. WEB: Design UNOSAT Cluster Map 

For this section of the tutorial, we have provided the `.html` file that you will need to use with your data. You can choose to copy/paste from here or the downloads file. Open Cluster.zip and download the following. 

``` html
<!-- Conflict Urbanism: Aleppo
     Center for Spatial Research
     Madeeha Merchant (mym2107@columbia.edu)

================================================================= -->
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />

<!-- ADD: Name to Appear on Tab --> 
<title>UNOSAT - Cluster</title>

<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
<script src='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.js'></script>
<link href='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.css' rel='stylesheet' />
<style>
  body { margin:0; padding:0; }
  #map { position:absolute; top:0; bottom:0; width:100%; }
</style>
</head>
<body>

<script src="../dist/leaflet.markercluster-src.js"></script>
<script src='https://api.mapbox.com/mapbox.js/plugins/leaflet-markercluster/v0.4.0/leaflet.markercluster.js'></script>
<link href='https://api.mapbox.com/mapbox.js/plugins/leaflet-markercluster/v0.4.0/MarkerCluster.css' rel='stylesheet' />
<link href='https://api.mapbox.com/mapbox.js/plugins/leaflet-markercluster/v0.4.0/MarkerCluster.Default.css' rel='stylesheet' />
<div id='map'></div>

<!-- ADD: Link to the file filename.js -->
<script src="uno1.js"></script>
<script>

//ADD: Access Token from your Mapbox Account 
L.mapbox.accessToken = 'pk.eyJ1IjoiY3N0b2FmZXIiLCJhIjoiY2lnNnRwN3hpMDF4YnU3a3BkNjAzcnBvaCJ9.0EZvAi2Bvn1zGdLj6crPsA';
// Here we don't use the second argument to map, since that would automatically
// load in non-clustered markers from the layer. Instead we add just the backing tileLayer, and then use the featureLayer only for its data.

// ADD: Long, Lat and Zoom Level. The settings below zoom at Aleppo
        var lat = 36.21; // Set World
        var lng = 37.15; // Set Worl
        var zoom =  13; // Zoom Out

        var markerPopup = false,
        allLayers = [];

        var map = L.map('map', {
            zoomControl: true
        }).setView([lat, lng], zoom);

// Since featureLayer is an asynchronous method, we use the `.on('ready'`
// call to only use its marker data once we know it is actually loaded.
        var markers = new L.MarkerClusterGroup();

// 'unosat is the variable you used in your javascript file. You can change this, if you changed it there'
        var geojson = L.geoJson(uno1, {
            pointToLayer: function (feature, latlng) {
                var myIcon = L.icon({
                    // The icon files are in the same folder. You could change them and re-use here as per your requirement.
                    iconUrl: 'icon1.png',
                    iconRetinaUrl: 'icon1_2x.png',
                    // Here, change the size of the icon 
                    iconSize: [10, 10],
                    iconAnchor: [16, 16],
                    popupAnchor: [15, 32],
                });
                return L.marker(latlng, { icon: myIcon });
            }
        });
        markers.addLayer(geojson);
        //markers.addTo(map);
        L.control.layers({
        // ADD: Satellite Layer of Mapbox or any other generic mapbox Layer
       'Satellite Imagery': L.mapbox.tileLayer('mapbox.satellite').addTo(map)
        }, {
        // ADD: Feature Layer for your Data   
        'UNOSAT Data': markers,
        }).addTo(map);

</script>
</body>
</html>

```
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027515/b7bb594a-d252-11e5-85cd-883ed8e777c8.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027520/bdf97de6-d252-11e5-80bb-b68abbcac678.png)

In the above code, remember to do the following:

You need to allow your html file to link to read the .js file. 
``` 
line 31 : <script src="uno1.js"></script>
```

You need to set your variable name here.
```
line 56: var geojson = L.geoJson(uno1, {
```

If required you can then change icon settings:
``` html                
var myIcon = L.icon({
                    // The icon files are in the same folder. You could change them and re-use here as per your requirement.
                    iconUrl: 'icon1.png',
                    iconRetinaUrl: 'icon1_2x.png',
                    // Here, change the size of the icon 
                    iconSize: [10, 10],
                    iconAnchor: [16, 16],
                    popupAnchor: [15, 32],

``` 

You can also add `multiple layers` to your map and slect the names under which it should appear.

``` html  
        L.control.layers({
        // ADD: Satellite Layer of Mapbox or any other generic mapbox Layer
       'Satellite Imagery': L.mapbox.tileLayer('mapbox.satellite').addTo(map)
        }, {
        // ADD: Feature Layer for your Data: Use the Title as you would like it to appear in the Drop Menu   
        'UNOSAT Data': markers,
        }).addTo(map);
``` 

For instance, if you also wanted to add the `High-Contrast layer`, change the code to the following:

``` html  
        L.control.layers({
        // ADD: Satellite Layer of Mapbox or any other generic mapbox Layer
       'Satellite Imagery': L.mapbox.tileLayer('mapbox.satellite').addTo(map),
       // Add a second Layer: 
       'OpenStreetMap': L.mapbox.tileLayer('mapbox.high-contrast)
        }, {
        // ADD: Feature Layer for your Data: Use the Title as you would like it to appear in the Drop Menu   
        'UNOSAT Data': markers,
        }).addTo(map);
``` 

Note the `,` added at the end of the satellite layer. You can add as many layers as you would like, just careful with the `,`. Every entry excep the last will need one.

Now save both your files in the folder `clusterMap`. You can `Right click` and test your files in Chrome. Yous should be able to see the below map. Then from the layers window on the right, you can click UNOSAT Data and the clusters should appear. Note that based on amount, you have 3 tiers of clusters, shaded by color range. Also note, the black dots, which are the icons that you set in your file.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027531/21cf8e5a-d253-11e5-89f8-5b9933fbd6f8.jpg)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027532/21e080f2-d253-11e5-9b37-067ce0af4d52.jpg)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027530/21b19968-d253-11e5-8057-1df3ee39aba4.jpg)

Feel free, to add additional options, through the ClusterMaps API. 


##### 04. WEB: Change Clusters Appearance  

You can keep the map this way if you like, but in this section we explore different options for further styling your map. There are mainly 2 features that you might want to stylize. 

*	Cluster Appearance
*	Icon Appearance

**Cluster Appearance**

You have 2 .css files that you link your html files to, in the code. If you want to change the default appearance, you will have to download these files and link your code to that. You can do this in the following steps.

* Add `Cluster.default.css` and `cluster.css` to your folder
* Now go to `Line 27` of you html code and change the links for the cluster files. 

You will remove:
```  
<link href='https://api.mapbox.com/mapbox.js/plugins/leaflet-markercluster/v0.4.0/MarkerCluster.css' rel='stylesheet' />
<link href='https://api.mapbox.com/mapbox.js/plugins/leaflet-markercluster/v0.4.0/MarkerCluster.Default.css' rel='stylesheet' />
``` 

You will add:
``` 
<link href='cluster.css' rel='stylesheet' />
<link href='cluster.default.css' rel='stylesheet' />    
``` 

Now, you can manually change the code in the .css files and it will reflect in your browser. 
Open ` cluster.default.css`  and look a the code.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027534/2a637ef0-d253-11e5-981d-c64420536f75.png)

Here, you can change the colors with `(R,G,B,A)` values, where `A = Opacity Value`

``` CSS
.marker-cluster-small {
	/*background-color: rgba(181, 226, 140, 0.6); light green */
	background-color: rgba(132, 132, 132, 0.4);
	}
.marker-cluster-small div {
	/*background-color: rgba(110, 204, 57, 0.6);  bright green */
	background-color: rgba(192, 225, 226, 0.8); 
	}

.marker-cluster-medium {
	/*background-color: rgba(241, 211, 87, 0.6); light orange */
	background-color: rgba(132, 132, 132, 0.4);
	}
.marker-cluster-medium div {
	/* background-color: rgba(240, 194, 12, 0.6); bright ornage */
	background-color: rgba(159, 221, 221, 0.8);
	}

.marker-cluster-large {
	/*background-color: rgba(255, 255, 255, 1); light yellow */
	background-color: rgba(132, 132, 132, 0.4);
	}
.marker-cluster-large div {
	/*background-color: rgba(0, 255, 0, 0.6);  bright green */
	background-color: rgba(102, 196, 188, 0.8);
	}
```
Here's what your map will look if you updated as per the numbers above. Please feel free to change as you would like.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027533/2a5c5bac-d253-11e5-8d81-276ac21be6fd.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027536/38476324-d253-11e5-86fd-4f929a826515.jpg)

**Icon Appearance**
The icon files, one for retina display and one for regular display are included in your folder. You can also make your own pngs and save using the `illustrator template` in the folder. Your icons can be any shape and color. The size can be changed in the code itself, as shown earlier. Save the file as you would like using the same *naming conventions*. For ease, I have added 2 optional icons for use, if you would like to test.


##### 05. WEB: Embed Map in your Case Study 

Using the code, provide in [tutorial2](), you can embed any interactive website, in your case study. Test `width` and `height` ratios, to see what works best for you. Note: You will need to upload your site in order to embed it. You could test it using a locally saved .html file. If you save it in the same folder as the casestudy, just  use *filename.html*. Furthermore, it can be tricky to have this working within your case study. 


```html
<iframe width='100%' height='500px' frameBorder='0' src= "filename.html" name="iframe_x"></iframe> 
<p><a href="filename.html" target="iframe_x">Interactive Site</a></p>
```

Note: As there are multiple files in this folder, please make sure your links are accurate.

### Deliverables:

### Tutorial Checklist
- [x] 01. QGIS: Explore UNOSAT dataset
- [x] 02. WEB: Export dataset .js format
- [x] 03. WEB: Design UNOSAT Cluster Map
- [x] 04. WEB: Change Clusters Appearance 
- [x] 05. WEB: Embed Map in your Case Study 


