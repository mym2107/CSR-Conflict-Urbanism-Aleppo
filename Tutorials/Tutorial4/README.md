######CSR / Conflict Urbanism Aleppo
##Tutorial 4: Creating a Basic Interactive Web Map 

Overview: In this tutorial,

### Tools: 
* QGIS
* Mapbox (Browser)
* HTML / CSS / JS

### Datasets: 
* Neighborhood.zip
* Informal.zip

### Data Access:
*CSR_Repo: Neighborhood.zip
*CSR_Repo: Informal.zip

### Steps:
* Setup Tutorial2 in QGIS
* Add Neighborhood Data
* Adjust Neighborhood Data
* Add Informal Data (csv)
* Perform Feature Join
* Export Neighborhood file as Shape file
* Export Informal file as Shape file
* Setup Mapbox Account, ID and Key
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
