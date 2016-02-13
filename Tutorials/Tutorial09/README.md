######CSR / Conflict Urbanism Aleppo 
##Tutorial 6: Designing a Categorized Cluster Map

In this tutorial, you will be using, the UNOSAT's Damage Analysis Sites, from the [Humanitarian Data Exchange](https://data.hdx.rwlabs.org/) website, to design an Interactive *Catergorized* Cluster Map, using Web tools, Mapbox and the Open Source Library Leaflet. You will use the .shp file provided by HIU of identified cultural heritage sites and edit and export it as a JSON file, using QGIS. You will then use *open source* library leaflet an its built in *cluster* function to design the interactive map based on categories. Lastly, you will edit the css, to change the look of the clusters. 


### Tools:
For this tutorial, we will be using the following tools:
* [QGIS](http://www.qgis.org/en/site/)
* [Sublime](http://www.sublimetext.com/)
* [Chrome](https://www.google.com/chrome/)
* [Terminal] *Command Line*


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

You can also look at the static map for a quick reveiew of the data you have downloaded or to see how UNOSAT visualizes it. In this tutorial, we will try to use a similar style approach.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027500/78ae924e-d252-11e5-8687-5685521a701f.png)

### Tutorial Title: Designing a Simple Cluster Map

##### Steps:
  * 01. QGIS: Explore / Edit UNOSAT dataset
  * 02. WEB: Export dataset as JSON file
  * 03. WEB: Design Categorized Cluster Map
  * 04. WEB: Change Clusters Appearance 
  * 05. WEB: Embed Map in your Case Study 

##### 01. QGIS: Explore / Edit HIU dataset

First, bring your `.shp` files into QGIS. To do this, Go to `Menu > Layer > Add Layer > Add Vector Layer` and browse to the .zip file you downloaded. Then holding onto the `Shift` key, select the layers you want to Add. If you select all or bring layers that you require, just remove them form the layer panel, by Layer > Right Click > Remove. Just keep the 2 layers below. Note: Make sure you have the correct Dataset and the shape file is `2015`.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027502/863814a8-d252-11e5-9976-7fda757b07fd.png)

You will add:
*	CityBorder
*	Damage_sites_Update3_Aleppo_2015...

Uncheck the `City Border` file and `Zoom to layer`, for the Damage Sites data. Open attributes table, by `Right-Click` and examine the fields in the dataset. You will see the following fields: 
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

Now `duplicate` your layer in Layers Panel and Go To attributes table again. This way you make sure you don't end up editing your main dataset. For the Cluster map, we want to `Clusterize` based on the Damage Typlogy marked by UNOSAT. Each marked site is assigned category 1,2 or 3; where 1 means destroyed (red), 2, severaly damaged (orange) and 3 moderately damaged (yellow). 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027505/8b1f5350-d252-11e5-9fce-f2dd3723324a.png)

We do not need all these fields in our visualization and to make our files simple and faster, it is recommended that you remove all unwanted data fields. In your attributes table, First, Click on the first button with the `pencil` icon to be able to edit your table. Then go to the Third Last button from right 'Delete Column'. In the pop up window select the unrequired fields and hit OK.  We will keep only the following: 

*	SiteID
* Neighborho
* SensorID_3
*	SensorDa_2
*	Main_Dam_2

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13028124/ce87f850-d265-11e5-8315-cf00173521ab.png)

It takes a while to process after which you have a file with a single column. If your system hangs, you can also delete 5 columns at a time, or so.


##### 02. WEB: Export dataset as JSON file

Our attribute table now has each event with certain associated information. To use with `ClusterAPI`, we need our data in Javascript format. To do this, `Right Click` on your Layer and `Save As`. Save your file in geoJSON format and make sure the Projection is set to `EPSG:4326`. You can check your saved layer in QGIS, to make sure the data appears the same. Now Close QGIS. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13028123/ce809100-d265-11e5-9921-f8a746024a4c.png) 

Now, you can drag and drop your `unosatc.geoJSON` file into chrome. You will notice, each entry retains it's geometry that is the `X,Y coordinates`. This is what each record has:

```
{ "type": "Feature", "properties": { "SiteID": "Building (General \/ Default)", "SensorDa_2": "2015\/04\/26", "SensorID_3": "Pleiades", "Main_Dam_2": "2", "Neighborho": "Farafira" }, "geometry": { "type": "Point", "coordinates": [ 37.157763310000064, 36.203296022000075 ] } },
```
Now save the file in the same folder as your `.html` file. Note: Unlike tutorial 6, we do not need to change anything in the geoJSON file.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13028121/c7b79080-d265-11e5-89f4-5ebb55968cc0.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13028120/c79e7d8e-d265-11e5-87ef-ffe63c390c6f.png) 

##### 03. WEB: Design Categorized Cluster Map

For this tutorial we are using an `open source` Javascript library called `leaflet`. You can access more details about it [here](http://leafletjs.com). It is a useful visualization library and provides many great functions that can be called in your code, through their API. 

*Leaflet:*
Leaflet is the leading open-source JavaScript library for mobile-friendly interactive maps. Weighing just about 33 KB of JS, it has all the mapping features most developers ever need. Leaflet is designed with simplicity, performance and usability in mind. It works efficiently across all major desktop and mobile platforms, can be extended with lots of plugins, has a beautiful, easy to use and well-documented API and a simple, readable source code that is a joy to contribute to. For more information on *clustering*, you can look [here](https://github.com/Leaflet/Leaflet.markercluster). 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027504/8b1e5536-d252-11e5-946f-6bfa3e0110d9.png)

For this section of the tutorial, we have provided the `.html` file that you will need to use with your data. You can choose to copy/paste from here or the downloads file (which includes all the reference files also). Open `Cluster.zip` and download. Then open index.html in Sublime. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13028122/c7c5e16c-d265-11e5-9454-d34944555252.png)

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
<title>UNOSAT</title>
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

<script>

//ADD: Access Token from your Mapbox Account
L.mapbox.accessToken = 'pk.eyJ1IjoiY3N0b2FmZXIiLCJhIjoiY2lnNnRwN3hpMDF4YnU3a3BkNjAzcnBvaCJ9.0EZvAi2Bvn1zGdLj6crPsA';

// Here we don't use the second argument to map, since that would automatically
// load in non-clustered markers from the layer. Instead we add just the
// backing tileLayer, and then use the featureLayer only for its data.
var map = L.mapbox.map('map')

// ADD: Long, Lat and Zoom Level. The settings below zoom at Aleppo
    .setView([36.2, 37.2], 13)
// ADD: Background Layer    
    .addLayer(L.mapbox.tileLayer('mapbox.satellite'));

// Since featureLayer is an asynchronous method, we use the `.on('ready'`
// call to only use its marker data once we know it is actually loaded.


L.mapbox.featureLayer()
// Add your geoJSON file here
    .loadURL('unosatc.geojson')
    .on('ready', function(e) {
    // Create a new MarkerClusterGroup that will show special-colored icons
    function makeGroup(color) {
      return new L.MarkerClusterGroup({ 
    // Set the Max Marker radius / Applicable at highest zoom
        maxClusterRadius: 60,
        iconCreateFunction: function(cluster) {
          return new L.DivIcon({
            // Set icons size here:
            iconSize: [30, 20],
            // Stylize icon and text color:
            html: '<div style="text-align:center;color:#fff;background:' +
            color + '">' + cluster.getChildCount() + '</div>'
          });
        }

      }).addTo(map);
    }

    // create a marker cluster group for each type of damage typology: 3 in our case.
    // For each of your categories, select icon (your designed png) and size
    var myIcons = {
        '1': L.icon({
            iconUrl: 'icons/icon_red_sq.png',
            iconRetinaUrl: 'icons/icon_red_ret_sq.png',
            iconSize: [14, 14],
            iconAnchor: [16, 16],
            popupAnchor: [0, -15]
        }),
        '2': L.icon({
            iconUrl: 'icons/icon_orange_sq.png',
            iconRetinaUrl: 'icons/icon_orange_retina_sq.png',
            iconSize: [12, 12],
            iconAnchor: [16, 16],
            popupAnchor: [0, -15]
        }),
        '3': L.icon({
            iconUrl: 'icons/icon_yellow_sq.png',
            iconRetinaUrl: 'icons/icon_yellow_ret_sq.png',
            iconSize: [10, 10],
            iconAnchor: [16, 16],
            popupAnchor: [0, -15]
        })
    };

    // Here declare these to be rendered as a single group
    var groups = {
        SingleGroup: makeGroup('gray')
    };
    e.target.eachLayer(function(layer) {


    // Declare what appears in the tool tip when any icon is clicked on.
        layer.setIcon(myIcons[layer.feature.properties.Main_Dam_2]);
        layer.bindPopup(layer.feature.properties.SiteID + " in " + layer.feature.properties.Neighborho + "<br>" + " " + layer.feature.properties.SensorID_3 + ": " + layer.feature.properties.SensorDa_2);

        groups['SingleGroup'].addLayer(layer);
    });
});
</script>


</body>
</html>
``` 

In the above code remember to do the following: 

Line 35: Enter your *MAP API Key* from Mapbox
``` 
L.mapbox.accessToken = 'pk.eyJ1IjoiY3N0b2FmZXIiLCJhIjoiY2lnNnRwN3hpMDF4YnU3a3BkNjAzcnBvaCJ9.0EZvAi2Bvn1zGdLj6crPsA';
``` 

Line 43: Enter the *long, lat and zoom levels*. By default it is set to Aleppo
``` 
    .setView([36.2, 37.2], 13)
``` 

Line 45: Select your *Base Layer*. In this case I've selected Mapbox OSM. You can also select the 2015 Image over Aleppo. If you would like to do so, please send us an email, to provide you with the MapID. If you are a student in the course, you will already have access to all our Map IDs.
``` 
    .addLayer(L.mapbox.tileLayer('mapbox.satellite'));
``` 

Line 53: You need to read data from your *geoJSON file*
``` 
    .loadURL('unosatc.geojson')
```

Line 62-67: Stylize the group cluster icon:
```
eturn new L.DivIcon({
            // Set icons size here:
            iconSize: [30, 20],
            // Stylize icon and text color:
            html: '<div style="text-align:center;color:#fff;background:' +
            color + '">' + cluster.getChildCount() + '</div>'
          }); 
```

Line 107-108: Here we select the data that we would like to show when you click on the icon. Please see how you can also add 'custom text.

```
        layer.setIcon(myIcons[layer.feature.properties.Main_Dam_2]);
        layer.bindPopup(layer.feature.properties.SiteID + " in " + layer.feature.properties.Neighborho + "<br>" + " " + layer.feature.properties.SensorID_3 + ": " + layer.feature.properties.SensorDa_2);
 ```
 
Once you have your `html` file, you can test in Chrome. But there is a catch here. For your `geoJSON data` to work, you will need to be on a webserver to test this file. If you have `FTP` access, you can use a public browser. However, you can also use a local server to test you html file.

##### Using Terminal for a Local Server

To do so, Go to `Terminal`, to use Command Line. Please refer to Tutorial 2, if you are unfamiliar with this. You will need `python` installed if you would like to use the below method. You can type `install python` in your terminal or you can look at easy to donwload packages like [Anaconda]. Once you have python installed, please proceed to the next step.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13028119/c1b9a056-d265-11e5-961f-a335a60ad59b.png)

In the terminal, browse to your folder and type the following command
```
python -m SimpleHttpServer
```

Please make sure you label your html file as `index.html`

Then in your browser type this address: 
`http://localhost:8000/`

You should now be able to see your map and clusters in the web browser. 

##### 04. WEB: Change Clusters Appearance 

Once you render your map in the web browser, you might want to change the appearance of your map icons and cluster icons. The html file has the following code, that can be changed

Line 75-97: Stylize your icon based on your group. Which means, when your cluster disintegrates. The icons are placed in the folder `icons`. You can replace then to your requirement. You can vary size for each catergory also. 

```
    var myIcons = {
        '1': L.icon({
            iconUrl: 'icons/icon_red_sq.png',
            iconRetinaUrl: 'icons/icon_red_ret_sq.png',
            iconSize: [14, 14],
            iconAnchor: [16, 16],
            popupAnchor: [0, -15]
        }),
        '2': L.icon({
            iconUrl: 'icons/icon_orange_sq.png',
            iconRetinaUrl: 'icons/icon_orange_retina_sq.png',
            iconSize: [12, 12],
            iconAnchor: [16, 16],
            popupAnchor: [0, -15]
        }),
        '3': L.icon({
            iconUrl: 'icons/icon_yellow_sq.png',
            iconRetinaUrl: 'icons/icon_yellow_ret_sq.png',
            iconSize: [10, 10],
            iconAnchor: [16, 16],
            popupAnchor: [0, -15]
        })
    };
```

Line 99-102: Declares and stylize the cluster icons. We set the color as 'gray' but this can be an RGB value. Or you can change the shape.
```
    // Here declare these to be rendered as a single group
    var groups = {
        SingleGroup: makeGroup('gray')
```
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13028118/c08ef2a8-d265-11e5-9226-bc4d02ee9886.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13028117/c06e6e16-d265-11e5-8f60-e2e37e0f37d5.png)

##### 05. WEB: Embed Map in your Case Study 

Using the code, provide in [tutorial2](), you can embed any interactive website, in your case study. Test `width` and `height` ratios, to see what works best for you. Note: You will need to upload your site in order to embed it. You could test it using a locally saved .html file. If you save it in the same folder as the casestudy, just  use *filename.html*. Furthermore, it can be tricky to have this working within your case study. 

```html
<iframe width='100%' height='500px' frameBorder='0' src= "filename.html" name="iframe_x"></iframe> 
<p><a href="filename.html" target="iframe_x">Interactive Site</a></p>
```

### Deliverables:

### Tutorial Checklist
- [x] 01. QGIS: Explore / Edit HIU dataset
- [x] 02. WEB: Export dataset as JSON file
- [x] 03. Design Categorized Cluster Map
- [x] 04. WEB: WEB: Change Clusters Appearance 
- [x] 05. WEB: Embed Map in your Case Study  


NOTE: You can do the same tutorial using, the Cultural Heritage Sites, *open data*, from the Humanitarian Information Unit , to design an Interactive *Catergorized* Cluster Map, using Web tools, Mapbox and the Open Source Library Leaflet. For this, you will use the .shp file provided by HIU of identified cultural heritage sites and edit and export it as a JSON file, using QGIS. You will then use *open source* library leaflet an its built in *cluster* function to design the interactive map based on categories. Lastly, you will edit the css, to change the look of the clusters. We chose to show you the UNOSAT dataset, so it is easier to see the difference in approach and visualizations. 
