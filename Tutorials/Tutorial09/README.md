######CSR / Conflict Urbanism Aleppo 
##Tutorial 9: Designing a Categorized Cluster Map

In this tutorial, you will be using, the UNOSAT's Damage Analysis Sites, from the [Humanitarian Data Exchange](https://data.hdx.rwlabs.org/) website, to design an Interactive *Catergorized* Cluster Map, using Web tools, Mapbox and the Open Source Library Leaflet. You will use the .shp file provided by HIU of identified cultural heritage sites and edit and export it as a JSON file, using QGIS. You will then use *open source* library leaflet an its built in *cluster* function to design the interactive map based on categories. Lastly, you will edit the css, to change the look of the clusters. 


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

![Add Layer](change)
You can search for *UNOSAT - UNITAR Aleppo - Damage assesment Aleppo*. Make sure you use the most recent file. (As of now, that is Data for May 2015). 

We will be using the following files from HDX:
* UNOSAT_DamageAssesment_OFDA-REACH_CE20130604SYR_shp.zip

*Geodata of Damage Assessment of Aleppo, Aleppo Governorate, Syria*
This map illustrates satellite-detected damage in a portion of the city of Aleppo, Syrian Arab Republic. Using satellite imagery acquired 01 May 2015, 26 April 2015, 23 May 2014, 23 September 2013, and 21 November 2010, UNITAR - UNOSAT identified a total of 5,170 affected structures within the extent of this map. Approximately 904 of these were destroyed, 2,641 severely damaged, and 1,625 moderately damaged. The city-wide analysis of Aleppo revealed a total of 14,034 affected structures, of which 2,878 were destroyed, 6,879 severely damaged, and 4,277 moderately damaged. While much of the city was damaged by 23 May 2014, 5,567 structures were newly damaged and 90 structures experienced an increase in damage between that date and 01 May 2015. This analysis was done of the REACH initiative for the U.S. Office of Foreign Disaster Assistance. This is a preliminary analysis and has not yet been validated in the field. Please send ground feedback to UNITAR - UNOSAT.

You can also look at the static map for a quick reveiew of the data you have downloaded or to see how UNOSAT visualizes it.

![Add Layer]()

HDX provides additional information on each data source including *layers*, *data source* and *contributor*. It often provides data in *multiple formats*. For our purpose, we will download the shape files. If you prefer to work in [ArcGIS](https://www.arcgis.com), you are welcome to download the geo database (`.gdb file`). 

Likewise, UNITAR/UNOSAT maintains a good repository on their site and frequently updates the data that can be accessed [here](http://www.unitar.org/unosat). The data is all made available on HDX, which is likely where you will download from, but you can always check UNITARs site to see if they have an update. 

![Add Layer]()

### Tutorial Title: Designing a Simple Cluster Map

##### Steps:
  * 01. QGIS: Explore / Edit UNOSAT dataset
  * 02. WEB: Export dataset as JSON file
  * 03. WEB: Design Categorized Cluster Map
  * 04. WEB: Change Clusters Appearance 
  * 05. WEB: Embed Map in your Case Study 

##### 01. QGIS: Explore / Edit HIU dataset

First, bring your `.shp` files into QGIS. To do this, Go to `Menu > Layer > Add Layer > Add Vector Layer` and browse to the .zip file you downloaded. Then holding onto the `Shift` key, select the layers you want to Add. If you select all or bring layers that you require, just remove them form the layer panel, by Layer > Right Click > Remove. Just keep the 2 layers below. Note: Make sure you have the correct Dataset and the shape file is `2015`.

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

Now `duplicate` your layer in Layers Panel and Go To attributes table again. This way you make sure you don't end up editing your main dataset. For the Cluster map, we just want to `clusterize` the events. In this easy example, we will not be adding pop-ups and descriptions of each event. The `Clusters` will disaggregate into marked damaged points. 

![Add Layer]()

We do not need all these fields in our visualization and to make our files simple and faster, it is recommended that you remove all unwanted data fields. In your attributes table, Go to the Third Last button from right Delete Column. In the pop up window select the unrequired fields and hit OK.  We will keep only the following: 

*	SiteID

It takes a while to process after which you have a file with a single column. If your system hangs, you cna also delete 5 columns at a time, or so.

Our attribute table now has each event as a point with no associated information. In order to save the X-Y coordinate information in our attribute table, Go To `Menu > Vector > Geometry Tools > Export / Add Geometry Tables`. Then select your input data layer and `Save` as a new `shape file`. Check `Add` result to `Canvas` option. NO w you should see the X-Y Coordinate Columns added to your data. If you are seeing more columns in your attributes table, it is ok. As menioned earlier, you should try to delete as many as possible. But as long as you have these 3, you can proceed.

*	SiteID
*	XCOORD
*	YCOORD

![Add Layer]() m10

##### 02. WEB: Export dataset as JSON file

export as json

##### 03. WEB: Design Categorized Cluster Map

add categories details / colors / code

##### 04. WEB: Change Clusters Appearance 

css.

##### 05. WEB: Embed Map in your Case Study 

Using the code, provide in [tutorial2](), you can embed any interactive website, in your case study. Test `width` and `height` ratios, to see what works best for you. Note: You will need to upload your site in order to embed it. You could test it using a locally saved .html file. If you save it in the same folder as the casestudy, just  use *filename.html*. Furthermore, it can be tricky to have this working within your case study. 

```html
<iframe width='100%' height='500px' frameBorder='0' src= "filename.html" name="iframe_x"></iframe> 
<p><a href="filename.html" target="iframe_x">Interactive Site</a></p>
```


### Deliverables:

### Tutorial Checklist
- [x] 01. QGIS: Explore / Edit UNOSAT dataset
- [x] 02. WEB: Export dataset as JSON file
- [x] 03. Design Categorized Cluster Map
- [x] 04. WEB: WEB: Change Clusters Appearance 
- [x] 05. WEB: Embed Map in your Case Study  


NOTE: You can do the same tutorial using, the Cultural Heritage Sites, *open data*, from the [Humanitarian Information Unit] website, to design an Interactive *Catergorized* Cluster Map, using Web tools, Mapbox and the Open Source Library Leaflet. For this, you will use the .shp file provided by HIU of identified cultural heritage sites and edit and export it as a JSON file, using QGIS. You will then use *open source* library leaflet an its built in *cluster* function to design the interactive map based on categories. Lastly, you will edit the css, to change the look of the clusters. We chose to show you the UNOSAT dataset, so it is easier to see the difference in approach and visualizations. 

