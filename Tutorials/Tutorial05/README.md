######CSR / Conflict Urbanism Aleppo
##Tutorial 5: Creating an Interactive Historical Map 
Overview: In this tutorial

###Tools: 
* QGIS
* Mapbox (Browser)
* HTML / CSS / JS

###Datasets: 
*Historical_Map.pdf
*ConflictControl_Map.pdf

###Data Access:
CSR_Repo: Historical_Map.pdf (Provided)
CSR_Repo: ConflictControl_Map.pdf

###Steps:
* Setup Tutorial3 in QGIS
* Add Mapbox Satellite Layer
* Set Projection and CRS
* Install GeoReferencer Plugin
* GeoReference Historical Map
* Export Georeferenced Map as .tiff
* Export to Mercator Projection
* Add RasterData1 to Mapbox
* GeoReference ConflictState Map
* Export Georeferenced Map as .tiff
* Export to Mercator Projection
* Add RasterData2 to Mapbox
* Set Up 3 layer Interactive Map with Toggle
* Embed Interactive Maps in Case Study

``` html
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
<title>SIDL_CU_Syria</title>
<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
<script src='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.js'></script>
<link href='https://api.tiles.mapbox.com/mapbox.js/v2.1.4/mapbox.css' rel='stylesheet' />
<style>
  body { margin:0; padding:0; }
  #map { position:absolute; top:0; bottom:0; width:100%; }
</style>
</head>
<body>
<style>
.menu-ui {
  background:#fff;
  position:absolute;
  top:10px;right:10px;
  z-index:1;
  border-radius:3px;
  width:120px;
  border:1px solid rgba(0,0,0,0.4);
  }
  .menu-ui a {
    font-size:13px;
    color:#404040;
    display:block;
    margin:0;padding:0;
    padding:10px;
    text-decoration:none;
    border-bottom:1px solid rgba(0,0,0,0.25);
    text-align:center;
    }
    .menu-ui a:first-child {
      border-radius:3px 3px 0 0;
      }
    .menu-ui a:last-child {
      border:none;
      border-radius:0 0 3px 3px;
      }
    .menu-ui a:hover {
      background:#f8f8f8;
      color:#404040;
      }
    .menu-ui a.active {
      background:#3887BE;
      background:#000000;
      color:#FFF;
      }
      .menu-ui a.active:hover {
        background:#3074a4;
        background:#000000;
        }
</style>
<nav id='menu-ui' class='menu-ui'></nav>
<div id='map'></div>

<script>
L.mapbox.accessToken = 'pk.eyJ1Ijoic3RhdGVvZmV4Y2VwdGlvbiIsImEiOiJQQVJaS1g4In0.o8lCHrDFmA-hNCVaqbDV7Q';
var map = L.map('map').setView([36.21, 37.15], 7);
var layers = document.getElementById('menu-ui');

addLayer(L.mapbox.tileLayer('stateofexception.39ed7a6c'), 'Satellite', 3);
addLayer(L.mapbox.tileLayer('stateofexception.b3ee5b96'), 'Open Street Maps', 2);
addLayer(L.mapbox.tileLayer('stateofexception.e6d3a2d9'), 'Syria GIS Layers', 1);

function addLayer(layer, name, zIndex) {
    layer
        .setZIndex(zIndex)
        .addTo(map);

    // Create a simple layer switcher that
    // toggles layers on and off.
    var link = document.createElement('a');
        link.href = '#';
        link.className = 'active';
        link.innerHTML = name;

    link.onclick = function(e) {
        e.preventDefault();
        e.stopPropagation();

        if (map.hasLayer(layer)) {
            map.removeLayer(layer);
            this.className = '';
        } else {
            map.addLayer(layer);
            this.className = 'active';
        }
    };

    layers.appendChild(link);
}
</script>
</body>
</html>
```


	
###Deliverable:
Template with 3 Layer Interactive Map 
