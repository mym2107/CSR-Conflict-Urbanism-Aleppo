######CSR / Conflict Urbanism Aleppo
##Tutorial 2

In this tutorial we are going to make a simple interactive case study. 

### Tools:
For this tutorial, we will be using the following tools:
* [WEB]
* [Mapbox](https://www.mapbox.com)

##### Web Basics:
[WEB Tutorials](http://learn.shayhowe.com/html-css/)

##### Template:
* Understanding Template Structure
* Understanding Annotations
* Add Text
* Add Links
* Add Image
* Add Video
* Add Interactive Map
* Embed other site

##### Mapbox:
* Set Up Mapbox Account
* Note Map API
* Note Map ID
* Draw over Point of Interest
* Add Text, Link, Image, etc
* Embed in Case Study

```html
<!-- Conflict Urbanism: Aleppo
     Center for Spatial Research
     Madeeha Merchant (mym2107@columbia.edu)

================================================================= -->
<!DOCTYPE html>
<html lang="en">
  <head>
  <!--Do not change Main title as appears in window -->
  <title> Conflict Urbanism: Aleppo</title>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1" />

  <!-- optimize for search ... student name  -->
  <meta name="description" content="">
  <meta name="author" content="">
    
  <!-- boostrap -->
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap.min.css">

  <!-- css files required for case study -->
  <link href='css/conflict_main.css' rel='stylesheet' />
  <link href='css/conflict_course.css' rel='stylesheet' />
  <style>
  body {
    font-family: Arial, sans;
  }
</style>
</head>

<body>
  <div class="container main">
    <div class="row top-row">
      <div class="col-md-12">
        <!-- Course : Title / Do not change -->
        <h5><a href="index.html">Conflict Urbanism Aleppo</a></h5>
        <!-- Case Study | Input Title and Student Name -->
        <h5>Case Study | Title: User Name </h5>
        <div class="img-padding">
          <!-- In put Header Image -->
          <img src="img/Header_image_1800x450.png" class="img-responsive" />
        </div>
      </div>
    </div>

<div class="row">
  <!-- menu -->
  <!-- Divide your case study into clear section for easy navigation -->
  <div class="col-md-3 scrollspy">
    <div id="sticky-menu ">
      <ul id="nav" class="nav c4sr-nav" data-spy="affix">
        <!--<li><a href="#section_id"><img src="img/dot-1.png" />Section Header</a></li> -->     
        <li><a href="#Text1"><img src="img/dot-1.png" />Text Paragraph</a></li>
        <li><a href="#Text2"><img src="img/dot-1.png" />Text with Annotation</a></li>
        <li><a href="#Text3"><img src="img/dot-1.png" />Text with PDF</a></li>
        <li><a href="#Text4"><img src="img/dot-1.png" />Text with Image</a></li>
        <li><a href="#Text5"><img src="img/dot-1.png" />Text with Video</a></li>
        <li><a href="#Text6"><img src="img/dot-1.png" />Text with Interactive</a></li>
        <li><a href="#Text7"><img src="img/dot-1.png" />Text with Map</a><li>
      </ul>
    </div>
  </div>

  <!-- main -->
  <div class="col-md-6 body-text">
     <!-- Adding a Text Paragraph -->
     <!-- <h5 id="section_id">Section Title</h5> -->
     <h5 id="Text1">Text Paragraph</h5>
Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.<br/><br/>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.<br/><br/>

<!-- Adding a Text Paragraph with Annotation-->
<!-- To add a footnote: <div class="footnote footnote-1">1</div> , change numbers-->
    <h5 id="Text2">Text with Annotation</h5>
Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.<div class="footnote footnote-1">1</div> Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. <br/><br/>

<!-- Adding a Text Paragraph with link-->
<h5 id="Text3">Text with PDF</h5><br/>
Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</br>
<a href='report.pdf'>Download Report</a><br/><br/>

<!-- Adding a Text Paragraph with Image-->
<h5 id="Text4">Text with Image</h5><br/>
<img src="img/CSR_Aleppo_HRWImpactSites.png" class="img-responsive"/>
<br/>
Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. <br/><br/>

<!-- Adding a Text Paragraph with video -->
<h5 id="Text5">Text with Video</h5><br/>
Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.<br/></br>
<div class="embed-responsive embed-responsive-4by3">
  <<iframe class="embed-responsive-item" src="https://player.vimeo.com/video/152612971"></iframe>
</div>
</br>
<div class="embed-responsive embed-responsive-4by3">
  <<iframe class="embed-responsive-item" src="http://www.youtube.com/embed/XGSy3_Czz8k?autoplay=1"></iframe>
</div>
</br>


<h5 id="Text6">Text with Interactive</h5><br/>
<a href="HRW-Interactive.html"><img src="img/CSR_HRW_InteractiveAnalysis.png" class="img-responsive"/></a>
<br/>
Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.<br/><br/> 

<h5 id="Text7">Text with Map</h5><br/>
Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.<br/><br/>
</br>
<!-- Copy iframe tab form Mapbox Editor -->
<iframe width='100%' height='500px' frameBorder='0' src='https://a.tiles.mapbox.com/v4/c4sr.p06ih30g/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'></iframe>
<br/> </br>
<iframe width='100%' height='500px' frameBorder='0' src='https://a.tiles.mapbox.com/v4/c4sr.o5bdhefo/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'></iframe>
</br>

</br>
<hr>
Your Name: <br/><br/>Description (Program, Year, Expertise)
<br/><br/>
</div>

<!-- footnotes -->
<div class="col-md-3">
  <div class="footnotes">
    <div class="footnote-ref footnote-ref-1"><sup>1</sup>Title <a href= "www.c4sr.columbia.edu"> “Descriptive text”</a> Date </div>
<!--   ADD  <div class="footnote-ref footnote-ref-1"><sup>1</sup>Title <a href= "www.c4sr.columbia.edu"> “Descriptive text”</a> Date </div> -->
  </div>
</div>


</div>

<!-- Do not change -->        

  <div class="row red bottom-line">
    <div class="col-sm-12">
      <h5><center> Center for Spatial Research, Columbia University</center></h5>
    </div>
  </div>

</div>

<!-- Do not change -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js" crossorigin="anonymous"></script>
    

<script>
$(document).ready(function() {

  // bootstrap affix menu
  $('#nav').affix({
    offset: {
      top: $('#nav').offset().top
    }
  });

  // footnote logic
  $('.footnote').each(function() {
    var f = $(this).attr('class').split(" ")[1];
    var num = f.split("-")[1];
    var top = $('.' + f).position().top;
    var num_c = num - 1;
    var offset = num_c * 32;
    var top_n = top - offset;
    
    // align footnote to position
    $('.footnote-ref-' + num).css({
      top: top_n
    });

    var final_p = $('.footnote-ref-' + num).position().top;
  });

  // Mobile version : Switch footnote position
  if ($("ul.c4sr-nav").css("display") == "none" ){
        $('.footnote-ref').each(function() {
          $(this).css({
            'top': 0,
            'margin-bottom': '10px'});
        });
  }

});
</script>


</body>
</html>
```
