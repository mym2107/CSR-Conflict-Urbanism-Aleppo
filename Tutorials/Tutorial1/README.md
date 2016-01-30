######CSR / Conflict Urbanism Aleppo 
##Tutorial 1: Mapping Aleppo

In this tutorial, you will be using [OpenStreetMaps](https://www.openstreetmap.org/#map=13/36.2022/37.1619) to map your selected region of Aleppo. CSR worked with [Humanitarian OpenStreetMap Team](https://hotosm.org/) to set a project on OSM's tasking manager, for mapping the urban form and damage in Aleppo. The project, restricted to invite-only allows users to map Aleppo and mark damage by comparing current High Resolution Satellite Imagery. 

### Tools:
For this tutorial, we will be using the following tools:
* [OSM-Editor](https://www.openstreetmap.org/edit?editor=id#map=13/36.2022/37.1619)
* [OSM-JOSM](https://josm.openstreetmap.de/)

**OpenStreetMap** 
is a tool for creating and sharing map information. Anyone can contribute to OSM, and thousands of people add to the project every day. Users draw maps on computers, rather than paper, but as we will see in this guide, drawing a map on a computer is not all that different from drawing on paper. We still draw lines to represent roads, fields, and anything else, and we still represent schools and hospitals with symbols. The important thing is that OSM maps are saved on the internet, and anyone can access them at any time, totally free.

**The HOT Tasking Manager**
The HOT Tasking Manager, http://tasks.hotosm.org/, is an intuitive tool that mappers can use to sort an area into a grid, and work together to map an area in an organized way. This allows mappers throughout the world to assist in mapping a defined region with a minimum risk of overlapping work areas, and also allows people both on the ground and working remotely (also sometimes referred to as “armchair mappers”) to collaborate effectively, rapidly, and avoid accidental rework being required due to conflicts.

```
You must have received an email, with a User ID and Password. Please use that for this tutorial and for using the Conflict Urbanism: Aleppo Project, on OSM. Please note, it is possible to map Aleppo through any account on Open Street Maps but our version of the project, which is a controlled mapping project, allows acces to restricted High Resolution Satellite Imagery from 2015. The data is used and processed in the same way, like any other OSM project. The updates you create are in realtime and will be updated on the OSM site soon. Hence, please make sure you are mapping accurately. We understand, that Aleppo is dense and a lot of the parts are unclear through the various sources of satellite imagery. If you would like to create a rough map, for your own use, you can do so in QGIS or Mapbox. Mapping that is not acceptable will not be entered into OSM. 
```

##### Steps:
  * 01. OSM: Understand OSM
  * 02. OSM Editor
  * 03. OSM JOSM

01. OSM: 

![Add Layer]: OSM Image

![Add Layer] Our system : OSM: Layer

02. OSM Editor
OSM Tasking Manager: https://tasks.hotosm.org
Project: #1453 Conflict Urbanism - Aleppo

Custom Tile:
https://a.tiles.mapbox.com/v4/c4sr.3aak56r2/{zoom}/{x}/{y}.jpg?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A

03. [JOSM](http://learnosm.org/en/josm/)

OpenStreetMap Contributors spend the bulk of their time editing. The more you edit, the better you get, and the more you learn. This section of learnOSM contains tutorials that will help you learn about editing with JOSM, which is the preferred editor for many mappers and is far more configurable than iD.

[Download here](josm.openstreetmap.de)
Note: You will need Java installed on your system.

3 Key Settings: 
+ JOSM > Preferences > Connection Settings -> Add Username and Password
+ JOSM > Imagery Preferences > Add TMS > Enter the URL and Name it 2015_Aleppo
+ JOSM > Preferences >  Preferences -> Download 'Building Module' Plugin

Go to Imagery & Switch the layer on
Save .gpx file and Add to JOSM to see area boundary
Check Imagery Offset
Use building module to map
Default setting: Building
Save Often
When Complete: Upload to OSM
