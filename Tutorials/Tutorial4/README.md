######CSR / Conflict Urbanism Aleppo
##Tutorial 4: Creating a Basic Interactive Web Map 

In this tutorial, you will be a making a basic interactive map of Aleppo, Syria through the use of *Open Source* GIS software, [QGIS](http://www.qgis.org/en/site/) and *Open Source* mapping platform for custom designed maps, [Mapbox](https://www.mapbox.com/). You will download *Neighborhood Level Data* and *Informal Settlements Data* from the [CSR](http://www.c4sr.columbia.edu/) Data Repository. You will build the *Neigborhood Level Map* in [Mapbox Studio](https://www.mapbox.com/mapbox-studio/) and the *Informal Settlements Map* in [Mapbox Classic](https://www.mapbox.com/mapbox-studio-classic/#darwin). You will then embed these interactive maps, individually in the case studies and also build a standalone two layer *Web Map*. 

### Tools:
For this tutorial, we will be using the following tools:
* [QGIS](http://www.qgis.org/en/site/)
* [Mapbox](https://www.mapbox.com/)
* HTML, CSS and Javascript 

### Datasets:
For this tutorial, we will be using the following datasets:
* Neighborhood.zip, Download [here](/Tutorials/Tutorial4/Data/Neighborhood.zip)
* Informal.zip, Download [here](/Tutorials/Tutorial4/Data/Informal.zip) 

### Datasets Overview:
This section provides detailed explanation of each data source. You can skip this section, if you would like to continue with the tutorial. However, it is recommended that you familiarize yourself with these sources, as they will asssist you in your research.

##### Neighborhood Level Data:
*Neighborhood Level Data* is a dataset prepared by CSR. It uses the *Neighborhood Map* published in the [Aleppo City Profile Report](http://unhabitat.org/city-profile-aleppo-multi-sector-assessment/), pg.24 published by UN-Habitat, in May 2014. We digitized the map based on Google Earth satellite imagery, and added Arabic tranlations for the neighborhood names. In a case, where a neighborhood was divided in parts, we've used roman numerals. A neighborhood map was also developed by [UNITAR/UNOSAT](http://www.unitar.org/unosat/), in early 2015, which slightly varies from the one initially produced by [UN Habitat](http://unhabitat.org/).  

##### Informal Settlements Data:
*Informal Settlements Data* is a dataset prepared by CSR. It uses the *report* on *Informal Settlements Report* from [Madinatuna: Aleppo City Planning Strategy](http://madinatuna.com/en/informals). This report is the first output of the Informal Settlements sub-component of the Syrian German Programme for Sustainable Urban Development (UDP) in Aleppo, which was supported by GTZ, the German Agency for Technical Cooperation. GTZ has been engaged in Syria since 1994, supporting the “Rehabilitation of the Old City of Aleppo”. In 2007, on request of the Syrian Government, GTZ widened its approach to providing technical advice to the Municipality of Aleppo on formulating a City Development Strategy and dealing with informal settlements. The report identifies **28** Informal Settlements. We identified corresponding entries using our Neighborhood map and coded those Neigborhoods and *Informal*. 

### Creating a Basic Interactive Web Map

##### Steps:
  * 01. QGIS: SetUp Neighborhood and Informal Data 
  * 02. MAPBOX: Sign Up, Installation and Introduction 
  * 03. MAPBOX_Classic: Design Informal Settlement Map
  * 04. MAPBOX_Studio: Design Neighborhood Map
  * 05. WEB: Embed Neighborhood and Informal Maps in Case Study
  * 06. WEB: Set Up 2 layer Interactive Map through HTML/JS/CSS
  * 07. WEB: Embed 2 layer Map in Case Study

##### 01. QGIS: SetUp Neighborhood and Informal Data
**QGIS Project**

##### 02. MAPBOX: Sign Up, Installation and Introduction 
* Setup Mapbox Account, ID and Key
*
##### 03. MAPBOX_Classic: Design Informal Settlement Map

##### 04. MAPBOX_Studio: Design Neighborhood Map

##### 05. WEB: Embed Neighborhood and Informal Maps

##### 06. WEB: Set Up 2 layer Interactive Map 

##### 07. WEB: Embed 2 layer Map in Case Study


* Add Informal.shp through MapboxEditor
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12650558/42ce0da6-c5b1-11e5-87f6-efa19e9c2c1e.png) 

* Embed Informal Interactive Map in Template
```html
<iframe width='100%' height='500px' frameBorder='0' src='https://a.tiles.mapbox.com/v4/c4sr.o59e801k/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'></iframe>
```
* Install Mapbox Studio (Mac / Win)
* Add Neighborhood.shp through MapboxEditor
* Embed Neighborhood Interactive Map in Template
```html
<iframe width='100%' height='500px' frameBorder='0' src='https://a.tiles.mapbox.com/v4/c4sr.o59e801k/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'></iframe>
```
* Set Up 2 layer Interactive Map through HTML/JS/CSS
* Embed Interactive Map in Case Study

```html
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
<title>A simple map</title>
<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
<script src='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.js'></script>
<link href='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.css' rel='stylesheet' />
<style>
  body { margin:0; padding:0; }
  #map { position:absolute; top:0; bottom:0; width:100%; }
</style>
</head>
<body>
<div id='map'></div>
<script>
L.mapbox.accessToken = '<your access token here>';
var map = L.mapbox.map('map', 'mapbox.streets')
    .setView([40, -74.50], 9);
</script>
</body>
</html>
```

##### Adding Feature Layer for Display

```
        var featureLayer1 = L.mapbox.featureLayer('c4sr.o59e801k')
            .on('click', function(e) {
                if (!markerPopup) {
                    var content = '<b>' + e.layer.toGeoJSON().properties.NAME + '<br \/>' +
                        '' + e.layer.toGeoJSON().properties.NAME_A + '<\/b>';
                    L.popup({}).setLatLng(e.layer.getBounds().getCenter()).setContent(content).openOn(map);
                }
            })
```

### Deliverable:
Template with 2 Layer Interactive Map 
