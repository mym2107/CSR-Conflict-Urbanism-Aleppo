######CSR / Conflict Urbanism Aleppo
##Tutorial 8: Creating a Story Based Interactive Map
Overview: 

### Tools:
* QGIS
* HTML / CSS / JS
	
### Datasets: 
* UNOSAT.zip

### Data Access:
*HDX: UNOSAT

### Steps:
* Setup Tutorial8 in QGIS
* Add UNOSAT Data
* Segregate Military Targets 
* Add XY Co-ordinates
* Add More Specific Data
* Set Up Interactive Map
* Set Up Story for Interactive Map
* Embed Interactive Map in Case Study

##### Set Up Interactive Map:
```html
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
<title>Scroll-driven navigation with markers and a narrative</title>
<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
<script src='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.js'></script>
<link href='https://api.mapbox.com/mapbox.js/v2.2.4/mapbox.css' rel='stylesheet' />
<style>
  body { margin:0; padding:0; }
  #map { position:absolute; top:0; bottom:0; width:100%; }
</style>
</head>
<body>
<style>
article {
  position:absolute;
  top:0;
  right:0;
  bottom:0px;
  left:0;
  overflow:auto;
  }
.quiet {
  color:rgba(0,0,0,0.5);
  }
.scroll {
  display:block;
  text-align:center;
  }
.sections {
  background:rgba(255,255,255,0.5);
  width:240px;
  }
section {
  padding:20px;
  color:rgba(0,0,0,0.5);
  -webkit-transition:background 500ms, color 500ms;
          transition:background 500ms, color 500ms;
  }
section.active {
  background:#fff;
  color:#404040;
  }
</style>
<div id='map'></div>

<article id='narrative'>
  <div class='sections prose'>
    <section id='cover' class='cover active'>
      <h2>The Adventure of the Bruce-Partington Plans</h2>
      <p>by Sir Arthur Conan Doyle</p>
      <small class='scroll quiet'>Scroll &#x25BE;</small>
    </section>
    <section id='baker'>
      <h3>Name</h3>
      <p>Text</p>
    </section>
    <section id='aldgate'>
      <h3>Name</h3>
      <p>Text</p>
    </section>
    <section id='london-bridge'>
      <h3>Name</h3>
      <p>Tetx</p>
    </section>
    <section id='woolwich'>
      <h3>Name</h3>
      <p>Text</p>
    </section>
    <section id='gloucester'>
      <h3>Name</h3>
      <p>Text</p>
    </section>
    <section id='caulfield-gardens'>
      <h3>Name</h3>
      <p>Text"</p>
    </section>
    <section id='telegraph'>
      <h3>Name</h3>
      <p>text</p>
    </section>
    <section id='charing-cross'>
      <h3>Name</h3>
      <p>Text</p>
      <small class='colophon'>
        Adapted from <a href='http://www.gutenberg.org/files/2346/2346-h/2346-h.htm'>Project Gutenberg</a>
      </small>
    </section>
  </div>
</article>

<script>
L.mapbox.accessToken = 'pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A';
// In this case, we just hardcode data into the file. This could be dynamic.
// The important part about this data is that the 'id' property matches
// the HTML above - that's how we figure out how to link up the
// map and the data.
var places = { type: 'FeatureCollection', features: [
{ geometry: { type: "Point", coordinates: [-0.12960000, 51.50110000] },
  properties: { id: "cover", zoom: 9 }, type: 'Feature' },
{ geometry: { type: "Point", coordinates: [-0.15591514, 51.51830379] },
  properties: { id: "baker" }, type: 'Feature' },
{ geometry: { type: "Point", coordinates: [-0.07571203, 51.51424049] },
  properties: { id: "aldgate" }, type: 'Feature' },
{ geometry: { type: "Point", coordinates: [-0.08533793, 51.50438536] },
  properties: { id: "london-bridge" }, type: 'Feature' },
{ geometry: { type: "Point", coordinates: [0.05991101, 51.48752939] },
  properties: { id: "woolwich" }, type: 'Feature' },
{ geometry: { type: "Point", coordinates: [-0.18335806, 51.49439521] },
  properties: { id: "gloucester" }, type: 'Feature' },
{ geometry: { type: "Point", coordinates: [-0.19684993, 51.5033856] },
  properties: { id: "caulfield-gardens" }, type: 'Feature' },
{ geometry: { type: "Point", coordinates: [-0.10669358, 51.51433123] },
  properties: { id: "telegraph" }, type: 'Feature' },
{ geometry: { type: "Point", coordinates: [-0.12416858, 51.50779757] },
  properties: { id: "charing-cross" }, type: 'Feature' }
]};

var map = L.mapbox.map('map', 'mapbox.streets', {
    zoomControl: false
});

var placesLayer = L.mapbox.featureLayer(places)
    .addTo(map);

// Ahead of time, select the elements we'll need -
// the narrative container and the individual sections
var narrative = document.getElementById('narrative'),
    sections = narrative.getElementsByTagName('section'),
    currentId = '';

setId('cover');

function setId(newId) {
    // If the ID hasn't actually changed, don't do anything
    if (newId === currentId) return;
    // Otherwise, iterate through layers, setting the current
    // marker to a different color and zooming to it.
    placesLayer.eachLayer(function(layer) {
        if (layer.feature.properties.id === newId) {
            map.setView(layer.getLatLng(), layer.feature.properties.zoom || 14);
            layer.setIcon(L.mapbox.marker.icon({
                'marker-color': '#a8f'
            }));
        } else {
            layer.setIcon(L.mapbox.marker.icon({
                'marker-color': '#404040'
            }));
        }
    });
    // highlight the current section
    for (var i = 0; i < sections.length; i++) {
        sections[i].className = sections[i].id === newId ? 'active' : '';
    }
    // And then set the new id as the current one,
    // so that we know to do nothing at the beginning
    // of this function if it hasn't changed between calls
    currentId = newId;
}

// If you were to do this for real, you would want to use
// something like underscore's _.debounce function to prevent this
// call from firing constantly.
narrative.onscroll = function(e) {
    var narrativeHeight = narrative.offsetHeight;
    var newId = currentId;
    // Find the section that's currently scrolled-to.
    // We iterate backwards here so that we find the topmost one.
    for (var i = sections.length - 1; i >= 0; i--) {
        var rect = sections[i].getBoundingClientRect();
        if (rect.top >= 0 && rect.top <= narrativeHeight) {
            newId = sections[i].id;
        }
    };
    setId(newId);
};
</script>
</body>
</html>
```

*Optional:*
* Export Shp file 
* Add Shape file to Mapbox Ed
* Trace Details and add
* Add Details for Mouse Click

### Deliverable:
Template with Interactive Story Map 
