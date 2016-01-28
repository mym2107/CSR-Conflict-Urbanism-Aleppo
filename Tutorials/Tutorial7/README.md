######CSR / Conflict Urbanism Aleppo
##Tutorial 7: Creating a Interactive Before / After Satellite Imagery Map
Overview: In this tutorial

### Tools:
* GDAL
* QGIS
* HTML / CSS / JS
	
### Datasets: 
* Aleppo_2015.zip

### Data Access:
* CSR_Repo: Imagery/Aleppo_2015.zip

### Steps:
* Setup Tutorial7 in QGIS
* Optional GDAL Basics
* Add Aleppo_2015 Imagery
* Set Projection
* Clip and Export Selected Region
* Convert to BigTiff 
* Add Files to Mapbox
* Set Up Interactive Map with Layers
* Set Up Swipe Feature
* Add Credits
* Embed Interactive Map in Case Study

```html
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
<title>Layers</title>
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
.range {
  position:absolute;
  width:100%;
  }
.leaflet-top .leaflet-control-zoom {
  top:20px;
  }
</style>

<div id='map'></div>
<input id='range' class='range' type='range' min='0' max='1.0' step='any' />

<script>
L.mapbox.accessToken = 'pk.eyJ1Ijoic3RhdGVvZmV4Y2VwdGlvbiIsImEiOiJQQVJaS1g4In0.o8lCHrDFmA-hNCVaqbDV7Q';
var map = L.mapbox.map('map');
L.mapbox.tileLayer('stateofexception.b3ee5b96').addTo(map);

var overlay = L.mapbox.tileLayer('stateofexception.39ed7a6c').addTo(map);
var range = document.getElementById('range');

function clip() {
  var nw = map.containerPointToLayerPoint([0, 0]),
      se = map.containerPointToLayerPoint(map.getSize()),
      clipX = nw.x + (se.x - nw.x) * range.value;

  overlay.getContainer().style.clip = 'rect(' + [nw.y, clipX, se.y, nw.x].join('px,') + 'px)';
}

range['oninput' in range ? 'oninput' : 'onchange'] = clip;
map.on('move', clip);
map.setView([36.21, 37.15], 13);

clip();
</script>
</body>
</html>
```

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12650193/de35003a-c5af-11e5-9f49-8eec9c7c57a7.png)

### Deliverable:
Template with Before/After Interactive Map 
