######CSR / Conflict Urbanism Aleppo 
##Tutorial 05: Creating an Interactive Historical Map with *Layers*

In this tutorial, you will make an interactive web map of Aleppo, that allows users to switch between a current stylized *OpenStreetMaps* map and an *old* map of Aleppo, Syria. You will georeference the historical Map of Aleppo, using the *Georeferencer* plugin in *QGIS* and build it as an online map, using *mapbox*. You will then use *mapbox studio* to build a style for OpenStreetMaps. Lastly, you will then use *html, css and javascript* to design an interactive map that allows you to swtich between the 2 map layer, you created. 

### Tools:
For this tutorial, we will be using the following tools:
* [QGIS](http://www.qgis.org/en/site/)
* [Sublime](http://www.sublimetext.com/)
* [Chrome](https://www.google.com/chrome/)


### Datasets:
For this tutorial, we will be using the following datasets:
* HistoricalMapA.zip, Download [here](https://www.dropbox.com/s/cnl3ol3rk1rlfka/AleppoPNG.zip?dl=0)
* Aleppo.zip, Download [here](https://www.dropbox.com/s/wxmer4gb59lnfoc/Aleppo1.zip?dl=0)
* Layers.html, Download [here](https://www.dropbox.com/s/ukj6jku6mshq5j3/Layer1.html?dl=0)

  
### Datasets Overview:
This section provides detailed explanation of each data source. You can skip this section, if you would like to continue with the tutorial. However, it is recommended that you familiarize yourself with these sources, as they will asssist you in your research.

##### Data set: Soviet City Plan of Haleb (Aleppo), Syria:
Digital Raster Graphics (DRGs) of Russian Military Topographic City Plan : Soviet City Plan of Haleb (Aleppo), Syria; Published: Colorado, USA,: LAND INFO Worldwide Mapping, LLC, 1985. This dataset has been provided here by [the Aleppo Project](http://ccnr.ceu.edu/thealeppoproject). As a course student, the georeferenced maps are on your shared Drive. If you are not a student in the course or collaborator, you can email us, to request access. In this tutorial we have used the .jpeg files, which are note georeferenceed. In [Tutorial 7]() you will use the `.tif` file which has already been georeferenced and projected. 

##### Data sets: Additional sources for finding maps of Aleppo), Syria:

1. **Columbia Gulf / 2000 Project** : Headed by Professor. Michael Izady, the Gulf 2000 Project consists of maps of the Middle East Region. The Gulf/2000 Project was created in 1993 as a service to scholars, government officials, business people, journalists and other specialists who have a professional association with the Persian Gulf and Gulf studies. You can acces the site [here](http://gulf2000.columbia.edu/maps.shtml).

t5-1
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872566/e89dc620-cda6-11e5-8f55-10ca3cbd2492.png)

2. **Humanitarian Response: Syria** : The Humaniatraian Response website is a repository for all maps that are being devloped by Humanitarian agencies, for Aleppo and Syria in General. These can be accessed [here](https://www.humanitarianresponse.info/en/operations/syria/infographics?search=&page=2).

t5-2
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872567/e8b6be00-cda6-11e5-9b24-ce323b3d0894.png)

3. **Real Time Maps: Syria**: The Liveuamap is opendata-driven media platform that change the way you receive latest news. Explore a map, messages, pictures and videos from the conflict zones. This platform allows you to take snapshots of maps of the most up to date conflict news, which you can then develop as an overlay, using the same tutorial. You can access the site [here](http://syria.liveuamap.com/).

t5-3
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872568/e8c14c62-cda6-11e5-8f63-10c0a47da95b.png)

### Creating an Interactive Historical Map

##### Steps:
  * 01. QGIS: Georeference Old Map
  * 02. MAPBOX: Build a Raster Layer 
  * 03. MAPBOX_STUDIO: Design New Style
  * 04. WEB: Set Up 2 Layer Interactive
  * 05. WEB: Embed Map in Case Study


##### 01. QGIS: Export Old Map

Download the folder, MapAleppo.zip. You will see the following file. 

*	MapAleppo.jpg	
* 	Aleppo.zip

Open the QGIS Application and first set the [project projection](https://docs.qgis.org/2.2/en/docs/user_manual/working_with_projections/working_with_projections.html). To do so, as soon as you start the Appliction, Go To: `Menu > Project > Project Properties`. In the Window, go to the `Second Tab CRS`. On the right it will list all the possible projections. From the list, under CRS, select `WGS 84 / Pseudo Mercator`. If you have to find the Projection, it is under `Coordinate Reference Systems: Projected Coordinate Systems: Albers Equal Area > Mercator > WGS 84 / Pseudo Mercator`. Then Select `OK`. On the bottom Right of your Map Window, you should be able to see: `EPSG:3857`.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872591/4e4f7356-cda7-11e5-8d31-e9ae42821052.png)

Add the Alp1.shp file from *Aleppo.zip*, through `Menu > Layer > Add Layer > Add Raster layer`. Likewise, you can always *drop* the file directly into the `map window`. 

When you bring in the layer: `Alp1.shp`, remember it's projection is already set now. You can recheck the CRS by going to the layer in the Layers Panel and Right Click on it. Goto: `Properties > General > Coordinate Reference System : EPSG:3857`. If this is different, you can change it in that panel, or right-click layer and click on `Set Layr CRS`. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872593/5a87dfaa-cda7-11e5-94da-c64788d87dbc.png)

Before you bring in an image to *georeference*, you will need a basemap or base image. There are multiple ways to do this. You can either use the built in satellite layers or you can use an image for reference that has already been georeferenced. Whichever you use, remember to make sure it is in the `Web Mercator projection`. 

Bring Satellite Data:
When you open satellite data, it can be extremely slow. Hence, by bringing in the `Alp1.shp` file, you can make sure you are only uploading data for Aleppo, and then further zoom into the selected region. To do so, Right-Click on the `Layer: Alp1`, and click, `Zoom to Layer`.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872594/5a885034-cda7-11e5-8bc2-35221da6640e.png)

Now Goto : `Menu > Web > OpenLayersPlugin > Google Maps > Google Satellite`. Zoom into the area of the citadel (center Aleppo) and see how it overlaps with the satellite data. If your image does not appear, it might be due to internet speed. You can select `OSM/Stamen > Stamen Toner / OSM` in that case. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872595/5a918f14-cda7-11e5-873e-1290e7df1de0.png)

Now, you will need to bring in your map to *georeference* it. To do so, you will be using the *plug-in* [Georeferencer](http://docs.qgis.org/1.8/en/docs/user_manual/plugins/plugins_georeferencer.html) To download / Add plug in, Go to `Menu > Plugins > Manage/Install Plugins`. In the window, type `georeferencer`, under Search. Select and Install. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872596/5a92ea1c-cda7-11e5-8e7d-97ac71618aec.png)

Once installed, you will be able to see it in the following menu. `Menu > Raster > GeoReferencer`.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872597/5a96f01c-cda7-11e5-8dc9-ff8e3c1d9bfa.png)

The *Georeferencer* Window Opens separately and has a completely different Menu System. Click on the first icon to add an image. Select `A1.jpg`. It will bring up the Projection Window. Choose `Web Mercator` again.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872598/5a97b664-cda7-11e5-807b-71f147bb463b.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872600/5aa70aec-cda7-11e5-846f-548a879bf38a.png)

For this tutorial, we will only develop a historical map for Old Aleppo. You can then zoom into the Old Aleppo region and start georeferencing common points. The idea here is simple. You add a point on your historical map and find a corresponding point in your satellite map, by clicking `From Map Canvas`. Each referenced Point will be listed in the table below the Image to be referenced. You need a minimum of 4 points to georeference an image. In most cases I suggest a minimum of 10 and in uniform directions. Once you have selected multiple points, you are ready to reference the image. WHile on the GeoReferencer window, Click `Menu > Settings > Transformation Settings`. In the window, select the `options` as shown. 

*	Transformation Type: `Thin Plate Spline`
*	Resampling Method: `Nearest Neighbor`
* 	Compression: `NONE`
*	Output Raster: Add Save As `Al2.tif`
*	Target SRS: `EPSG: 3857`
* 	Select Load in QGIS

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872599/5aa17096-cda7-11e5-89d3-7a5b3ff77b4d.png)

Look at different parts of the image you brought in and the underlying OSM map to see if they overlap well. You can change the `order` of the layers by dragging the `Stamen Toner / OSM` below. Then `Right Click` on Properties of the Alp1 layer and set `Transparency` at 70%. You will now be able to test the overlap better. Sometimes, you might see the need to go back and add more reference points. 

Note: In this example, we used 4 points near the Citadel region. If you did this exercise with just 4 points, you will also end up with an unsatifactory result. However, getting to this point, you are now able to see exactly the points that you should georeference. In most case, I would do the gerreferencing again, covering the points, where my map is most off. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872603/5aae4884-cda7-11e5-8d99-9ed115f9da5c.png)

Once you are satisfied, with the result, you will export the map as a *GeoTiff*, so you can upload to Mapbox. In some cases, where the image you georeferenced is exactly the size of the map, you can right-click and save as a geotiff file. Here we will only export a porttion of the map. To do so, Go To `Menu > Raster > Extraction > Clipper`

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872602/5aae2cc8-cda7-11e5-8d64-eebc0994470e.png)

In the Clipper Window, Select the Input file, we just Georeferenced and give an Output Name. Select `No Data Value = 0`, check `Load into Canvas when finished` and hit Ok. A new `Clipped Image` should now be saved to your Layers Panel. We now have the file that we need to upload to Mapbox. Your exported Map should have been `Web Mercator`.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872604/5ab53c48-cda7-11e5-8486-760b3764cd5e.png)

##### 02. MAPBOX: Build a raster Map 

The *raster* map now needs to be uploaded to mapbox. There are 3 things important to remember for uploading any type of raster data to mapbox.
*	Projection: `Web Mercator`
*	Bit Depth: `8 Bit / Byte`
*	If Large file upload as `BigTiff`

As we know, our *Projection* is already set as `Web Mercator`. For the `Bit Depth`, it should also be `Byte`. However, if you were trying to bring in a file that ends up giving you an output file of greater than 8 bit, you will need to resample it to 8 bit. One way is using QGIS, the other is using a simple free software such as **FIJI**, where you could just resave the image as 8 Bit. A 3rd way is using *Command Line Tools*, **GDAL**. These are explained more in detail in [Tutorial 7]. If you upload your file to mapbox and get an error regarding bit size, please refer to Tutorial 7, to proceed. **BigTiff** is an option supported by mapbox that allows you to compress your raster file for better performance. This is also explained in Tutorial 7, as it used command line tools.

Goto *Mapbox.com* and Sign into your account. Once you are on the Main Window, Under `Data > Select New Tileset`. From the window select the file you just exported. A Download status window appears. There are 2 phases of Download. After Uploading, it will provide you with a Map Id. It will then continue to *process*. This takes a few minutes, depending on file size. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872605/5abc41b4-cda7-11e5-995f-cb3f3e8228e3.png)

Once your raster is uploaded and processed, it will appear under 'Data'. Click on the `layer` and you will see all it's properies and details. The few important things to note here are:

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872606/5ac095e8-cda7-11e5-95ca-2cfa0e68476f.png)

* Map ID:
On the right corner, you will see a `Map ID`. The Map ID for my upload is: `c4sr.0jsc3bj6`. Please note your mapID as this is what will be used to reference your map.

* Zoom Extents:
This tells us at what layer extent our zooms would be possible. In some cases, there is a manual way to set this. However, if you uploaded raster data directly to mapbox, it is auto-set.

* Make Private:
The data you uploaded is *public*. This means, that anyone can use your uploaded map, through your MapID and `API Key`. By *use*, I mean call from within their application. You could choose to make your map *private* in order to avoid this. However, it is common practise to let people use your maps, styles, etc. 


##### 03. MAPBOX_STUDIO: Design New Style

In this step, we will create the `figure-groud` style that is used on the Aleppo Platform. However, instead of following this, I leave this exercise open-ended fo ryour to experiment and design your own base map. You could also make a map that uses the color template of your uploaded map. 

Go to Mapbox Main window and click on the Classic tab. In your list, select create from Mapbox Studio Classic and Click on the link. Download [Mapbox Classic](https://www.mapbox.com/mapbox-studio-classic/#darwin). Mapbox Classic is a desktop application, spaced between the we versions of Mapbox Editor and Mapbox Studio. The Studio is a great tool because it's easier to stylize in it.  

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872608/5ac68c50-cda7-11e5-9568-91c63b638dcf.png)

In your Mapbox Classic window, click on `Styles & Sources` on the lower left corner. Then Click on `New Style or Source`.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872607/5ac6bbd0-cda7-11e5-8cab-701a73ab0c5f.png)

The figure Ground Map is a variation of the `High-Contrast Map`, created by [Stamen Design](http://maps.stamen.com/toner/#12/37.7706/-122.3782). So we select this as the *style* in order to then *edit* it according to our figure-ground requirements. You can select any base style that you feel, you would need to edit. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872609/5acb6d38-cda7-11e5-9d33-07d7d340df0e.png)

As you are designing a basemap for Aleppo, I recommend going to Aleppo through `Search` or through the `Zoom In and Out` keys on the top Bar. The way the map works is using different styling for elements at different zoom levels. For instance, the road might appear as a thick line at `zoom level:19`, where as a dotted line at `zoom level: 15` and diassappear at anything above `zoom level: 12`. The window on the right of the map is for CSS, which is where all the styling components go. You can look through the different sections and change *colors / types / sizes*, etc to see how your map renders. Remember it is important to test at different zoom levels. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872610/5ace4d6e-cda7-11e5-97bb-eb4895dcf4f9.png)

In the Style tab, scroll all the way to the 'Buildings part'. Instead of adding a pattern to the buildings, we are filling the polygon as *black*. Stamen's Toner map uses *OpenStreetMaps Data*, so a *building* in OSM appears rendered with a grey striped pattern in Stamen's Toner Rendering. We now switch this to Black by adding the following line of code: `polygon-fill: #000;`

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872611/5ad90812-cda7-11e5-8f9b-317a94178d6b.png)

```css
// Buildings 

#building {
  [zoom>=14] {
  line-width: 0.5; 
  line-color: #999;
  }
  [zoom>=16] {
	line-width: 0.5; 
      polygon-fill: #000;
	//polygon-pattern-file: url('img/patterns/stripe_sm.png');
    //polygon-pattern-opacity: 0.9;
  }
  ::overlay {
    opacity: 0.05;
    }
  }
```

You can now change the appearance for any geometry.For example, if you don't want labels to show after a particular zoom, you can change the zoom settings under the `labels` tab. We made a few more changes for our Figure-Ground Map, but I leave this for you to experiment. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872612/5adfb18a-cda7-11e5-8b8d-d866e212ac43.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872614/5ae4ac4e-cda7-11e5-8359-bb3d4f9d6374.png)

Once you are happy with your *stylized map*, click on `Save As`, give it a *name* and save *locally*. Next Click on the `Settings` tab under Saved.  Here, add the *Name, Description, format and Zoom level* (as per the image below). If your map is centered at Aleppo, you will have the setting for 'center' accordingly. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872613/5ae2582c-cda7-11e5-9045-7b0072ef1b8f.png)

Now click on 'Upload to Mapbox'. Once uploaded the `Map ID`, will appear above 'Upload to Mapbox'. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872616/5b13f652-cda7-11e5-8cde-5e5d02b636f7.png)

You can now return to your mapbox window, where you will be able to see this layer under `Tabs > Classic`. You will now use this `MapID`, to make your 2 layer map. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12872617/5b1bb9e6-cda7-11e5-84a8-8614870216f5.png)


##### 04. WEB: Set Up 2 Layer Interactive

Now that you have your layers, you will use the code below to design an interactive web map that has the 2 layers, you designed. You can copy paste the code here, into sublime or you can download the packaged html files and make changes accordingly.

These are the parts that need to be changed:
*	Name Your Interactive
*	Map API: `Copy from your Mapbox Account`
*	Map ID: `This is for the individual Maps you designed`
*	Zoom Level = `What zoom Level do you want to set your map at`
* 	Long, Lat = `The center position for your map` 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12874401/9ae4e058-cdd3-11e5-9bda-edac199d4943.png)

Here's the html script. Please look at the comments, to understand the steps:

```html

<!-- Conflict Urbanism: Aleppo
     Center for Spatial Research
     Madeeha Merchant (mym2107@columbia.edu)

===========

<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />

<!-- ADD: Name to Appear on Tab --> 
<title>Interactive_Layers</title>

<meta name='viewport' content='width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no' />
<script src='https://api.tiles.mapbox.com/mapbox.js/v1.6.1/mapbox.js'></script>
<link href='https://api.tiles.mapbox.com/mapbox.js/v1.6.1/mapbox.css' rel='stylesheet' />

<style>
  body { margin:0; padding:0; }
  #map { position:absolute; top:0; bottom:0; width:100%; }
</style>
</head>
<body>

<div id='map'></div>

<script>

// ADD: Access Token from your Mapbox Account. 
L.mapbox.accessToken = 'pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A';

// ADD: Long, Lat and Zoom Level. THe settings below zoom at Aleppo
var map = L.map('map').setView([36.21, 37.15], 15);

/* ADD: Here you will add the Map IDs of the maps you have created. 
        The layers on the top are base layers. Only one base layer can be selected at a time.
        The layer below can be added with multiple other layers and have a Switch ON/OFF Check box */

L.control.layers({
    // ADD: Satellite Layer of Mapbox or any other generic mapbox Layer.
    'Satellite ': L.mapbox.tileLayer('mapbox.satellite').addTo(map),
    // ADD: Style Map you created for the Basemap. Here we are using the Figure-Ground Map
    'Streets ': L.mapbox.tileLayer('c4sr.7bbdfa09')
}, {
    //Add the Historical Map Layer. You can add as many layers as you would like.
    // If you would like the historical map to appear by default, at the end of the line, add '.addTo(map)'
    //'Historical Map': L.mapbox.tileLayer('c4sr.0jsc3bj6').addTo(map)
   'Historical Map': L.mapbox.tileLayer('c4sr.0jsc3bj6')

}).addTo(map);
</script>

</body>
</html>
```

Once you have made the changes, save the `.html` file and open with `Chrome`. You should be able to see your map with the layers option on the upper right corner. From there you should be able to select the Historical map for display. Note: There are simple tools you can add to enhance your map, such as the transparency bar. Please *comment* below and I will provide an update. Also, incase your site does not show the expected result, use Chrome Developer Tools to debug. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12874400/9ae30a94-cdd3-11e5-9bc5-c6d8fd510bb9.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12874399/9adca370-cdd3-11e5-8342-8151fcfd9c49.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12874398/9ac22a7c-cdd3-11e5-8c1b-93b17435e817.png)

##### 05. WEB: Embed Map in Case Study

Using the code, provide in [tutorial2](), you can embed any interactive website, in your case study. Test `width` and `height` ratios, to see what works best for you. Note: You will need to upload your site in order to embed it. You could test it using a locally saved .html file. If you save it in the same folder as the casestudy, just  use *filename.html*.

```html
<iframe width='100%' height='500px' frameBorder='0' src= "filename.html" name="iframe_x"></iframe> 
<p><a href="filename.html" target="iframe_x">Interactive Site</a></p>
```

### Deliverables:

Embed a 2 layer map of Aleppo, with 1 layer being the historical map and the other being a style you have designed in mapbox classic. 


### Tutorial Checklist
- [x] 01. QGIS: Export Old Map
- [x] 02. MAPBOX: Build a raster Map 
- [x] 03. MAPBOX_STUDIO: Design New Style
- [x] 04. WEB: Set Up 2 Layer Interactive
- [x] 05. WEB: Embed Map in Case Study
