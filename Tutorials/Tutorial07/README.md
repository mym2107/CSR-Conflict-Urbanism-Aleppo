######CSR / Conflict Urbanism Aleppo 
##Tutorial 07: Creating an Interactive Historical Map with Swipe

In this tutorial, you will make an interactive web map of Aleppo, that allows users to *swipe* between a current stylized *OpenStreetMaps* map and an *old* map of Aleppo, Syria. You will use the historical Soviet City Plan of Aleppo, and build it as an online map, using *mapbox*. You will then use *mapbox studio* to build a style for OpenStreetMaps. Lastly, you will then use *html, css and javascript* to design an interactive map that allows you to swipe between the 2 map layer, you created. 

### Tools:
For this tutorial, we will be using the following tools:
* [QGIS](http://www.qgis.org/en/site/)
* [Sublime](http://www.sublimetext.com/)
* [Chrome](https://www.google.com/chrome/)


### Datasets:
For this tutorial, we will be using the following datasets:
* HistoricalMapB.zip, Download [here](link to repository)
* Aleppo.zip, Download [here](link to repsotitory)
* Swipe.html, Download [here](link to repository)

  
### Datasets Overview:
This section provides detailed explanation of each data source. You can skip this section, if you would like to continue with the tutorial. However, it is recommended that you familiarize yourself with these sources, as they will asssist you in your research.

##### Data set: Soviet City Plan of Haleb (Aleppo), Syria:
Title: Digital Raster Graphics (DRGs) of Russian Military Topographic City Plan : Soviet City Plan of Haleb (Aleppo), Syria
Published: 	Colorado, USA,: LAND INFO Worldwide Mapping, LLC, 1985
This dataset has been provided here by [the Aleppo Project](http://ccnr.ceu.edu/thealeppoproject). As a course student, the georeferenced maps are on your shared Drive. If you are not a student in the course or collaborator, you can email us, to request access, or you can use the *jpeg* files and georeference them. 

##### Data sets: CSR Repository Images

You can use the High Resolution Satellite Imagery or Maps. In this example, we are using a map that was georeferenced and projected. The steps are similar, when you use Satellite Imagery. 


### Creating an Interactive Historical Map

##### Steps:
  * 01. QGIS: Export Old Map
  * 02. MAPBOX: Build a raster Map 
  * 03. MAPBOX_STUDIO: Design New Style
  * 04. WEB: Set Up 2 Layer Interactive
  * 05. WEB: Embed Map in Case Study


##### 01. QGIS: Export Old Map

Download the folder, AleppoHistoricalMap.zip and *browse* the contents. You will see the following files. 
*	Full Raw
	*	Haleb_(Aleppo)1.tif
	*	Haleb_(Aleppo)2.tif 
*	GeoWGS84
	* 	Haleb_(Aleppo).tif
	*	Haleb_(Aleppo).tfw
	*	Haleb_(Aleppo).prj

Open the QGIS Application and Open these files using: `Menu > Layer > Add Layer > Add Raster layer` and *browse* to the individual files. Likewise, you can always *drop* the file directly into the `map window`.  

When you bring in the layer: GeoWSG84: Haleb_(Aleppo).tif, remember it's projection is already set. You can recheck the CRS by going to the layer in the Layers Panel and Right Click on it. Goto: `Properties > General > Coordinate Reference System : EPSG:4326 - WSG 84`. To be able to bring the raster data as a map, you will need to reset this to Web Mercator (as shown in the next step). 

t5-4
![Add Layer](link)

When you bring in *raster* data to QGIS, it is important that you recheck its *georeferecing* and *projection*. If something looks wrong in the map window, it will 100% not work in mapbox. To test it's precision, either add a georeferenced image of a know area. Or you can bring in the underlay of a satellite image. To do this Goto : `Menu > Web > OpenLayersPlugin > Google Maps > Google Satellite`. Zoom into the area of the citadel (center Aleppo) and see how it overlaps with the satellite data. If your image does not appear, it might be due to internet speed. You can select `OSM/Stamen > Stamen Toner / OSM` in that case. 

t5-6
![Add Layer](link)

Look at different parts of the image you brought in and the underlying OSM map to see if they overlap well. Sometimes, raster images are not georeferenced properly and might have minor offsets that need to be manually fixed. You can change the `order` of the layers by dragging the `Stamen Toner / OSM` below. Then `Right Click` on Properties of the Haleb (Aleppo) layer and set `Transparency` at 70%. You will now be able to test the overlap better.

t5-7
![Add Layer](link)

Now, you will need to export the layer in a format that is acceptable to mapbox. Please remember mapbox only uses the `Projection: Web Mercator`. So you will need to export the image as a *geotiff* and also reproject it to WebMercator. To do this, `Right Click` on the Layer in `Layers Panel`, Right Click: `Save As`. In the `Save raster layer as` window, set the following:

*	Format: GTiff
*	Save As: AleppoOldMap
*	CRS > Change > Opens `Coordinate reference system selector`
*	Select *WGS 84 / Psuedo mercator, EPSG: 3857
* 	Save the file in your selected format (Takes a while!)

t5-7
![Add Layer](link)

Note: You can skip the above section and directly use the file: Haleb_(Aleppo).tif from the downloaded folder.

##### 02. MAPBOX: Build a raster Map 

The *raster* map now needs to be uploaded to mapbox. There are 3 things important to remember for uploading any type of raster data to mapbox.
*	Projection: `Web Mercator`
*	Bit Depth: `8 Bit / Byte`
*	If Large file upload as `BigTiff`

To do these, you will need to become familiar with Coomand Line Tools. They are NOT as hard as they sound. On a MAC system, you will ned to open Terminal. You can Navigate to these, using the Search Bar. A key point for Command Line Tools is knowing where your files are. I suggest making a folder on desktop and naming it tutorial7. Then in your terminal window type:

> cd desktop

This will take you to the desktop folder on your computer. Now to go to the folder, type cd tutorial7

> cd tutorial7

You can type 'ls' for list to see the contents of the folder.

> ls

You need to install GDAL, prior to this exercise. Please see my notes at the end of the section. However, if you downloaded QGIS, you most likely had to download GDAL, without being specifically asked to. As a result the chances are it's on your computer. You can test the next step. If Terminal responds saying GDAL command not known, please follow the instructions to download GDAL and then return to this section.

**GDALINFO**
If you type in gdalinfo filename.ext, you will get all the information about your stored file. You should make sure your file is within the same folder or else you will have to add the correct filepath. gdalinfo provides details on everything: projection, image size, bit depth. When you run the following command, you can verify the details on the image prior to mapbox upload.

> gdalinfo Alp.tif

Here's waht gdalinfo returned. Please make note of the following parts in your gdalinfo output

*	Size: 29426, 16165
*	Coordinate System: Authority: AUTHORITY["EPSG","4326"]]
*	Band 1 Block=29426x1 Type=Byte, ColorInterp=Palette

```
i-a@Madeehas-MacBook-Pro:~/desktop/Tutorial7$ gdalinfo Alp.tif
Driver: GTiff/GeoTIFF
Files: Alp.tif
Size is 29426, 16165
Coordinate System is:
GEOGCS["WGS 84",
    DATUM["WGS_1984",
        SPHEROID["WGS 84",6378137,298.257223560493,
            AUTHORITY["EPSG","7030"]],
        AUTHORITY["EPSG","6326"]],
    PRIMEM["Greenwich",0],
    UNIT["degree",0.0174532925199433],
    AUTHORITY["EPSG","4326"]]
Origin = (37.085438877230487,36.242935195238431)
Pixel Size = (0.000005736305177,-0.000005736305177)
Metadata:
  AREA_OR_POINT=Area
Image Structure Metadata:
  COMPRESSION=PACKBITS
  INTERLEAVE=BAND
Corner Coordinates:
Upper Left  (  37.0854389,  36.2429352) ( 37d 5' 7.58"E, 36d14'34.57"N)
Lower Left  (  37.0854389,  36.1502078) ( 37d 5' 7.58"E, 36d 9' 0.75"N)
Upper Right (  37.2542354,  36.2429352) ( 37d15'15.25"E, 36d14'34.57"N)
Lower Right (  37.2542354,  36.1502078) ( 37d15'15.25"E, 36d 9' 0.75"N)
Center      (  37.1698371,  36.1965715) ( 37d10'11.41"E, 36d11'47.66"N)
Band 1 Block=29426x1 Type=Byte, ColorInterp=Palette
  Color Table (RGB with 256 entries)
```

`Coordinate System: "EPSG","4326"` confirms the projection of your input data. 
`Type: "Byte"` confirms that the bit depth is 8 bit

If both of these are `TRUE`, you can skip the next two steps. 
However, if they aren't, you can use **GDAL** to change according to Mapbox reqiorements.

**To change Projection:**

Use the below code command at the Command Line, after:
*	Switch the file names
*	Use the projection you were provided through GDAL, instead of EPSG:4326

`-s_srs means` “source spatial reference system” - this is the projection that the flle you are starting with is stored in.

`-t_srs` means “target spatial reference system” - this is the projection that you want to convert the datasource to. For any raster file you want to use with Mapbox this should be EPSG:3857.

`-r` bilinear is telling the program what resampling interpolation method to use. If you want the command to run faster and don’t mind a rougher-looking output, choose near instead of bilinear. If you don’t mind waiting longer for very high-quality output, choose lanczos.

`-te` -20037508.34 -20037508.34 20037508.34 20037508.34 is telling the program the desired “target extent” of our output file.

'''
gdalwarp -s_srs EPSG:4326 -t_srs EPSG:3857 -r bilinear -te -20037508.34 -20037508.34 20037508.34 20037508.34 ActualImage.tif NewImage.tif
'''

For more details: [GDALWarp](http://www.gdal.org/gdalwarp.html)

**To change Bit Depth:**

If your image is `16 bit`, you will need to downsample it to `8 bit` to use with Mapbox, using GDALTranslate.

# Converting from 16bit to 8bit
```
gdal_translate -ot Byte -scale 0 65535 0 255 inputfilename.tif outputfilename.tif
```

For more details: [GDALTranslate](http://www.gdal.org/gdal_translate.html)

**To Convert to BIGTIFF**

You can create a [BigTIFF](http://www.awaresystems.be/imaging/tiff/bigtiff.html) using the command line raster utility, `gdal_translate` (using GDAL version >= 1.5.0). For more information, here's Mapbox's [explanation](https://www.mapbox.com/blog/bigtiff-upload-support). 

```
gdal_translate -of GTiff -co BIGTIFF=YES -co TILED=YES -co COMPRESS=LZW original.jp2 bigtiff.tif
```

The `-of` flag stands for "output format". The above command is setting the output to GeoTIFF.

The `-co` flag stands for "creation option". The above command is passing the `BIGTIFF` option to the output format driver to create a `BigTIFF`. The `TILED` command breaks the image up into square tiles. Pre-cutting high-res imagery into tiles can make accessing and processing that image more efficient. Also, the `COMPRESS` command helps decrease the overall filesize.

Goto *Mapbox.com* and Sign into your account. Once you are on the Main Window, Under `Data > Select New Tileset`. From the window select the file you just exported. A Download status window appears. There are 2 phases of Download. After Uploading, it will provide you with a Map Id. It will then continue to *process*. This takes a few minutes, depending on file size. 

TX-13
![Add Layer](link)

Once your raster is uploaded and processed, it will appear under 'Data'. Click on the `layer` and you will see all it's properies and details. The few important things to note here are:

TX-14
![Add Layer](link)

* Map ID:
On the right corner, you will see a `Map ID`. The Map ID for my upload is: `c4sr.0jsc3bj6`. Please note your mapID as this is what will be used to reference your map.

* Zoom Extents:
This tells us at what layer extent our zooms would be possible. In some cases, there is a manual way to set this. However, if you uploaded raster data directly to mapbox, it is auto-set.

* Make Private:
The data you uploaded is *public*. This means, that anyone can use your uploaded map, through your MapID and `API Key`. By *use*, I mean call from within their application. You could choose to make your map *private* in order to avoid this. However, it is common practise to let people use your maps, styles, etc. 


##### 03. MAPBOX_STUDIO: Design New Style


In this step, we will reuse a 'pencil sketch' style. However, instead of following this, I leave this exercise open-ended for you to experiment and design your own base map. You could also make a map that uses the color template of your uploaded map. 

Go to Mapbox Main window and click on the Classic tab. In your list, select create from Mapbox Studio Classic and Click on the link. Download [Mapbox Classic](https://www.mapbox.com/mapbox-studio-classic/#darwin). Mapbox Classic is a desktop application, spaced between the we versions of Mapbox Editor and Mapbox Studio. The Studio is a great tool because it's easier to stylize in it.  

TX-15
![Add Layer](link)

In your Mapbox Classic window, click on `Styles & Sources` on the lower left corner. Then Click on `New Style or Source`.

TX-16
![Add Layer](link)

Select the pencil sketch map here in your Style&Source window. For more information on the method, read [here](https://www.mapbox.com/blog/pencil-drawn-style/). We select this as the *style* in order to then *edit* it according to our requirements. 

TX-17
![Add Layer](link)

As you are designing a basemap for Aleppo, I recommend going to Aleppo through `Search` or through the `Zoom In and Out` keys on the top Bar. The way the map works is using different styling for elements at different zoom levels. For instance, the road might appear as a thick line at `zoom level:19`, where as a dotted line at `zoom level: 15` and diassappear at anything above `zoom level: 12`. The window on the right of the map is for CSS, which is where all the styling components go. You can look through the different sections and change *colors / types / sizes*, etc to see how your map renders. Remember it is important to test at different zoom levels. 

Once you are happy with your *stylized map*, click on `Save As`, give it a *name* and save *locally*. Next Click on the `Settings` tab under Saved.  Here, add the *Name, Description, format and Zoom level* (as per the image below). If your map is centered at Aleppo, you will have the setting for 'center' accordingly. 
Note: For this tutorial, I just renamed the style and used it. You are welcome to experiment with textures or colors.

Now click on 'Upload to Mapbox'. Once uploaded the `Map ID`, will appear above 'Upload to Mapbox'. 
TX-23
![Add Layer](link)

You can now return to your mapbox window, where you will be able to see this layer under `Tabs > Classic`. You will now use this `MapID`, to make your 2 layer map. 

TX-25
![Add Layer](link)


##### 04. WEB: Set Up 2 Layer Interactive

Now that you have your layers, you will use the code below to design an interactive web map that has the 2 layers, you designed. You can copy paste the code here, into sublime or you can download the packaged html files and make changes accordingly.

These are the parts that need to be changed:
*	Name Your Interactive
*	Map API: `Copy from your Mapbox Account`
*	Map ID: `This is for the individual Maps you designed`
*	Zoom Level = `What zoom Level do you want to set your map at`
* 	Long, Lat = `The center position for your map` 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12874495/5632831e-cdd5-11e5-8d1f-c3fa3c1fd726.png)

Here's the html script. Please look at the comments, to understand the steps:

```html

<!-- Conflict Urbanism: Aleppo
     Center for Spatial Research
     Madeeha Merchant (mym2107@columbia.edu)

================================================================= -->

<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />

<!-- ADD: Name to Appear on Tab --> 
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

//ADD: Access Token from your Mapbox Account 
L.mapbox.accessToken = 'pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A';

var map = L.mapbox.map('map');

// ADD: Layer 1 : Here we add the Pencil Style we are using
L.mapbox.tileLayer('c4sr.8a769a77').addTo(map);

// ADD: Layer 2 : Here we add the Soviet Historical Map of Aleppo
var overlay = L.mapbox.tileLayer('c4sr.8a769a77,c4sr.6b61i4ek').addTo(map);
var range = document.getElementById('range');

//Do NOT Change
function clip() {
  var nw = map.containerPointToLayerPoint([0, 0]),
      se = map.containerPointToLayerPoint(map.getSize()),
      clipX = nw.x + (se.x - nw.x) * range.value;

  overlay.getContainer().style.clip = 'rect(' + [nw.y, clipX, se.y, nw.x].join('px,') + 'px)';
}

range['oninput' in range ? 'oninput' : 'onchange'] = clip;
map.on('move', clip);

// ADD: Long, Lat and Zoom Level. The settings below zoom at Aleppo
map.setView([36.21, 37.15], 14);


clip();
</script>
</body>
</html>
```

Once you have made the changes, save the `.html` file and open with `Chrome`. You should be able to see your map with the layers option on the upper right corner. From there you should be able to select the Historical map for display. Note: There are simple tools you can add to enhance your map, such as the transparency bar. Please *comment* below and I will provide an update. Also, incase your site does not show the expected result, use Chrome Developer Tools to debug. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12874497/5901f516-cdd5-11e5-8f9d-5186c83dceed.png)

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12874500/5cdd3182-cdd5-11e5-9773-f3e7f3f34f02.png)

```
var overlay = L.mapbox.tileLayer('c4sr.8a769a77,c4sr.6b61i4ek').addTo(map);
```

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12874496/57b93fc0-cdd5-11e5-8445-1fa790271631.png)


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
