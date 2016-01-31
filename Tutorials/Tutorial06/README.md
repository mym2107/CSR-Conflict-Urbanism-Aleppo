######CSR / Conflict Urbanism Aleppo
##Tutorial 6: Creating an Interactive Cluster Map 
Overview: In this tutorial

### Tools:
* QGIS
* Leaflet
* Adobe Illustrator
* HTML / CSS / JS
	
### Datasets: 
* UNOSAT.zip

###Data Access:
* HDX: UNOSAT.zip

###Steps:
* Setup Tutorial4 in QGIS
* Add + Analyze UNOSAT Data
* Add X,Y Co-ordinates
* Export as GeoJSON
* Edit to Javascript file
* Set Up Interactive Map
* Set Up Cluster Map
* Set Up Map Styling
* Add Layers for Before/After
* Embed Interactive Map in Case Study


##### Initializing Cluster

```        
        var markers1 = new L.MarkerClusterGroup();

        var geojson = L.geoJson(hrw, {
            pointToLayer: function (feature, latlng) {
                var myIcon = L.icon({
                    iconUrl: 'icon1 copy.png',
                    iconRetinaUrl: 'icon1_2x copy.png',
                    iconSize: [10, 10],
                    iconAnchor: [16, 16],
                    popupAnchor: [15, 32],
                });
                return L.marker(latlng, { icon: myIcon });
            }
         });
         markers1.addLayer(geojson);
```
##### Set Up in Layers Tab to visualize the UNOSAT Layer *markers1*

```html
var controls = L.control.layers({
	    'BASE LAYER': L.mapbox.tileLayer('sidl.m7vqvuzk,c4sr.w6vedqb7').addTo(map)
	    },{
	    'DAMAGE: UNOSAT': markers1
	    });
```	    
	    
###Deliverable:
Template with Cluster Interactive Map 
