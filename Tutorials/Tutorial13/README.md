######CSR / Conflict Urbanism Aleppo 
##Tutorial 13: UNOSAT Processing Animation

In this tutorial, you will be making a simple interactive animation of UNOSAT data. You will create this animation in the [Processing](https://processing.org) programming language. Processing is a free, (relatively) intuitive, easy-to-learn software sketchbook that allows us to create interactive graphics. While this tutorial is attempting to be accessible to all - it is not within the scope of this course or this tutorial to teach the fundamentals of computer science. Some prior experience with a comparable object oriented programming language (Python, C#, Javascript, etc.) is recommended, but not required.

A quick word of advice before getting started: if you ever get stuck with an error in your code, google your error. It is amazing how helpful crowd sourced solutions, like those on [stackoverflow](http://stackoverflow.com), are.

### Tools:
For this tutorial, we will be using the following tools:
* TextEdit / Notepad (or your favorite text editor)
* [Processing](https://processing.org)
* [Adobe AfterEffects](http://www.adobe.com/products/aftereffects.html)

NOTE: We will only use AfterEffects at the very end to turn our frames into an animation. If you don't have AfterEffects, don't worry. You can download a free trial or use the software on a school computer. Alternatively, Adobe Photoshop is one of many viable software alternatives to convert frames into an animation.


### Datasets:
For this tutorial, we will be using the following datasets:
* UNOSAT.zip, Download [here](https://www.dropbox.com/s/3dha98zai4wtcxg/UNOSAT.zip?dl=0)
* [Processing Tutorial Package](https://drive.google.com/open?id=0BxbL3W9pPVTtcXc4ZDN2dVhWWms)

  
### Datasets Overview:
This section provides detailed explanation of each data source. You can skip this section, if you would like to continue with the tutorial. However, it is recommended that you familiarize yourself with these sources, as they will asssist you in your research.

**NOTE: For the purpose of this tutorial, you are provided with a UNOSAT dataset of Aleppo in a .CSV format. You are, however, welcome to create your own .CSV from the UNOSAT shapefile by following Steps 1 and 2 of [Tutorial 9](https://github.com/mym2107/CSR-Conflict-Urbanism-Aleppo/blob/master/Tutorials/Tutorial09/README.md).**

##### Dataset 1:
**Humanitarian Data Exchange**, [HDX](https://data.hdx.rwlabs.org) is a good place for open data as it presents a *consolidated repository* of data collected through multiple sources. The goal of the Humanitarian Data Exchange (HDX) is to make humanitarian data easy to find and use for analysis. If you are interested in exploring datasets from multiple Humanitarian Agencies, it is recommended that you register yourself on the HDX website. You can select regions and organisations of interest and explore the vast collection of datasets. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/13027498/786cd4b2-d252-11e5-90bc-74a7e2824e24.png)

You can search for *UNOSAT - UNITAR Aleppo - Damage assesment Aleppo*. Make sure you use the most recent file. (As of now, that is Data for May 2015). 

We will be using the following files from HDX:
* UNOSAT_DamageAssesment_OFDA-REACH_CE20130604SYR_shp.zip

*Geodata of Damage Assessment of Aleppo, Aleppo Governorate, Syria*
This map illustrates satellite-detected damage in a portion of the city of Aleppo, Syrian Arab Republic. Using satellite imagery acquired 01 May 2015, 26 April 2015, 23 May 2014, 23 September 2013, and 21 November 2010, UNITAR - UNOSAT identified a total of 5,170 affected structures within the extent of this map. Approximately 904 of these were destroyed, 2,641 severely damaged, and 1,625 moderately damaged. The city-wide analysis of Aleppo revealed a total of 14,034 affected structures, of which 2,878 were destroyed, 6,879 severely damaged, and 4,277 moderately damaged. While much of the city was damaged by 23 May 2014, 5,567 structures were newly damaged and 90 structures experienced an increase in damage between that date and 01 May 2015. This analysis was done of the REACH initiative for the U.S. Office of Foreign Disaster Assistance. This is a preliminary analysis and has not yet been validated in the field. Please send ground feedback to UNITAR - UNOSAT.

HDX provides additional information on each data source including *layers*, *data source* and *contributor*. It often provides data in *multiple formats*. If you prefer to work in [ArcGIS](https://www.arcgis.com), you are welcome to download the geo database (`.gdb file`). 

Likewise, UNITAR/UNOSAT maintains a good repository on their site and frequently updates the data that can be accessed [here](http://www.unitar.org/unosat). The data is all made available on HDX, which is likely where you will download from, but you can always check UNITARs site to see if they have an update. 


### Tutorial Title: UNOSAT Processing Animation

##### Steps:
  * 01 TEXTEDIT: Explore UNOSAT dataset
  * 02 PROCESSING: "Hello world"
  * 03 PROCESSING: Load UNOSAT data
  * 04 PROCESSING: Display UNOSAT data
  * 05 PROCESSING: Animate UNOSAT data
  * 06 PROCESSING: Display damage data on each data point
  * 07 PROCESSING: Add context and export animation frames
  * 08 AFTEREFFECTS: Compile frames into animation

##### 01. TEXTEDIT: Explore UNOSAT dataset

Let's first open up our UNOSAT dataset to see what we're working with. If you haven't already, download the zipped project folder in the Datasets section above. Open the folder and find the file named "UNOSAT_Processing.csv". Open this file in your favorite text editor. You'll see the following:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902308/4b115d60-ee1a-11e5-9592-9cbdaaa386a5.png)

You may also open the csv in Excel for a cleaner viewing experience. The data presented here is a slightly modified version of the UNOSAT attribute table taken from the shapefile at the address provided above. Just to reiterate the above, this data essentially tells us how severly buildings/data points are damaged over 3 different sensor dates/periods. Buildings that are identified in the first sensor period, 9/23/13, are checked again in subsequent sensor periods. Many data points do not appear until the third sensor period. Thus these buildings do not have damage assocaited with them in the first two sensor periods as they were not damaged or identified until the most recent sensor period. We will have to remember this once we are coding in order to show the correct data.

For a description on how this dataset is modified from the given UNOSAT attribute table, consult the following. The modifications are the additional data columns added after the blank "_" data column. These new fields are "SENSORGROUP", "Long", "Lat", "MainDamageNum", and "MainDam_2Maxd". The "SENSORGROUP" simply tells in which sensor period the data point first appears. So, if a data point is first recorded in the second sensor date period this value would be 2. "Long" and "Lat" are simply the latitutde and longitude of the data point extracted for convenience from the first column "wkt_geom". "MainDamageNum" converts the "Main_Damag" column to numbers where 1=Destroyed, 2=Severely Damaged and 3=Moderately Damaged. This is done to keep the dataset consistent as the other sensor groups damage columns, "Main_Dam_1" for the second sensor group and "Main_Dam_2" for the third sensor group, are in this numeric form. And finally, the "MainDam_2Maxd" column removes a few errors from the "Main_Dam_2" column where a few values are not coded correctly.


##### 02. PROCESSING: "Hello world"

Now it's time to get into the fun stuff - the code. If you haven't already, go to [Processing's website](https://processing.org) to download and install the software. Processing is available for free for both PC and Mac. If you are familiar with Processing, you may skip this section covering the basics and proceed to Step 03.

After installing, open Processing and you should be greated by the following:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902322/4b234160-ee1a-11e5-806b-de6ab0b01624.png)

This blank file is where we will write our brilliant code. The play button at the top of the window runs whatever code we write and the stop button stops that code. After we hit play, the code runs until we hit the stop button and explicitly tell Processing to stop. The black space at the bottom of the window is the console. This is where Processing reports errors or prints messages to us. To start and get ourselves familiar with Processing, let's execute an extremely simple program. Let's have Processing say, "Hello World". Before we start coding, know that everyone is sure to mess up somewhere along the way, so please save frequently.

In the Processing window, write the following lines of code (the grey code on the lines with "//" is commented code for your convenience, you do not need to copy it but it is STRONGLY ENCOURAGED that you comment your own code so you can figure out what the heck you were doing after a few days break):

```Processing
void setup()
{
    // Here we write the lines of code that we want to complete
  	// before the computer draws anything on our 
  	// digital canvas. Code here is only executed once by the
  	// computer.
  	// Here, for example, we will load the data from our CSV
    println("Hello World");
}
    
void draw()
{
    // Here we write the lines of code that we want to execute
  	// while the computer draws on our digital canvas. Code here
 	// is executed continuosly by the computer.
 	// Here, for example, we will draw, or display, the UNOSAT
 	// lat long data as circles.
}
```

Ok, let's digest what we just wrote before we run it. We have two sections of our code, ```void setup()``` and ```void draw()```. Any code that we write between the {} brackets after ```void setup()``` is the code that we want to run when the program or sketch is starting up. This code is only executed once. This, for example, is a good place to load data from an external data file, like our CSV, into Processing. We put it in setup because we don't need to load the data more than once. Any code that we write between the {} brackets after ```void draw()``` is the code we want to run continuously while our sketch is playing. This code is executed many times per second.

So, in the code we just wrote, Processing will print the text string "Hello World" in its console once. And that's it. ```println()``` prints any string between it's () brackets in Processing's console at the bottom of the window. And since ```println("Hello World")``` is in the setup section of our code, Processing will only print the string once.  Let's press play and make sure it works.

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902320/4b208d80-ee1a-11e5-8b64-0cb386086b98.png)

Woo! Our first sketch! The grey window that popped up displays anything Processing draws on screen. Since we did not draw anything, the window is blank. And the console has our text, "Hello World". You can press the stop button now.

If we move the line of code ```println("Hello World")```, to the draw section of our code, we get a slightly different result. Your code, excluding comments, should look like:

```Processing
void setup()
{

}
    
void draw()
{
	println("Hello World");
}
```

and the output looks like this:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902319/4b1efbdc-ee1a-11e5-9111-f47b9136a2a1.png)

Notice that Processing keeps printing "Hello World" in the console. This is because our ```println()``` function is now in the draw section of our code. So Processing is executing this line of code as often as it can, something like 60 times per second. Every second, Processing prints "Hello World" 60 times in the console. You'll also notice that the grey window that pops up is still blank - that's ok. We still haven't told Processing to draw anything in that window.

Ok, great. Let's make things a little bit more exciting and actually draw something in the window. Let's write some code to draw a circle under our mouse as we move it around the window. The code is simply:

```Processing
void setup()
{
	// tells processing how big to make our window
  	size(600,600); 
}
    
void draw()
{
  	// draws a circle of pixel radius 10 centered about the mouse's X
  	// and Y position in the window
  	ellipse(mouseX, mouseY, 10,10);
}
```

Run the code by pressing play and move your mouse across the window.

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902321/4b21e306-ee1a-11e5-827c-af56fdaf4f26.png)

Cool! Every time the code in draw runs, it places a circle of radius 10 under the pointer's X and Y cooridnates (```mouseX``` and ```mouseY```) in the Processing window. If we only want one circle to display under the current mouse's position in the window, we need only add one line of code in our draw section:

```Processing
void setup()
{
    // tells processing how big to make our window
  	size(600,600); 
}
    
void draw()
{
	// draws a black background on the window
    background(0);
      
  	// draws a circle of pixel radius 10 centered about the mouse's X
  	// and Y position in the window
  	ellipse(mouseX, mouseY, 10,10);
}
```

Now, everytime the code in draw runs, a black background covers up all of the old circles so we only see the most recent one in our window. To explore the full range of funcitons like ```ellipse()``` and ```println()``` that come with Processing, refer to the reference page [here](https://processing.org/reference/). You can also create your own functions.

That's it! Now that you have the Processing fundamentals under your belt, let's work on getting our UNOSAT data into Processing. 

##### 03. PROCESSING: Load UNOSAT data

Lucky for us, Processing comes with some built in functionality to read data in a CSV. Let's start with a new file. Name it whatever you' like. In order for Processing to read our CSV, we must move the CSV into the same folder as your new Processing sketch. Let's now write some code to read the csv:

```Processing
//Global variable to hold csv table
Table unosatTable;

//Global variable to store number of rows
int totalRowCount;

void setup()
{ 
  //Loads the CSV into a table
  unosatTable = loadTable("UNOSAT_Processing.csv", "header");
  
  //Finds the total number of rows containing data excluding the header
  totalRowCount = unosatTable.getRowCount();
  println(totalRowCount + " total rows in table");
}

void draw()
{
  //Drawing code
  
}

```

You'll notice that there are two variables placed above the setup code. These variables are global variables, meaning they are data that can be accessed in any section of our code. The ```unosatTable``` variable is of the type, Table, it's a built in data type that makes it easier for us to put csv data into processing. The second, ```totalRowCount```, variable is an integer (..-2, -1, 0, 1, 2,..). It can hold any integer value. Right now it is not set to any integer but we will use this variable to store the total number of rows in our dataset.

In the ```void setup()``` portion of our code, the first line of code reads the data from our csv and places it into our ```unosatTable``` variable. Now the rows and data from the csv exist in a form that Processing can interact with! Next, we use a Processing method ```.getRowCount()``` on ```unosatTable``` to determine the total number of rows. We store this integer in our ```totalRowCount``` variable. The last line of setup code simply prints the total number of rows in the console. If you ever want to check what is going on under the hood of your code, it is helpful to print values to the console and check them manually.

Run the code and you should see that there are 14058 rows in the Processing console.

**NOTE: The above code is zipped as Processing sketch loaddatav01 for your convenience.**

Great - so Processing has the data in this table variable but right now it's not doing a lot with it. It's just telling us how many rows of data the table variable contains. Let's put Processing to some more use by storing the relevant data in lists. If you are not familiar with lists, do some quick googling. Essentially, lists can contain many pieces of information. We could have a list of integers like ```[1,2,3,769,-3]``` or a list of decimal or floating point numbers like ```[0.91, 189.0, 0.5, 7.8, 9.1, 2.0]```. We can have a list of strings or a list of lists. Lists are a very powerful datatype. With lists, it is important to know how to index a list. When we index a list, we reference one value from that list. So, for example with the list called ```myList``` where ```myList = [1,2,3,769,-3]```, an index of 0 would return the first value in the list, ```1```. In Processing, we write this as ```myList[0]```. Similarly, an index of 3 would return the fourth value in the list, ```myList[3] = 769```. We will use indexes in our animation to reference multiple dimensions of one datapoint.

Let's create a list for each column of data in the csv that we would like to reference. In Processing, we need to tell the lists how long we want them to be. Luckily, we have our ```totalRowCount``` variable from above that is telling us how many rows of data we have. We should make each list as long as there are rows of data. We do that in the following:
```Processing
Table unosatTable;

int totalRowCount;

//Lists to store the relevant
float[] latList;
float[] longList;
int[] damageList1;
int[] damageList2;
int[] damageList3;

void setup()
{
  //Setup code
  
  //Loads the CSV into a table
  unosatTable = loadTable("UNOSAT_Processing.csv", "header");
  
  //Finds the total number of rows containing data excluding the header
  totalRowCount = unosatTable.getRowCount();
  println(totalRowCount + " total rows in table");
  
  //Creates lists for each column of data we'd like to import
  latList = new float[totalRowCount];
  longList = new float[totalRowCount];
  damageList1 = new int[totalRowCount];
  damageList2 = new int[totalRowCount];
  damageList3 = new int[totalRowCount];
}

void draw()
{
  //Drawing code
}
```

You'll see that we create five lists as global variables before the setup portion of our code. The first two lists, ```float[] latList``` and ```float[] longList``` are two lists that will contain floating point numbers. The first will store the latitude of each point and the second list will store the longitude. The other three lists, ```int[] damageList1```, ```int[] damageList2```, and ```int[] damageList3``` are lists of integers. They store the numeric value of how damaged a specific location was in sensor period 1, 2 and 3 respectively.

We've just created the lists as global variables but we haven't told each list how long we want it to be. We do this in the setup portion of the code after we know how many rows of data there are. Observe the line of code, 
```Processing
latList = new float[totalRowCount];
```
This line of code tells latList that it should be a list of length ```totalRowCount```, i.e. a list of length 14058 since ```totalRowCount``` = 14058. We do this for each of the 5 lists.

**NOTE: The above code is zipped as Processing sketch loaddatav02 for your convenience.**

We have lists that are correct length to store data but they are empty right now. Next, we need to move the data from our ```unosatTable``` variable into our respective lists. To do so, we will utilize a loop, specifically a for loop.

First you'll notice that we've added a 6th list of integers called ```sensorGroup```. This list tells us in which sensor period the data point was first identified. 

```Processing
Table unosatTable;

int totalRowCount;

float[] latList;
float[] longList;
int[] damageList1;
int[] damageList2;
int[] damageList3;
int[] sensorGroup;

void setup()
{
  //Setup code
  
  //Loads the CSV into a table
  unosatTable = loadTable("UNOSAT_Processing.csv", "header");
  
  //Finds the total number of rows containing data excluding the header
  totalRowCount = unosatTable.getRowCount();
  println(totalRowCount + " total rows in table");
  
  //Creates lists for each column of data we'd like to import
  latList = new float[totalRowCount];
  longList = new float[totalRowCount];
  damageList1 = new int[totalRowCount];
  damageList2 = new int[totalRowCount];
  damageList3 = new int[totalRowCount];
  sensorGroup = new int[totalRowCount];
  
  int rowCount = 0;
  //Loops through each table element and sets the ith value in the corresponding table
  for(TableRow row : unosatTable.rows()) 
  {
    latList[rowCount] = row.getFloat("Lat");
    longList[rowCount] = row.getFloat("Long");          
    damageList1[rowCount] = row.getInt("MainDamageNum");  
    damageList2[rowCount] = row.getInt("Main_Dam_1");
    damageList3[rowCount] = row.getInt("Main_Dam_2Maxd");
    sensorGroup[rowCount] = row.getInt("SENSORGROUP");
    
    //test println 
    println(sensorGroup[rowCount] + ", " + rowCount);
    
    //Iterate through length of the lists
    rowCount = rowCount + 1;
  }
}

void draw()
{
  //Drawing goes here
}
```

The important new additions to the code start with the ```int rowCount = 0;``` line. We use a for loop to step through every row in our ```unosatTable```. We then take each portion of data of interest and set it in the appropriate list using the header name of the desired column to fetch the desired value. Since, for example, in our csv, latitude is stored in a column named "Lat" we take this value and store it in the ```latList```.

The integer variable ```rowCount``` allows us to step through each value in our lists that are length ```tableRowCount```. If ```rowCount = 0``` always, we would only ever be putting data from the ```unosatTable``` variable into the first value of our lists, rewriting data and not appropriately filling the list. We use ```rowCount``` to iterate through the length of the list so that the second value will be put in the rowCount = 1, or second place in our list, the third value will be put in the third value of our lists, etc. (It's important to note that in Processing, index 0 is the first value, index 1 is the second value, etc.)

Lastly, the line,
```Processing
   //test println 
   println(sensorGroup[rowCount] + ", " + rowCount);
   ```
Is simply for our convenience to verify that the code is stepping through the lists correctly. This line prints the current sensorGroup and rowCount value to the console.

**NOTE: The above code is zipped as Processing sketch loaddatav03 for your convenience.**

We now have all of the data we'll need to create our animation loaded into lists in Processing. To review, the first row of data from our CSV is now distributed across 6 lists. Each list can be easily queried such that if we want to know the 895th's data points lat long we need only write ```latList[894];```. In the next step of this tutorial we will actually display the UNOSAT data in our canvas window. We will iterate through the length of our lists to display each point sequentually using loops inside of the draw portion of our code.

##### 04. PROCESSING: Display UNOSAT data

Now that our code is starting to become a little bit longer, we will no longer be pasting the entirety of the code here. To follow along, please refer to the zipped sketches you downloaded above. For this following segment, refer to the sketch called **DisplayDatav01**. Please open this sketch and follow along.

The first thing you'll notice scrolling through the new code are ```line 12 - line 16``` of the sketch:
```Processing
//Lat long extents of underlay Aleppo Map
float long1 = 37.0755910328;
float long2 = 37.270195015;
float lat1 = 36.2616902128;
float lat2 = 36.1192872988;
```

These define the upper left hand and lower right hand coordinates of our desired map extents. In the dataset, we were given lat long coordinates of each data point. In order to display these in our canvas window we need to convert them proportinally to the extents of the window. If you think about it, a lat long coordinate of 37.1, 36.2 does not mean much to Processing if there are no reference points. The above lines of code simply provide us with two reference points so that we can locate the data with respect to these corners. If we consider the upper left hand corner of the map extents the upper left hand corner of our window and the lower right hand corner of the map extents the lower right hand corner of the window, we can proportionally place our data points between these two points within the rectangle that is our canvas window. This is how we will place the data on our sketch's "map".

The next few lines of code you'll see are ```line 21 - line 22``` that simply tell processing that we would like our window to be 740 x 542 pixels and that we would like to run through the draw code 10 times per second.

Now that we're into the setup section of our code, we need to scale or map our data from its lat long coordinates to some pixel distance in our window. This is done on ```line 57 - line 66```

```Processing
	//Remap the lat long of each row entry based on extents of our image
	for(int i=0; i<totalRowCount; i++)
	{
    	println(latList[i] + ", " + longList[i] + ", "+  i);
    	latList[i] = map(latList[i], lat1, lat2, 0, height);
    	longList[i] = map(longList[i],long1, long2, 0, width);
    
    	//text print new lat long
    	println(latList[i] + ", " + longList[i] + ", "+  i);
  	}
```

Let's go through the code line by line. The for loop at the beginning iterate through every value in our lists where the current value is the ```ith``` value. The first line in the loop prints the given lat long that we read from the CSV. The following two lines map the given latitude and longitude based on the upper left hand corner and lower right hand corner of the map to window height and width. A given value that was in the middle of our map extents will now be displayed in the middle of the window. A given value that was in the bottom right hand corner of the map extents is now in the bottom right hand corner of our window. The last line of code prints the new lat long in the console. After the for loop steps through all of the values in our lists we have mapped the given lat long to pixel dimensions that Processing can display!

Let's display these data points by drawing circles around each lat long data point. Observe the draw section of the code:

```Processing
void draw()
{ 
  //Which sensor group would we like to display data from
  int currentSnsrGrp = 3;
  
  //loop through all of the data and draw an ellipse whereever there is a data point
  for(int i=0; i<totalRowCount; i++)
  {
    //Only draw an ellipse if it has data in the current sensor group
    if(currentSnsrGrp >= sensorGroup[i])
    {
      ellipse(longList[i], latList[i], 10,10);
    }
  }
}
```

Recall that the code in draw runs continuosly so the code above will keep running until we hit stop. Eventually, we would like the user to be able to control which sensor group they are viewing in the canvas window but for now let's hard code this value as ```int currentSnsrGrp = 3;```. We can manually change this value to either 1 or 2 to view data from the first sensor group or the second sensor group.

Now, let's use a for loop to draw every point in our desired sensor group. To do this, we step through every value in our lists ```  for(int i=0; i<totalRowCount; i++) ``` we then check to make sure that the current data point has data in this sensor group ``` if(currentSnsrGrp >= sensorGroup[i]) ```. If it is a valid point that does have data, we draw an ellipse about the remapped lat long coordinates with radius 10, ``` ellipse(longList[i], latList[i], 10,10); ```. Run the code and you'll see the following:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902312/4b1753d2-ee1a-11e5-9071-cab488446bf6.png)

The sensor group if statement ``` if(currentSnsrGrp >= sensorGroup[i]) ```, is a subtle one. To understand it, recall that the ```sensorGroup``` refers to the period in which the datapoint was first recorded. This means that a datapoint that was first recorded in the first sensor group would have ```sensorGroup[i] = 1```. In order for this data point to show up when ```currentSnsGrp = 2 or 3``` we use a ```>=``` equality in our if statement.

Great! Next, let's give the user control over which sensor group they are seeing.

##### 05. PROCESSING: Animate UNOSAT data

There are many ways to give the user control over which group they see. We could have them press 1, 2, or 3 on the keyboard to display the respective group, we could have them click on a button, etc. For the purpose of this tutorial, let's have the user's mouse X position dictate the current sensor group. We will divide the screen into 3 segments horizontally. If the user's mouse is on the left third side of the screen, Processing will display data from the first sensor group. If the user's mouse is on the middle third of the screen, Processing will display data from the second sensor group. And finally, if the user's mouse is on the left third of the screen, Processing will display data from the third sensor group. We can do this with just a few lines of code.

Open the zipped Processing sketch **DisplayDatav02**. We don't need to change any code in the setup section so scroll down to the draw portion and observe the following modifications in ```line 72 - 84```:

```Processing
	background(0);
  
	int currentSnsrGrp;
  
	//gives us mouse control over which group of data we're seeing
	if (mouseX<width/3)
    {
    	currentSnsrGrp = 1;
	} else if(mouseX<width*2/3) {
		currentSnsrGrp = 2;
    } else {
    	currentSnsrGrp = 3;
	}
```

Let's go through line by line. You'll notice first that we've added ```background(0);``` to draw. Now everytime draw runs it will first cover the canvas in a black background. This is good as we'll be updating values whenever draw runs, we don't want old values to stay on the canvas window. The if statement contains the meat of the new code additions.

We use an if, elseif, else statement to meet all three of the possible mouse requirements we described above. If the mouse's X position is on the left third of the screen, set ```currentSnsrGrp = 1```. If this if statement fails we know the mouse is somewhere on the remaining 2/3 rd's of the screen. If the mouse's X position is less than 2/3 times the width, set the ```currentSnsrGrp = 2```. Else, if this fails, we know ```currentSnsrGrp = 3```. Easy as that! Run the code and move the mouse across the screen to see the different data associated with each sensor group.

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902313/4b18f228-ee1a-11e5-9804-6f1fbe769852.png)

Great! Now let's use some of the data we imported to display the level of damage at each data point to the user. There are many ways to do this, a convenient way is to color the data point based on it's damage data, either moderately damaged, severely damaged, or destroyed. We can code each one of these three to their own color.

##### 06. PROCESSING: Display damage data on each data point

In order to color each data point we'll take advantage of Processing's ```color(R, G, B)``` data type. Open the zipped Processing sketch **DisplayDatav03**.

You'll note some new lines of code, ```line 18 - 21 ``` before the setup portion of the code where we define our new global color variables:

```Processing
color moderateColor = color(0,0,255);
color severeColor = color(0,255,0);
color destroyColor = color(255,0,0);
color[] colorList = {destroyColor, severeColor, moderateColor};
```

Here, we create three colors, one for each damage type. ```moderateColor``` is blue, ```severeColor``` is green, and ```destroyColor``` is red. We then store these values in a list of colors called ```colorList``` so we can easily querry this data in our draw function later.

We will tell Processing how to color each dot in the draw section of our code. Scroll down to ```lines 96 - 112```. Note that the following takes place in our for loop so it will be executed for each value in our lists where ```i``` is the current value:

```Processing
    //Find the color of each of the circles
    if(currentSnsrGrp == 1)
    {
      if(damageList1[i]!=0)
      {
        //tell me the color!
        fill(colorList[damageList1[i]-1]);
      }
    } else if(currentSnsrGrp == 2) {
      if(damageList2[i]!=0)
      {
        //tell me the color!
        fill(colorList[damageList2[i]-1]);
      }
    } else {
      fill(colorList[damageList3[i]-1]);
    }
```

Let's unpack this line by line. It looks a little confusing but there are just some nested if statements that we need to get a handle on to understand what's going on. First, we check and see what the current sensor group is as defined by the user's mouse X position. If the current sensor group is 1 (```if(currentSnsrGrp == 1)```) and if this ```ith``` data point has a damage value associated with it in the first sensor group, i.e. if the damageList1 value for the current data point is nonzero ( ``` if(damageList1[i]!=0) ```), let's find the color of this datapoint based off of damage in ```damageList1``` (         ``` fill(colorList[damageList1[i]-1]); ```). The ```fill()``` function determines the fill color of the ellipse that we draw in ```line 117```. We determine the color by using our ```colorList ``` from above. Conveniently, we can use the ```damageList1``` value that is 1, 2, or 3 to index our ```colorList``` to retrieve the desired color. We subtract 1 from the ```damageList1``` value to correctly index the ```colorList``` off of the zero index. So, for example, if ```damageList1[i] = 1```, then ```damageList1[i]-1 = 0``` and so ``` colorList[damageList1[i]-1] = colorList[0] = destroyColor = color(255,0,0);``` and the ellipse will be filled as red.

Now, the above explanation only applied to the first sensor group since we were using ```damageList1```. But, sensor groups 2 and 3 are completely analogous arguments, we just use their respective damageLists. So, if ```currentSnsrGrp = 2```, for example, Processing executes code in  ```line 105 - 109``` and colors the ellipse based off of ```damageList2```. If, ```currentSnsrGrp = 3```, Processing executes ```line 111``` and colors the ellipse based off of ```damageList3```.

Woo! Ok run the code and you should see following:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902316/4b1c59a4-ee1a-11e5-8db0-1bd05aa323c4.png)

Great. Now let's add one last bit of visual interest to the datapoints before finish up by adding our map underlay. In the dataset, UNOSAT sometimes changes the damage classification from one sensor group period to another. So, for example, a building that was classified as severely damaged in sensor group 1, might be classified as moderately damaged or destroyed in sensor group 2 based off of the new satelite image that UNOSAT is working off of. Let's have the size of the dots reflect whether or not damage increased or decreased since the prior period. Let's make a dot bigger if damage increased from a prior period and let's outline a dot with a white border if it decreased in damage from a prior period.

Open the zipped Processing sketch **DisplayDatav04**.

Similar to the code we wrote to determine the ellipse color, we will change the size of the ellipse in the draw portion of the code. Scroll down to ```line 96``` inside of our for loop. You'll see a new variable,

```Processing
    //base radius of our ellispe datapoints
    circleRadius = 2;
    
    //stroke width and stroke color of ellipse edge
    strokeWeight(.75);
    stroke(0);
```

Before, our circleRadius was hard coded as the interger 10 in the ellipse function. We have simply created a variable for this integer and made it a smaller value, 2. The other two lines of code simply set the stroke or edge of the ellipse to have a line thickness of 0.75 pixels and a black stroke color by default.

Now, to determine the cirlce radius. Since the circle radius is determined versus a prior sensor group period, sensor group 1 data points are unaffected and will all be the same radius as there is no prior period to compare them to. So scroll down to ```line 111``` to observe the case where our current sensor group is sensor group 2.

```processing
    if(damageList2[i]!=0)
        {
        //tell me the color!
        fill(colorList[damageList2[i]-1]);

        //determine if bigger or smaller than last event
        if(damageList1[i]!=0)
        {
            if(damageList2[i] > damageList1[i])
            {
                circleRadius = circleRadius*3;
            } else if(damageList2[i] < damageList1[i]){
                stroke(255);
            }
        }
    }
```

You will notice that the new lines of code are added after we determined the color. First, we ensure that there is associated data in the previous sensor group period. Since this is sensor group 2, we check to make sure that the ```ith``` value in ```damageList1``` is non zero with ``` if(damageList1[i]!=0) ```. We then see if the current sensor group damage is greater than the prior periods sensor group damage with ```if(damageList2[i] > damageList1[i])```. If true, we increase the circleRadius by a factor of 3 with ``` circleRadius = circleRadius*3; ```. If the current damage is not greater than the prior damage it could either be less than or equal. If it is equal, we want to keep the circle unchanged, so we only check to see if the current damage is smaller than the prior damage period with  ```} else if(damageList2[i] < damageList1[i]){ ``` if this is true, we make the outline of the cirlce white with  ```stroke(255);```. The same logic is applied to the third sensor group in ``` line 130 - 140 ```. Run the code, and you should see the following:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902314/4b1ae790-ee1a-11e5-8cb5-2e2df513c735.png)

Fantastic! We are done with all of the difficult tasks! Now we will just add a map for context behind the data points and some text to tell the user which sensor group they are viewing.

##### 07. PROCESSING: Add context and export frames

We have a bunch of data displayed on our canvas and that data shows us how damaged each location is. But it is hard to tell where everyting is on this black background. Let us add a map for context. Open the zipped Processing sketch **DisplayDatav05**.

In the sketch folder you will find a .png that is a map of Aleppo roads that is cropped to the lat long coordinates we specified in our code with lat1, lat2, long1, long2. We can display this map in Processing using a handy image type, ```PImage```. 

We only need to add four lines of code to display our map under the data.

First, scroll to ``` line 23 ``` and observe the following global variable to initiaite our image ```mapunderlay``` variable of the ```PImage``` class:

```Processing
PImage mapunderlay;
```

Next, in ```line 31 - 33``` we tell Processing what image we would like to assign to ```mapunderlay``` and we then resize the image so that it fits in our canvas window:

```Processing
  //Load the photo
  mapunderlay = loadImage("Aleppo_Vector Roads-04.png");
  mapunderlay.resize(width, height);
```

Great, the photo is now loaded to memory and szied correctly. Finally, we just need to draw the image in the canvas window. We do this in - that is right - the draw section of the code. Scroll down to ```line 84 - 85 ``` and observe:

```Processing
  //Display our map underlay in the canvas window
  image(mapunderlay, 0, 0);
```
The ```0,0``` just tells Processing that we want the upper left hand corner of the image to be at the pixel location ```0,0```, the upper left hand corner of the canvas. Note that we wrote this code after ```background(0);```, so that the background does not cover our image. Run the code and you should see the map under our data points:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902315/4b1bfae0-ee1a-11e5-85ba-859d06f95516.png)

Super cool. Let us add one last finishing visual touch. Obviously you could spend a lot more time refining your animation and adding more functionality but for this tutorial, let us just tell the user which sensor date period they are hovering over.

Open the zipped Processing sketch **DisplayDatav06**. This will only take a few lines of code to achieve. Let us first make a list to store the 3 sensor dates as strings. This is the text that we will display in the window depending on what the current sensor group is. In the sketch, scroll to ``` line 25 ``` and observe:

```Processing
String[] sensorStringList = {"Latest Sensor Date: 9/23/13", "Latest Sensor Date: 5/23/14", "Latest Sensor Date: 4/26/15"};
```

Now, in the draw section of our code, all we need to do is get the correct string value based off of what the ```currentSnsrGrp``` is. Scroll down to ```line 101 - 104``` and note the following:

```Processing
  //displays the text of the latest sensor group in the window
  textSize(32);
  fill(255);
  text(sensorStringList[currentSnsrGrp-1], 10, height - 10);
  ```
The fist line here selects the font size, the second sets the text color to white and the third actually displays the text in the window. Note that, similar to our strategy with the color list, in ```sensorStringList[currentSnsrGrp-1]```, we are using the current sensor group subtracted by 1 to retrive the correct string from our ```sensorStringList```. We then tell Processing to display this text 10 pixels from the left hand side of the screen and 10 pixels above the bottom of the screen with ``` 10, height - 10 ```. Run the code and you should see the following:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902317/4b1cc8a8-ee1a-11e5-8187-3e69950fda7e.png)

It is all coming together! Last but not least, let us save frames from the animation. Saving frames allows us to create an animation that we can show as a gif or a video on a webpage. This allows us to share our work with the world! There are ways to present an interactive Processing sketch online but browser requirements and frequent Processing updates often render code outdated and unusable online. It is best to preserve an animation to easily share your work.

Lucky for us again, the folks at Processing thought this would be a nifty feature so they created a built in function to help us save frames. It only takes one line of code. Open the zipped Processing sketch **DislpayDatav07**.

Scroll all the way down to ```line 163 - 164``` and note the following code:

```Processing
  //Saves animation frames to frames folder
  saveFrame("frames/frame_#####.png");
```

The code saves the current frame as ```frame_####.png``` in a ```frames ``` folder in our sketch folder. Be careful: if you get an error make sure you created a folder named exactly ```frames``` for the images to be saved to! Run the code, and you will find that each frame is saved as a png in your ```frames``` folder. If you would like to output fewer frames per second, simply adjust the ```frameRate(10);``` to ```frameRate(1);``` to output one frame per second. You did it! You have created a Processing animation. For the very last step, we will move to Adobe AfterEffects to compile all of the frames into one animation.


##### 08. AFTEREFFECTS: Compile frames into animation

If you have not already, run the Processing sketch until you create your desired number of frames. Confirm that the frames saved correctly by navigating to the ```frames``` folder. Before we import the frames, let us make sure that all the frames saved completely. If we stopped Processing in the middle of saving a frame it can create an incomplete .png that might mess up the last frame of our animation. Examine the last few saved frames of your animation, if any are incomplete, delete them.

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902318/4b1e1032-ee1a-11e5-84b6-1eeafe1c1bee.png)

Now, open up AfterEffects. In this tutorial we will only be using the most basic features of AfterEffects. You could easily make the animation more advanced here by adding titles and credits. We are going to import the frames now.

Left click on the left hand side of the window to the left of the Composition canvas and select ```Right Click > Import > File...``` as pictued below:

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902307/4b11354c-ee1a-11e5-9032-84724c57c1d3.png)

Navigate to your Processing sketch frame folder and select the first frame. Make sure that PNG Sequence box is selected and then click Open.

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902310/4b129d4c-ee1a-11e5-8f57-65369927b15a.png)

Now that the frames are imported, let's create a new Composition to hold these frames. In the same place you right clicked to import the file, ```Right Click > New Composition...```. In the window that pops up, set the width of the Composition to 740 px and the height to 542 px, the dimensions of our Processing frames. Set the Duration to ```0:00:30:00```, that is 30 seconds. You can always adjust this later. Click Ok.

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902311/4b148a8a-ee1a-11e5-90dd-22782b5cd28d.png)

Now that we have a Composition to host the animation, click and drag the animation frames down to the lower portion of the screen.

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902309/4b11be86-ee1a-11e5-8381-2688d210b1d4.png)

Let's adjust our Composition length to the number of frames we have. On the menu bar click, ```Composition > Composition Settings... ``` and adjust the Composition duration to the desired length. Now, to render the animation, on the menu bar again select ```Composition > Add to Render Que```

![Add Layer](https://cloud.githubusercontent.com/assets/17283990/13902306/4b111ab2-ee1a-11e5-846b-83f6335e8e96.png)

You may change the file name and location by editing the "Output To:" field in the Rendering settings. Once you are satisfied, press Render towards the right hand side of the screen. Once the rendering completes, navigate to the Output location you specified to view your animation. You did it! You now have your very own Processing animation.

### Deliverables:

Give yourself a firm pat on your the back for completing the entire tutorial.

**Tutorial CheckList**

- [x] 01. TEXTEDIT: Explore UNOSAT dataset
- [x] 02. PROCESSING: "Hello world"
- [x] 03. PROCESSING: Load UNOSAT data
- [x] 04. PROCESSING: Display UNOSAT data
- [x] 05. PROCESSING: Animate UNOSAT data
- [x] 06. PROCESSING: Display damage data on each data point
- [x] 07. PROCESSING: Add context and export animation frames
- [x] 08. AFTEREFFECTS: Compile frames into animation
