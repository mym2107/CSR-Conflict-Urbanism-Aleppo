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
 * Open the `Neighborhood.shp` and `Informal.shp` file in QGIS, through `Layer > Add Layer > Add Vector Layer`
 * Look at the `attributes table` to see the available fields. Delete Uncessary fields to save space on mapbox

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12660491/f84ffeca-c5e1-11e5-9c0e-5ffd9d16e9b7.png)

*`Neighborhood.shp`:133 Neighborhoods
  * Id
  * Name
  * Name_A
  
*`Informal.shp`:15 Neighborhoods
  * Id
  * Name
  * Name_A
  * Informal
  
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12660490/f84d4c7a-c5e1-11e5-9d73-4e730c500205.png)

Export these as `shape files`, after setting Coordinate Reference System CRS 
Mapbox only allows *WGS 84/ Pseudo Mercator ([EPSG:3857](https://epsg.io/3857))*

##### 02. MAPBOX: Sign Up, Installation and Introduction 
**Mapbox**
Mapbox is an open source mapping platform. Below we will look at the 3 different working environments it offers and some basic terminology.
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12666482/6302c9f0-c60f-11e5-8e8f-d3c11283d3ae.png)

[Mapbox Editor](https://www.mapbox.com/editor/#style) is an online interface where you can choose a Mapbox classic style as a basemap, drag and drop features, and share your project. Editor requires no coding skills and can be easily integrated into a web template. You can import GeoJSON, CSV, KML, or GPX files into Mapbox Editor. You can also export data in GeoJSON or KML format.
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12666484/66c7e368-c60f-11e5-8cd9-47022b4494b0.png)

[Mapbox Studio Classic](https://www.mapbox.com/help/define-mapbox-studio-classic/) is a desktop application for designing world maps. It allows you to design maps by using [vector tiles](https://www.mapbox.com/help/define-vector-tiles/) and [CartoCSS](https://www.mapbox.com/help/define-cartocss/). Mapbox Studio Classic allows you to upload your map directly to your Mapbox account and then use your map style with our Developer tools. You can also use the map that you design in Mapbox Studio Classic as a baselayer in Mapbox Editor. You can import shapefiles, KML, GeoJSON, GPX, CSV, TIF, and VRT files into Mapbox Studio Classic. You can export Mapbox Studio Classic sources as MBTiles.
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12666485/66cc8bac-c60f-11e5-8588-1290bf068b36.png)

[Mapbox Studio](https://www.mapbox.com/mapbox-studio/)o is an online application for designing world maps. It allows you to design maps with vector tiles and Mapbox GL. You can use your map style on the web with Mapbox GL JS and in your mobile apps with the iOS SDK. You can import MBTiles, KML, GPX, GeoJSON, Shapefiles (zipped), CSV, and GeoTIFF files into Mapbox Studio to create vector tiles for styling.
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12666481/63022e14-c60f-11e5-8792-2f651a648615.png)

Key Terms
**API Key**
To use any of Mapbox’s tools, APIs, or SDKs, you’ll need a Mapbox access token. Mapbox uses access tokens to associate requests to API resources with your account. There are two types of access tokens:
**Public access tokens** — use a public access token in websites or applications where they can be easily rotated, like scripts on a web page.
**Secret access tokens** — only use a secret access token in places where it’s difficult to rotate, like mobile apps which require an approval process. You should also use secret tokens when you need to set specific token parameters, like when using the Uploads API.

For the purpose of this tutorial, you will have have a `Public API Key`
```
c4sr API Key: https://api.mapbox.com/v4/mapbox.emerald/page.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A
```
**Map ID**
Any time you create a project with *Mapbox Editor*, upload a style with *Mapbox Studio Classic*, or upload data to your account on *Mapbox.com*, it will receive a `map ID`. The `map ID` allows you to reference that specific project, style, or data with a *Mapbox API* or SDK. This means you can create a custom map style in *Mapbox Studio Classic* and then use that map with your Mapbox.js project or upload a dataset and add it as a custom source in Mapbox Studio Classic.
```
Your map ID will always start with your Mapbox username followed by your map’s unique handle: `username.handle`
```
There are three different types of `map IDs`:
* [Projects](https://www.mapbox.com/studio/classic/projects/) — projects are made with Mapbox Editor. Share your map from Mapbox Editor or use your project map ID with Mapbox APIs or SDKs.
* [Styles](https://www.mapbox.com/studio/classic/styles/) — styles are custom maps and styled data made with Mapbox Studio Classic. Use your style map ID with Mapbox APIs or import it into Mapbox Editor.
* [Data](https://www.mapbox.com/studio/data) — You can upload data or sources on Mapbox.com and from Mapbox Studio Classic. Add your data map ID as a custom source in Mapbox Studio Classic or update it with the Mapbox Upload API.

There are also some common `map IDs`, that you can use:
* *mapbox.streets*: Street Layer, OpenStreetMaps
* *mapbox.satellite*: Satellite Layer, Digital Globe
* *mapbox.high-contrast*: Stamen Design high Contrast Map
* *mapbox.landsat-live*: LANDSAT Imagery

##### 03. MAPBOX_Classic: Design Informal Settlement Map

##### 04. MAPBOX_Studio: Design Neighborhood Map

##### 05. WEB: Embed Neighborhood and Informal Maps

##### 06. WEB: Set Up 2 layer Interactive Map 
**Baselayer**
A `baselayer` often refers to the map style that you designed in [Mapbox Studio Classic](https://www.mapbox.com/help/define-mapbox-studio-classic/) or the [Mapbox classic styles](https://www.mapbox.com/maps/). The baselayer provides geographic context and serves as a starting point for your map.

**Layers**
`Layers` are used in GL styles to add styling rules to specific subsets of data. Layers contain both a reference to the data for which they’re defining a style as well as the styling rules to be applied.


##### 07. WEB: Embed 2 layer Map in Case Study


* Add Informal.shp through MapboxEditor
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12650558/42ce0da6-c5b1-11e5-87f6-efa19e9c2c1e.png) 

* Embed Informal Interactive Map in Template

**i-frame**
* Mapbox Editor generates an embed code for you to add your maps to your website or blog. The embed code uses an `iframe` to display your map. This HTML element allows you to put a webpage into another webpage, insulating all the code that makes your map work from the code on your website.

```html
<iframe width='100%' height='500px' frameBorder='0' src='https://a.tiles.mapbox.com/v4/c4sr.o59e801k/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'></iframe>
```

* Install Mapbox Studio (Mac / Win)
* Add Neighborhood.shp through MapboxEditor
* Embed Neighborhood Interactive Map in Template

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

```javascript
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
