######CSR / Conflict Urbanism Aleppo 
##Tutorial 08: Designing a Navigational Story Map

In this tutorial, you will be using your research to design a story-based navigational map. Using a *vertical* scroll bar, you will be able to tag different parts of your story to different regions on the adjacent map. This tutorial is designed for you to be able to easily enter your research for a functional story map. Please feel free to explore more enhanced *design* possibilities.

### Tools:
For this tutorial, we will be using the following tools:
* [WEB](http://www.qgis.org/en/site/)
* [Sublime](http://www.sublimetext.com/)
* [Chrome](https://www.google.com/chrome/)


### Datasets:
For this tutorial, we will be using the following datasets:
* Research.zip, Download [here](link to repository)
* StoryMap.zip, Download [here](https://www.dropbox.com/s/e12g50d22lon7mw/StoryMap.html?dl=0)

  
### Datasets Overview:
This section provides detailed explanation of the data source. You can skip this section, if you would like to continue with the tutorial. However, it is recommended that you familiarize yourself with these sources, as they will asssist you in your research.

##### Data set 1: Research
We decided to build a navigational map to introduce visitors to the 9 gates of Aleppo. For our research, we used text from *wikipedia*. We limited the amount of text for each feature, for a better prototype. Using *code* discussed in Tutorial 2, you can embed links, additional pages, etc.  


### Tutorial Title: Designing a Simple Cluster Map

##### Steps:
  * 01. WEB: Organizing Research 
  * 02. WEB: Adding Long/Lat for Points
  * 03. WEB: Adding Story Content to Website
  * 04. WEB: Changing Story Appearance 
  * 05. WEB: Embed Map in your Case Study 

##### 01. WEB: Organizing Research

For each feature, you need 'Title', 'Text' and 'Coordinates'. In this part you will research your topic and add relevant text. Please make sure you do not have special characters in your text. While *researching*, note that you can embed image/video/article links and also add content in arabic, as shown in the html example.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12905601/cc0fb1d4-ced8-11e5-8aaf-5f88867a72f8.png)

##### Research Text:

**Title**: The Gates of Aleppo
**Sub Title**: The old part of Aleppo city is surrounded with 5 kilometers long thick walls, pierced by the nine historical gates of the old town. These are, clockwise from the north-east of the citadel

**Gate 01:**
Title: `Bab al-Hadid`
Text: Bab al-Hadid: meaning the Iron Gate of Victory, is one of the nine historical gates of the Ancient City of Aleppo, Syria. It is one of the well-preserved gates of old Aleppo. The gate was planned during the reign of Az-Zahir Ghazi and built by his son Mohammed as Bab al-Qanat (the Aqueduct Gate). It was rebuilt by the final Mamluk sultan Al-Ashraf Qansuh al-Ghawri in 1509. The gate and surrounding quarters of the old city are some of the best preserved areas in the old city of Aleppo. It was historically known for its blacksmiths and to this day, there are some operating with the same traditional practices, most of whom have had the trade in their family for many generations.
coordinates: [37.165065, 36.2034507]

**Gate 02:** 
Title: `Bab al-Ahmar`
Text: Bab al-Ahmar: meaning the Red Gate, was one of the nine historical gates of the Ancient City of Aleppo, Syria. The name was derived from the village of al-Hamr as the gate was leading to the village at the eastern suburbs of ancient Aleppo. The gate was built in the eastern part of old Aleppo in the first half of the 13th century, during the reign of the Ayyubid emir of Aleppo al-Aziz Muhammad. It was renovated during the rule of the Mamluk sultan Al-Ashraf Qansuh al-Ghawri at the beginning of the 16th century. The gate was completely ruined in the 1830s by Ibrahim Pasha of Egypt during his campaign in Syria against the Ottomans between 1831-1833. in 1834, the stones of the gate were used to build the Ibrahim Pasha military barracks (the current Aleppo Citadel Museum) in the Citadel of Aleppo.[1] The famous Hammam Bab al-Ahmar is located near the gate within the historic walls of the ancient city. It was completely ruined during the Ottoman rule over Syria.
coordinates: [37.1655558, 36.1997715]

**Gate 03:** 
Title: `Bab al-Nairab`
Text: Bab al-Nairab: also spelled Bab al-Nayrab, meaning the "Gate of Al-Nayrab", was one of the nine historical gates of the Ancient City of Aleppo in northern Syria, but has since disappeared. Its name refers to the nearby village of al-Nayrab (currently a suburb of Aleppo) as the gate led towards the village. Today, the city district where the gate used to stand is commonly called Bab al-Nairab, but is officially known as Muhammad Bek. The Bab al-Nairab gate was built sometime during the period of 1216–1237 in the southeastern part of the ancient city by the Ayyubid ruler of Aleppo, al-Aziz Muhammad, son of predecessor az-Zahir Ghazi.[1] The latter had planned its construction but al-Aziz carried it out following az-Zahir's death. The new gate marked the southward expansion of Aleppo during az-Zahir's rule.
coordinates: [37.1656376, 36.1957546]

**Gate 04:** 
Title: `Bab al-Maqam`
Text: Bab al-Maqam: is one of the Gates of Aleppo. The 13th century structure was built by al-Aziz Muhammad. Deviations in its design from the majority of medieval Syrian gates suggest that its function was ceremonial rather than military. In Constructions of Power and Piety in Medieval Aleppo (1997), Yasser Tabbaa details some of these differences, noting that they reinforce the possibility that the gate had primarily a religious and political function, serving as homage to Abraham and contrasting with the eastern shrines of Mashhad al-Dikka and Mashhad al-Husayn.
coordinates: [37.1584877, 36.1919206]

**Gate 05:**
Title: `Bab Qinnasri`n
Text: Bab Qinnasrin: is one of the gates of the medieval Old City of Aleppo in northern Syria. In its present form, it dates to 1256. The gate was originally built by the Hamdanid ruler Sayf al-Dawla in 964, and fitted with the doors of the gate of Amorium, taken as spoils by Caliph al-Mu'tasim after his sack of the city in 838. Al-Mu'tasim installed them at the entrance of his palace in Samarra, until they were taken, probably towards the end of the 9th century, and installed at al-Raqqah, whence Sayf al-Dawla in turn took them.
coordinates: [37.151497, 36.1944861]

**Gate 06:** 
Title: `Bab Antakeya`
Text: Bāb Antakiya: "Gate of Antioch" formed one of the most important defense gates in Aleppo, protecting the city from the west. Baba Antakiya is located in the centre of the western wall of the old city of Aleppo, and its name was derived from Antioch, the capital of ancient Syria, as the gate was the main exit which was leading to the city of Antioch. It is one of the oldest gates built due to its strategic site thus going through several construction periods. Sayf al-Daula rebuilt the gate using its antique foundations and the Fatimids restored it during the 11th century. It went through periodical repairs and restorations until 1422. The Bab is well preserved today with both its towers still intact. The two massive Ayyubid defense towers were built with thick stone walls into which the deep arrow slits were discreetly inserted. The gate contains the shrine of Sheikh Ali al-Rumi in the southern tower.
coordinates: [37.1511322, 36.1948931]

**Gate 07:**
Title: `Bab Jnen`
Text: Bāb Jnēn: was one of the gates of Aleppo that used to lead to gardens on the banks of the Quwēq river. The gate was demolished about 120 years ago in order to widen the road. There used to be numerous exchangers and storage houses for goods near the gate, and a pine dating back to the 16th century. The gate had a tower called the "serpent tower" in which was said[by whom?] to be a talisman capable of protecting from serpent bites. Bāb Jnēn today is the site of a traditional souk.
coordinates: [37.1498463, 36.2022385]

**Gate 08:** 
Title: `Bab al-Faraj`
Text: Bab al-Faraj: Bab al-Faradis was one of the 9 main gates of the ancient city walls of Aleppo, Syria. It was located at the northern side of the ancient city. The gate was ruined in 1904. Some remains are still found at the north-eastern part of the gate. Bab al-Faraj was built by Az-Zahir Ghazi and later renovated by An-Nasir Yusuf. In 1904 it was torn down with a portion of the surrounding fabric to become a public square known by the same name. Nowadays, it is a major junction of the traffic flow in and out of the old city to the extramural areas. The Bab al-Faraj reconstruction project is one of the first preservation efforts in Aleppo. 
coordinates: [37.1505141, 36.2040714]

**Gate 09:**
Title: `Bab al-Nasr`
Text: `Bab al-Nasr: meaning the Gate of Victory, is one of the nine historical gates of the Ancient City of Aleppo, Syria. It was partially ruined during the Ottoman rule over Syria. It was originally called Bab al-Yahud because of its location next to the Jewish Quarter. It was rebuilt and renamed by az-Zahir Ghazi in 1212 to become the most important northern gate of the city. Its simple, direct access form became more complex under the reconstruction with the fortifying tactics used by the Ayyubids. The left tower has an opening that leads to a vaulted chamber that changes the direction of procession towards the right. The chamber connects to a vaulted corridor carved out of the thickness of the wall that leads outside to the left.
coordinates: [37.1604779, 36.2041243]


##### 02. WEB: Adding Long/Lat for Points

As we assume that you are not using QGIS for this tutorial, we will use Google Maps, to get Long/Lat for each feature. The Title and Text is documented in the below format. Then using Google Maps, browse to the locations and save (long, Lat) that usually appears on the status bar.

T8-2
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12905600/cbf54d6c-ced8-11e5-98e7-46079ec5734f.png)

* Gate01: `37.165065,  36.2034507`
* Gate02: `37.1655558, 36.1997715`
* Gate03: `37.1656376, 36.1957546`
* Gate04: `37.1584877, 36.1919206`
* Gate05: `37.151497,  36.1944861`
* Gate06: `37.1511322, 36.1948931`
* Gate07: `37.1498463, 36.2022385`
* Gate08: `37.1505141, 36.2040714`
* Gate09: `37.1604779, 36.2041243`

I added these back into the research section. You cain maintain a separate list for them. For this tutorial, we have hard-coded each point of interest. As sotyr maps will atmost have 10-20 points, it is ok to input this manually. If you have lots of points, it might be better to divided your map into different narratives, then having using browse across an extremely long story. 

##### 03. WEB: Adding Story Content to Website

We assume that you will be switching the titles, text and coordinates based on your requirement You can either copy/paster the .html code below or use the .html file in the downloads section. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12939116/3108fc74-cfbc-11e5-84bb-22ad40076b5a.png)

There are few key sections to understanding the navigational map. Each `feature point` is an Element that has a correlating *section*. We use the section id, to reference these elements and sections. Note: The last entry is a nested entry so the scrolling feature goes to the last section.

```html
    <section id='Gate01'>
      <h3>Title</h3>
      <p>Text Paragraph</p>
    </section>
```
 
Next, for each element, using the 'section-id'  tag, we now provide more information:

```html
{ geometry: { type: "Point", coordinates: [Lat, Long] },
  properties: { id: "Gate01" }, type: 'Feature' },
```

Other than these 2 components for your story, you need to decide on the base map, you will be using for navigation. In some cases you will need a map API, if te layer you selected is not for public use. For instance, you can use the public layer: mapbox.satellite or you can use CSR's layer of the 2015 High Resolution Image of Aleppo.

BaseMap: `mapbox.satellite ` 

Once you have all your data, please input it in the required format, into your html file, using Sublime. 
Now open the file in Chrome and test the Navigation.


```html
<!-- Conflict Urbanism: Aleppo
     Center for Spatial Research
     Madeeha Merchant (mym2107@columbia.edu)
     * This script is a modified version of the example provided by Mapbox.

================================================================= -->

<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />

<!-- ADD: Name to Appear on Tab --> 
<title>Narrative and Navigation Map</title>
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
  /* Settings for Inactive Navigation */
  color:rgba(0,0,0,0.5);
  }

.scroll {
  /* Settings for Scroll Feature */
  display:block;
  text-align:center;
  }

.sections {
  /* Set Color of Sections, R,G,B Alpha (Transparency) */
  background:rgba(255,255,255,0.7);
  /* Set Width of Sections */
  width:300px;
  }

section {
  padding:20px;
  color:rgba(0,0,0,0.5);
  -webkit-transition:background 500ms, color 500ms;
          transition:background 500ms, color 500ms;
  }

section.active {
  /* Settings for Active Navigation */
  background:#fff;
  color:#404040;
  }

</style>
<div id='map'></div>

<article id='narrative'>
  <div class='sections prose'>
    <section id='cover' class='cover active'>

      <!-- ADD: Title of Story -->
      <h2>The Gates of Aleppo</h2>

      <!-- ADD: Description -->
      <p>The old part of Aleppo city is surrounded with 5 kilometers long thick walls, pierced by the nine historical gates of the old town. These are, clockwise from the north-east of the citadel:</p>
      <small class='scroll quiet'>Scroll &#x25BE;</small>
    </section>

    <!-- ADD: Section ID's for each Element in your Story. 
        In this example, we will be looking at the 9 gates of Aleppo -->

    <!-- ADD: Gate1: Bab al-Hadid -->
    <section id='hadid'>
      <h3>Bab al-Hadid</h3>
      <p>Bab al-Hadid: meaning the Iron Gate of Victory, is one of the nine historical gates of the Ancient City of Aleppo, Syria. It is one of the well-preserved gates of old Aleppo. The gate was planned during the reign of Az-Zahir Ghazi and built by his son Mohammed as Bab al-Qanat (the Aqueduct Gate). It was rebuilt by the final Mamluk sultan Al-Ashraf Qansuh al-Ghawri in 1509. The gate and surrounding quarters of the old city are some of the best preserved areas in the old city of Aleppo. It was historically known for its blacksmiths and to this day, there are some operating with the same traditional practices, most of whom have had the trade in their family for many generations.</p>
    </section>

    <!-- ADD: Gate2: Bab al-Ahmar -->    
    <section id='ahmar'>
      <h3>Bab al-Ahmar</h3>
      <p>Bab al-Ahmar: meaning the Red Gate, was one of the nine historical gates of the Ancient City of Aleppo, Syria. The name was derived from the village of al-Hamr as the gate was leading to the village at the eastern suburbs of ancient Aleppo. The gate was built in the eastern part of old Aleppo in the first half of the 13th century, during the reign of the Ayyubid emir of Aleppo al-Aziz Muhammad. It was renovated during the rule of the Mamluk sultan Al-Ashraf Qansuh al-Ghawri at the beginning of the 16th century. The gate was completely ruined in the 1830s by Ibrahim Pasha of Egypt during his campaign in Syria against the Ottomans between 1831-1833. in 1834, the stones of the gate were used to build the Ibrahim Pasha military barracks (the current Aleppo Citadel Museum) in the Citadel of Aleppo.</p>
    </section>

    <!-- ADD: Gate3: Bab al-Nairab -->    
    <section id='nairab'>
      <h3>Bab al-Nairab</h3>
      <p>Bab al-Nairab: also spelled Bab al-Nayrab, meaning the "Gate of Al-Nayrab", was one of the nine historical gates of the Ancient City of Aleppo in northern Syria, but has since disappeared. Its name refers to the nearby village of al-Nayrab (currently a suburb of Aleppo) as the gate led towards the village. Today, the city district where the gate used to stand is commonly called Bab al-Nairab, but is officially known as Muhammad Bek. The Bab al-Nairab gate was built sometime during the period of 1216–1237 in the southeastern part of the ancient city by the Ayyubid ruler of Aleppo, al-Aziz Muhammad, son of predecessor az-Zahir Ghazi.[1] The latter had planned its construction but al-Aziz carried it out following az-Zahir's death. The new gate marked the southward expansion of Aleppo during az-Zahir's rule. Along with Banqusa, Bab al-Nairab became one of the most powerful quarters of Aleppo, where the countryside immigrants and the merchants of the caravan trade held sway and could influence the public order as well as the urban tax system.</p>
    </section>

    <!-- ADD: Gate4: Bab al-Maqam -->    
    <section id='maqam'>
      <h3>Bab al-Maqam</h3>
      <p>Bab al-Maqam: is one of the Gates of Aleppo. The 13th century structure was built by al-Aziz Muhammad. Deviations in its design from the majority of medieval Syrian gates suggest that its function was ceremonial rather than military. In Constructions of Power and Piety in Medieval Aleppo (1997), Yasser Tabbaa details some of these differences, noting that they reinforce the possibility that the gate had primarily a religious and political function, serving as homage to Abraham and contrasting with the eastern shrines of Mashhad al-Dikka and Mashhad al-Husayn</p>
    </section>

    <!-- ADD: Gate5: Bab Qinnasrin -->    
    <section id='qinnasrin'>
      <h3>Bab Qinnasrin</h3>
      <p>Bab Qinnasrin: is one of the gates of the medieval Old City of Aleppo in northern Syria. In its present form, it dates to 1256. The gate was originally built by the Hamdanid ruler Sayf al-Dawla in 964, and fitted with the doors of the gate of Amorium, taken as spoils by Caliph al-Mu'tasim after his sack of the city in 838. Al-Mu'tasim installed them at the entrance of his palace in Samarra, until they were taken, probably towards the end of the 9th century, and installed at al-Raqqah, whence Sayf al-Dawla in turn took them </p>
    </section>

    <!-- ADD: Gate6: Bab Qinnasrin -->    
    <section id='antakeya'>
      <h3>Bab Antakeya</h3>
      <p>Bāb Antakiya: "Gate of Antioch" formed one of the most important defense gates in Aleppo, protecting the city from the west. Baba Antakiya is located in the centre of the western wall of the old city of Aleppo, and its name was derived from Antioch, the capital of ancient Syria, as the gate was the main exit which was leading to the city of Antioch. It is one of the oldest gates built due to its strategic site thus going through several construction periods. Sayf al-Daula rebuilt the gate using its antique foundations and the Fatimids restored it during the 11th century. It went through periodical repairs and restorations until 1422. The Bab is well preserved today with both its towers still intact. The two massive Ayyubid defense towers were built with thick stone walls into which the deep arrow slits were discreetly inserted. The gate contains the shrine of Sheikh Ali al-Rumi in the southern tower.</p>
    </section>

    <!-- ADD: Gate7: Bab Jnen -->    
    <section id='jnen'>
      <h3>Bab Jnen</h3>
      <p>Bāb Jnēn: was one of the gates of Aleppo that used to lead to gardens on the banks of the Quwēq river. The gate was demolished about 120 years ago in order to widen the road. There used to be numerous exchangers and storage houses for goods near the gate, and a pine dating back to the 16th century. The gate had a tower called the "serpent tower" in which was said to be a talisman capable of protecting from serpent bites. Bāb Jnēn today is the site of a traditional souk.</p>
    </section>

    <!-- ADD: Gate8: Bab al-Faraj -->   
    <section id='faraj'>
      <h3>Bab al-Faraj</h3>
      <p>Bab al-Faraj: Bab al-Faradis was one of the 9 main gates of the ancient city walls of Aleppo, Syria. It was located at the northern side of the ancient city. The gate was ruined in 1904. Some remains are still found at the north-eastern part of the gate. Bab al-Faraj was built by Az-Zahir Ghazi and later renovated by An-Nasir Yusuf. In 1904 it was torn down with a portion of the surrounding fabric to become a public square known by the same name. Nowadays, it is a major junction of the traffic flow in and out of the old city to the extramural areas. The Bab al-Faraj reconstruction project is one of the first preservation efforts in Aleppo.</p>
    <!-- ADD: Gate8: Bab al-Nasr : Note this is added differently. --> 
    <section id='nasr'>
      <h3>Bab al-Nasr</h3>
      <p>Bab al-Nasr: meaning the Gate of Victory, is one of the nine historical gates of the Ancient City of Aleppo, Syria. It was partially ruined during the Ottoman rule over Syria. It was originally called Bab al-Yahud because of its location next to the Jewish Quarter. It was rebuilt and renamed by az-Zahir Ghazi in 1212 to become the most important northern gate of the city. Its simple, direct access form became more complex under the reconstruction with the fortifying tactics used by the Ayyubids. The left tower has an opening that leads to a vaulted chamber that changes the direction of procession towards the right.</p>

    <!-- ADD: Reference Here -->  
      <small class='colophon'>
        Adapted from <a href='https://en.wikipedia.org/wiki/Ancient_City_of_Aleppo'>Old City Aleppo</a>
      </small>
    </section>
  </div>
</article>

<script>
<!-- ADD: Your Map API from Mapbox -->  
L.mapbox.accessToken = 'pk.eyJ1Ijoic2lkbCIsImEiOiJkOGM1ZDc0ZTc5NGY0ZGM4MmNkNWIyMmIzNDBkMmZkNiJ9.Qn36nbIqgMc4V0KEhb4iEw';

// In this case, we just hardcode data into the file. 
// This could be dynamic if you have many points - which may not be recommended.
// The important part about this data is that the 'id' property matches the HTML above 

// For each of the places, Add the coordinates accordingly.
var places = { type: 'FeatureCollection', features: [

//36.2034507,37.165065
{ geometry: { type: "Point", coordinates: [37.165065, 36.2034507] },
  properties: { id: "hadid", zoom: 15 }, type: 'Feature' },

//36.1997715,37.1655558 (invert)
{ geometry: { type: "Point", coordinates: [37.1655558, 36.1997715] },
  properties: { id: "ahmar" }, type: 'Feature' },

//36.1957546,37.1656376
{ geometry: { type: "Point", coordinates: [37.1656376, 36.1957546] },
  properties: { id: "nairab" }, type: 'Feature' },

//36.1919206,37.1584877
{ geometry: { type: "Point", coordinates: [37.1584877, 36.1919206] },
  properties: { id: "maqam" }, type: 'Feature' },

//36.1944861,37.151497
{ geometry: { type: "Point", coordinates: [37.151497, 36.1944861] },
  properties: { id: "qinnasrin" }, type: 'Feature' },

//36.1948931,37.1511322
{ geometry: { type: "Point", coordinates: [37.1511322, 36.1948931] },
  properties: { id: "antakeya" }, type: 'Feature' },
  
//36.2022385,37.1498463
{ geometry: { type: "Point", coordinates: [37.1498463, 36.2022385] },
  properties: { id: "jnen" }, type: 'Feature' },

//36.2040714,37.1505141
{ geometry: { type: "Point", coordinates: [37.1505141, 36.2040714] },
  properties: { id: "faraj" }, type: 'Feature' },

//36.2041243,37.1604779
{ geometry: { type: "Point", coordinates: [37.1604779, 36.2041243] },
  properties: { id: "nasr" }, type: 'Feature' }
]};

//c4sr.3aak56r2
var map = L.mapbox.map('map', 'mapbox.satellite', {
    zoomControl: false
});

var placesLayer = L.mapbox.featureLayer(places)
    .addTo(map);

// Ahead of time, select the elements we'll need 
// the narrative container and the individual sections
var narrative = document.getElementById('narrative'),
    sections = narrative.getElementsByTagName('section'),
    currentId = '';

setId('cover');

// Do NOT Change 
function setId(newId) {


    if (newId === currentId) return;

    placesLayer.eachLayer(function(layer) {
        if (layer.feature.properties.id === newId) {
            map.setView(layer.getLatLng(), layer.feature.properties.zoom || 18);
            layer.setIcon(L.mapbox.marker.icon({
                'marker-color': '#000'
            }));
        } else {
            layer.setIcon(L.mapbox.marker.icon({
                'marker-color': '#fff'
            }));
        }
    });
    for (var i = 0; i < sections.length; i++) {
        sections[i].className = sections[i].id === newId ? 'active' : '';
    }

    currentId = newId;
}

narrative.onscroll = function(e) {
    var narrativeHeight = narrative.offsetHeight;
    var newId = currentId;
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
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12939114/2ffc664a-cfbc-11e5-9fcd-f541273745ea.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12939113/2fe1347e-cfbc-11e5-8e1f-7ec0a8090a19.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12939112/2fdf735a-cfbc-11e5-81c4-44e616435f8d.png)

##### 04. WEB: Changing Story Appearance  

You can easily change the way, your Story Map looks by changing a few of the settings at the start of your .html file. Here are some key points that you can test. You can add additional styling features to your html code, once you have your basic navigation functioning. Remember, you can embed links, add pop-ups and also change the style and color of your icons. 

```html
.quiet {
  /* Settings for Inactive Navigation */
  color:rgba(0,0,0,0.5);
  }

.scroll {
  /* Settings for Scroll Feature */
  display:block;
  text-align:center;
  }

.sections {
  /* Set Color of Sections, R,G,B Alpha (Transparency) */
  background:rgba(255,255,255,0.5);
  /* Set Width of Sections */
  width:240px;
  }

section {
  padding:20px;
  color:rgba(0,0,0,0.5);
  -webkit-transition:background 500ms, color 500ms;
          transition:background 500ms, color 500ms;
  }

section.active {
  /* Settings for Active Navigation */
  background:#fff;
  color:#404040;
  }
```

##### 05. WEB: Embed Map in your Case Study   

Using the code, provide in [tutorial2](), you can embed any interactive website, in your case study. Test `width` and `height` ratios, to see what works best for you. Note: You will need to upload your site in order to embed it. You could test it using a locally saved .html file. If you save it in the same folder as the casestudy, just  use *filename.html*. Furthermore, it can be tricky to have this working within your case study. 

You can use another option from Tutorial 2, which will place a temporary image, that links to the interactive site. You can also, embed a .gif or animated video of the story map and turn it into a clickable link to open the interactive in a spearate window.

```html
<iframe width='100%' height='500px' frameBorder='0' src= "filename.html" name="iframe_x"></iframe> 
<p><a href="filename.html" target="iframe_x">Interactive Site</a></p>
```

### Deliverables:

### Tutorial Checklist
- [x] 01. WEB: Organizing Research
- [x] 02. WEB: Adding Long/Lat for Points
- [x] 03. WEB: Adding Story Content to Website
- [x] 04. WEB: Changing Story Appearance 
- [x] 05. WEB: Embed Map in your Case Study  
