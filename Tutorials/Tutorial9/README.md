######CSR / Conflict Urbanism Aleppo
##Tutorial 9: Creating an Interactive Categorized Cluster Map
Overview: 

### Tools:
* QGIS
* Leaflet
* Adobe Illustrator
* HTML / CSS / JS
	
### Datasets: 
*CulturalSites.zip

### Data Access:
*HDX: CulturalSites.zip

### Steps:
* Setup Tutorial9 in QGIS
* Add + Analyze Cultural Sites
* Add X,Y Co-ordinates
* Check Categories
* Export as GeoJSON
* Set Up Interactive Map
* Set Up Cluster Map
* Set Up Map Styling
* Make Icons with Illustrator
* Add Layers for Satellite and OSM
* Embed Interactive Map in Case Study

* Selected Sites Only
* Add Shape File to Mapbox Editor
* Set Icons and Display Information
* Embed iframe Map

```html
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
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
L.mapbox.accessToken = 'pk.eyJ1IjoiY3N0b2FmZXIiLCJhIjoiY2lnNnRwN3hpMDF4YnU3a3BkNjAzcnBvaCJ9.0EZvAi2Bvn1zGdLj6crPsA';
// Here we don't use the second argument to map, since that would automatically
// load in non-clustered markers from the layer. Instead we add just the
// backing tileLayer, and then use the featureLayer only for its data.
var map = L.mapbox.map('map')
    .setView([36.2, 37.2], 13)
    .addLayer(L.mapbox.tileLayer('mapbox.high-contrast'));

// Since featureLayer is an asynchronous method, we use the `.on('ready'`
// call to only use its marker data once we know it is actually loaded.


L.mapbox.featureLayer()
    .loadURL('2_UNOSAT.geojson')
    .on('ready', function(e) {
    // create a new MarkerClusterGroup that will show special-colored
    // numbers to indicate the type of rail stations it contains
    function makeGroup(color) {
      return new L.MarkerClusterGroup({ 
        maxClusterRadius: 60,
        iconCreateFunction: function(cluster) {
          return new L.DivIcon({
            iconSize: [30, 20],
            html: '<div style="text-align:center;color:#fff;background:' +
            color + '">' + cluster.getChildCount() + '</div>'
          });
        }

      }).addTo(map);
    }
    // create a marker cluster group for each type of rail station
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

    var groups = {
        SingleGroup: makeGroup('gray')
    };
    e.target.eachLayer(function(layer) {
      // add each rail station to its specific group.

        layer.setIcon(myIcons[layer.feature.properties.Main_Dam_2]);
        layer.bindPopup(layer.feature.properties.SiteID + " in " + layer.feature.properties.Neighborho + "<br>" + " " + layer.feature.properties.SensorID_3 + ": " + layer.feature.properties.SensorDa_2);

        groups['SingleGroup'].addLayer(layer);
    });
});
</script>
```

</body>
</html>

### Deliverable:
* Template with Cluster Interactive Map
* Optional: Template with Cultural Sites Map 


