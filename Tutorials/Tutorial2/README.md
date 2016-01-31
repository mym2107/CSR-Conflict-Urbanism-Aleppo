######CSR / Conflict Urbanism Aleppo 
##Tutorial 2: Setting Up A Conflict Urbanism: Case Study

In this tutorial, you will go through the basics of web design, to be able to easily work on the Conflict Urbanism: Case Study ([Example](http://c4sr.columbia.edu/conflict-urbanism-aleppo/data-and-advocacy.html)). We have provided the basics here with an understanding that you are willing to explore and understand the code. However, you are welcome to skip the section on the Basics of Web Design and look at the section on using the Case Study Template. You do not need to understand the code, in order to build your Case Study. You are requested *not* to change the style settings, so your submission is consistent with our style.

### Tools:
For this tutorial, we will be using the following tools:
* [Sublime](http://www.sublimetext.com/)
* [Chrome](https://www.google.com/chrome/)


### Datasets:
For this tutorial, we will be using the following datasets:
* Case_Study.zip, Download [here](https://dl.dropboxusercontent.com/u/37129324/CSR_CUA_Tutorials/CaseStudy%202.zip)


### Setting Up A Conflict Urbanism: Case Study


##### Steps:
  * 01. WEB: Introduction to HTML/CSS
  * 02. SUBLIME: Setting Up a Case Study


##### 01. WEB: Introduction to HTML/CSS
The following section is from [here](http://learn.shayhowe.com/html-css/building-your-first-web-page/) and provides a good understanding of Web Basics. Please refer to it for more information. Likewise, if you are interested in diving deeper, you are recommended to work through the following (7 hour) [course](https://www.codecademy.com/learn/web), on Code Academy. 

A **Website** has 2 main components:

**HTML**, *HyperText Markup Language*, gives content structure and meaning by defining that content as, for example, headings, paragraphs, or images. 

**CSS**, *Cascading Style Sheets*, is a presentation language created to style the appearance of content—using, for example, fonts or colors.
</br>

*Below are web basics. Feel free to skip to Case Study*

##### Three Common *HTML* terms:

*Elements*
Elements are designators that define the structure and content of objects within a page. Some of the more frequently used elements include multiple levels of `headings` (identified as `<h1>` through `<h6>` elements) and `paragraphs` (identified as the `<p>` element); the list goes on to include the `<a>`, `<div>`, `<span>`, `<strong>`, and `<em>` elements, and many more.

Elements are identified by the use of less-than and greater-than angle brackets, `< >`, surrounding the element name. Thus, an element will look like the following:

```html
<a>
```

*Tags*

The use of less-than and greater-than angle brackets surrounding an element creates what is known as a `tag`. Tags most commonly occur in pairs of opening and closing tags.

An `opening tag` marks the beginning of an element. It consists of a less-than sign followed by an element’s name, and then ends with a greater-than sign; for example, `<div>`.

A `closing tag` marks the end of an element. It consists of a less-than sign followed by a forward slash and the element’s name, and then ends with a greater-than sign; for example, `</div>`.

The `content` that falls between the opening and closing tags is the content of that element. An `anchor` link, for example, will have an opening tag of `<a>` and a closing tag of `</a>`. What falls between these two tags will be the content of the anchor link.

So, anchor tags will look a bit like this:

```html
<a> ... </a>
```

*Attributes*

Attributes are properties used to provide additional information about an element. The most common attributes include:
*	`id` attribute: which identifies an element
*	`class` attribute, which classifies an element
*	`src` attribute, which specifies a source for embeddable content
*	`href` attribute, which provides a hyperlink reference to a linked resource

Attributes are defined within the opening tag, after an element’s name. Generally attributes include a name and a value. The format for these attributes consists of the attribute name followed by an equals sign and then a quoted attribute value. For example, an `<a> `element including an href attribute would look like the following:

So, anchor tags will look a bit like this:

```html
<a href="http://www.google.com/">Google</a>
```

##### Setting Up an HTML Document:

**HTML** documents are plain text documents saved with an .html file extension rather than a .txt file extension. To begin writing HTML, you first need a plain text editor that you are comfortable using. This does not include Microsoft Word or Pages, as those are rich text editors. Two of the more popular plain text editors for writing HTML and CSS are *Dreamweaver* and *Sublime Text*.

All HTML documents have a required structure that includes the following declaration and elements: `<!DOCTYPE html>`, `<html>`, `<head>`, and `<body>`.

The document type declaration, or `<!DOCTYPE html>`, informs web browsers which version of HTML is being used and is placed at the very beginning of the HTML document. Because we’ll be using the latest version of HTML, our document type declaration is simply `<!DOCTYPE html>`. Following the document type declaration, the <html> element signifies the beginning of the document.

Inside the `<html>` element, the `<head>` element identifies the top of the document, including any metadata (accompanying information about the page). The content inside the `<head>` element is not displayed on the web page itself. Instead, it may include the document title (which is displayed on the title bar in the browser window), links to any external files, or any other beneficial metadata.

All of the visible content within the web page will fall within the `<body>` element. A breakdown of a typical HTML document structure looks like this:


```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Hello World</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a web page.</p>
  </body>
</html>
```

```css
body,
p {
  margin: 0;
}
h1 {
  margin-top: 0;
}
```

The preceding code shows the document beginning with the document type declaration, `<!DOCTYPE html>`, followed directly by the `<html>` element. Inside the `<html>` element come the `<head>` and `<body>` elements. The `<head>` element includes the character encoding of the page via the `<meta charset="utf-8">` tag and the title of the document via the `<title>` element. The `<body>` element includes a heading via the `<h1>` element and a paragraph via the `<p>` element. Because both the heading and paragraph are nested within the <body> element, they are visible on the web page.

When an element is placed inside of another element, also known as nested, it is a good idea to indent that element to keep the document structure well organized and legible. In the previous code, both the `<head>` and `<body>` elements were nested—and indented—inside the `<html>` element. The pattern of indenting for elements continues as new elements are added inside the `<head>` and `<body>` elements.


##### Three Common *CSS* terms:

In addition to HTML terms, there are a few common CSS terms you will want to familiarize yourself with. These terms include selectors, properties, and values. As with the HTML terminology, the more you work with CSS, the more these terms will become second nature.

*Selectors:*

As elements are added to a web page, they may be styled using CSS. A selector designates exactly which element or elements within our HTML to target and apply styles (such as color, size, and position) to. Selectors may include a combination of different qualifiers to select unique elements, all depending on how specific we wish to be. For example, we may want to select every paragraph on a page, or we may want to select only one specific paragraph on a page. Selectors generally target an attribute value, such as an id or class value, or target the type of element, such as `<h1>` or `<p>`.

Within CSS, selectors are followed with curly brackets, `{}`, which encompass the styles to be applied to the selected element. The selector here is targeting all `<p>` elements.

```css
p {
  margin: 0;
}
```

*Properties:*

Once an element is selected, a property determines the styles that will be applied to that element. Property names fall after a selector, within the curly brackets, `{}`, and immediately preceding a colon, `:`. There are numerous properties we can use, such as background, color, font-size, height, and width, and new properties are often added. In the following code, we are defining the color and font-size properties to be applied to all `<p>` elements.

```css
p {
  color: ...;
  font-size: ...;
}
```

*Values*

So far we’ve selected an element with a selector and determined what style we’d like to apply with a property. Now we can determine the behavior of that property with a value. Values can be identified as the text between the colon, `:`, and semicolon, ;. Here we are selecting all `<p>` elements and setting the value of the color property to be orange and the value of the font-size property to be 16 pixels.

```css
p {
  color: orange;
  font-size: 16px;
}
```

To review, in CSS our rule set begins with the selector, which is immediately followed by curly brackets. Within these curly brackets are declarations consisting of property and value pairs. Each declaration begins with a property, which is followed by a colon, the property value, and finally a semicolon.

It is a common practice to indent property and value pairs within the curly brackets. As with HTML, these indentations help keep our code organized and legible.


##### Working with *Selectors*:

Selectors, as previously mentioned, indicate which HTML elements are being styled. It is important to fully understand how to use selectors and how they can be leveraged. The first step is to become familiar with the different types of selectors. We’ll start with the most common selectors: `type`, `class`, and `ID ` selectors.


*Type Selectors:*

Type selectors target elements by their element type. For example, should we wish to target all division elements, `<div>`, we would use a type selector of div. The following code shows a type selector for division elements as well as the corresponding HTML it selects.

```css
div { ... }
```

```html
<div>...</div>          
<div>...</div>
```

*Class Selectors:*

Class selectors allow us to select an element based on the element’s class attribute value. Class selectors are a little more specific than type selectors, as they select a particular group of elements rather than all elements of one type.

Class selectors allow us to apply the same styles to different elements at once by using the same class attribute value across multiple elements.

Within CSS, classes are denoted by a leading period, `.`, followed by the class attribute value. Here the class selector will select any element containing the class attribute value of awesome, including both division and paragraph elements.

```css
.awesome { ... }
```

```html
<div class="awesome">...</div>
<p class="awesome">...</p>
```

*ID Selectors:*

ID selectors are even more precise than class selectors, as they target only one unique element at a time. Just as class selectors use an element’s class attribute value as the selector, ID selectors use an element’s id attribute value as a selector.

Regardless of which type of element they appear on, id attribute values can only be used once per page. If used they should be reserved for significant elements.

Within CSS, ID selectors are denoted by a leading hash sign, `#`, followed by the id attribute value. Here the ID selector will only select the element containing the id attribute value of shayhowe.

```css
#Test { ... }
```

```html
<div id="Test">...</div>
```

Selectors are extremely powerful, and the selectors outlined here are the most common selectors we’ll come across. These selectors are also only the beginning. Many more advanced selectors exist and are readily available. When you feel comfortable with these selectors, don’t be afraid to look into some of the more advanced selectors.

All right, everything is starting to come together. We add elements to a page inside our HTML, and we can then select those elements and apply styles to them using CSS. Now let’s connect the dots between our HTML and CSS, and get these two languages working together.

##### Referencing **CSS**:

In order to get our CSS talking to our HTML, we need to reference our CSS file within our HTML. The best practice for referencing our CSS is to include all of our styles in a single external style sheet, which is referenced from within the `<head>` element of our HTML document. Using a single external style sheet allows us to use the same styles across an entire website and quickly make changes sitewide.

To create our external CSS style sheet, we’ll want to use our text editor of choice again to create a new plain text file with a .css file extension. Our CSS file should be saved within the same folder, or a subfolder, where our HTML file is located.

Within the `<head>` element of the HTML document, the `<link>` element is used to define the relationship between the HTML file and the CSS file. Because we are linking to CSS, we use the rel attribute with a value of stylesheet to specify their relationship. Furthermore, the href (or hyperlink reference) attribute is used to identify the location, or path, of the CSS file.

Consider the following example of an HTML document `<head>` element that references a single external style sheet.

```html
<head>
  <link rel="stylesheet" href="main.css">
</head>
```

In order for the CSS to render correctly, the path of the href attribute value must directly correlate to where our CSS file is saved. In the preceding example, the main.css file is stored within the same location as the HTML file, also known as the root directory.

If our CSS file is within a subdirectory or subfolder, the href attribute value needs to correlate to this path accordingly. For example, if our main.css file were stored within a subdirectory named stylesheets, the href attribute value would be stylesheets/main.css, using a forward slash to indicate moving into a subdirectory.

##### Commenting Code:

HTML comments start with `<!-- and end with -->`. 
CSS comments start with `/*` and end with `*/`.
Note: If you would like to learn more, please follow further tutorials [here](http://learn.shayhowe.com/html-css/getting-to-know-html/).



##### 02. SUBLIME: Setting Up a Case Study

For this part, we will walk through a case study. The deliverable for this tutorial is to upload a case study about the neighborhood you mapped. If you are using this as a guide to build your final case-study, please use the different modules, based on requirement. 

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12704890/00e51b58-c833-11e5-9005-1cabfcdddf33.png)

We've divided the code in several parts to add additional explanations. We start with the complete code and dive into explanations for each part later. You can set up a new folder using the code below, through sublime. Or you can use the downloaded Case_Study.zip folder that has the `.html` and `.css` files. Open the `.html` and `'.css` files in sublime and open the CaseStudy in Chrome.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12704891/0250f0ac-c833-11e5-9398-a3c6e2577647.png)

We suggest using Chrome, as you have access to developer tools that will help you to debug your code. You probably won't run into any issues using the case study template, but knowing how to decode or atleast see where you have an error is a good practise. In Chrome, go to  `View > Developer > Developer Tools`. This opens the `console` that shows you different parts of your site. If there is an error, you will be able to see it here.

![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12704893/061b1fb4-c833-11e5-8710-620e62942ff1.png)
<br>
![Add Layer](https://cloud.githubusercontent.com/assets/16892784/12704892/0610ebca-c833-11e5-8b99-37095dc1af4a.png)

This is the code for the Case Study. Every step is commented. You can also skip to the end of the code, to look at individual components separately. Or you can follow the instructions in the code comments, to make changes and add your content on the go. Everytime you change the code in sublime, hit `save`. `Refresh` the web page and you should be able to see the changes. Note: We request you to not make any changes to the .css files. 

```html
<!-- Conflict Urbanism: Aleppo
     Center for Spatial Research
     Madeeha Merchant (mym2107@columbia.edu)

================================================================= -->
<!DOCTYPE html>
<html lang="en">

  <head>
  <!--Do not change: Main title as appears in window -->
  <title> Conflict Urbanism: Aleppo</title>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1" />

  <!--Add: Project Keyword Description & Student Name  -->
  <meta name="description" content="">
  <meta name= "author" content="">
    
  <!--Do not change: boostrap -->
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.4/css/bootstrap.min.css">

  <!--Do not change: css files required for case study -->
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

        <!--Do not change:Course : Title if working on Aleppo -->
        <h5><a href="index.html">Conflict Urbanism Aleppo</a></h5>

        <!--Add: Case Study Title -->
        <h5>Case Study | Type Title Here </h5>

        <!--Add: Image Header: File Size: 1800x450.png. 
        Save your file as 'Header_image_1800x450.png in the <img> folder
        Use Illustrator Template in folder, if you require size setup-->
        <div class="img-padding">
          <img src="img/Header_image_1800x450.png" class="img-responsive" />
        </div>

      </div>
    </div>

<!--Note: We suggest dividing your case study ito many different components. Think of this as chapters of your paper. 
In this example, we have 7 sections. Below we set up a list for adding to the menu on left. 
You could use chapter 1, chapter 2 or give text titles. --> 

<div class="row">
  <div class="col-md-3 scrollspy">
    <div id="sticky-menu ">
      <ul id="nav" class="nav c4sr-nav" data-spy="affix">
        <!-- <li><a href="#section_id"><img src="img/dot-1.png" />Chapter_Name</a></li>-->
        <li><a href="#Text1"><img src="img/dot-1.png" />Introduction</a></li>
        <li><a href="#Text2"><img src="img/dot-1.png" />Text with Annotation</a></li>
        <li><a href="#Text3"><img src="img/dot-1.png" />Text with PDF</a></li>
        <li><a href="#Text4"><img src="img/dot-1.png" />Text with Image</a></li>
        <li><a href="#Text5"><img src="img/dot-1.png" />Text with Video</a></li>
        <li><a href="#Text6"><img src="img/dot-1.png" />Text with Interactive</a></li>
        <li><a href="#Text7"><img src="img/dot-1.png" />Text with Map</a><li>
      </ul>
    </div>
  </div>

<!--Note: You can start with the first few paragraphs and keep adding. Each <item> above has a referenced paragraph below. 
You can think of the above being a table of contents and below being the chapters, with actual text. 
If you add a chapter, go back to the Table of Contents and add a tab for it. --> 

  <!-- main -->
  <div class="col-md-6 body-text">

<!--Add: Text Paragraph -->
     <!-- <h5 id="section_id">Section Title</h5> -->
     <h5 id="Text1">Introduction to the course</h5>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. <br/><br/>Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. <br/><br/>

<!--Add: Text Paragraph with Annotation. 

We have designed annotations, so that they are responsive to where you are on the case study. 
These appear on the right column next to the footnote. To add a footnote, insert the following line of code. 
Please change numbers in order. Everytime, you add a footnote, you will be required to go to the footnote section of the code, 
to add in the text and link.

To add a footnote, insert: <div class="footnote footnote-1">1</div> 
Starting from #1, change as you proceed-->

    <h5 id="Text2">Text with Annotation</h5>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. <div class="footnote footnote-1">1</div> Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.<div class="footnote footnote-2">2</div> It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. <br/><br/>

<!--Add: Text Paragraph with PDF report. 
To add a link to a PDF, save the file in the same folder and update link text 
Insert the following code: <a href='filename.pdf'>Download Report</a> -->
    <h5 id="Text3">Text with PDF</h5><br/>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</br>
<a href='sample_report.pdf'>Download Report</a><br/><br/>

<!--Add: Text Paragraph with Image. 
To add an Image, save the file in the <img> folder 
Insert the following code: <img src="img/filename.png" class="img-responsive"/> -->
    <h5 id="Text4">Text with Image</h5><br/>
<img src="img/Sample_Image.png" class="img-responsive"/><br/>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. <br/><br/>

<!--Add: Text Paragraph with Video. 
To add a Video, either upload to vimeo or use Youtube link 
Insert the following code: 
<div class="embed-responsive embed-responsive-4by3">
  <<iframe class="embed-responsive-item" src="weblink_of_video"></iframe>
</div>
-->
<h5 id="Text5">Text with Video</h5><br/>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. <br/></br>
<!-- Example: Vimeo -->
<div class="embed-responsive embed-responsive-4by3">
  <<iframe class="embed-responsive-item" src="https://player.vimeo.com/video/152612971"></iframe>
</div>
</br>

<!--Add: Text with Interactive. 
As part of the project, you might design an interactive website. If you would like to include that in the case study, 
the easiest way might be linking that to an image. We suggest this as oppose to integrating them into your case study. 
Interactives might be heavier files and be difficult to load, instantly. Below, there are 3 examples.
-->

<h5 id="Text6">Text with Interactive</h5><br/>
<a href="Interactive.html" target='_blank' ><img src="img/Sample_Image_Interactive.png" class="img-responsive"/></a>

<br/>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.<br/><br/> 

<iframe width='100%' height='500px' frameBorder='0' src='interactive.html'></iframe>

<br/><br/> 
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.<br/><br/> 

<iframe width='100%' height='500px' frameBorder='0' src= "http://c4sr.columbia.edu/conflict-urbanism-aleppo/index.html" name="iframe_x"></iframe> 
<p><a href="http://c4sr.columbia.edu/conflict-urbanism-aleppo/index.html" target="iframe_x">Aleppo Site</a></p>

<br/>

<!--Add: Text with Interactive Map. 
You can bring any project from mapbox editor, using the iframe method. 
In tutorial 4, we go over Mapbox basics, to make such an interactive map in mapbox editor.

Note: You can bring in any project, with the above code as long as you have your mapbox API key and map id
-->

<h5 id="Text7">Text with Map</h5><br/>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.<br/><br/>
</br>

<!-- Copy iframe tab form Mapbox Editor -->
</br>
<iframe width='100%' height='500px' frameBorder='0' src='https://a.tiles.mapbox.com/v4/c4sr.p194inbb/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'></iframe>
</br>

<!--Add: Your name and description as follows -->
</br>
<hr>
Your Name: <br/><br/>Description (Program, Year, Expertise)
<hr>
<br/><br/>
</div>

<!-- Add: footnotes with definitions
This is the code:
<div class="footnote-ref footnote-ref-1"><sup>1</sup>Title <a href= "www.c4sr.columbia.edu"> “Descriptive text”</a> Date </div> 
-->
<div class="col-md-3">
  <div class="footnotes">
    <div class="footnote-ref footnote-ref-1"><sup>1</sup>Title <a href= "www.c4sr.columbia.edu"> “Descriptive text”</a> Date </div>
    <div class="footnote-ref footnote-ref-2"><sup>2</sup>Test2 <a href= "www.c4sr.columbia.edu"> “Description ”</a> Date </div>
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
    
<!-- Do not change !!! -->
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

##### Code Snippets:
This section, looks at the individual snippets separately and what you will need to change in the code. 

* Add Title:
```html
<!--Add: Case Study Title -->
<h5>Case Study | Type Title Here </h5>
```

*  Add Header Image:
Save your file as 'Header_image_1800x450.png in the <img> folder. Use Illustrator Template in folder, if you require size setup.
```html
<div class="img-padding">
<img src="img/Header_image_1800x450.png" class="img-responsive" />
</div>
```
* Add Chapter: Titles:
We suggest dividing your case study ito many different components. Think of this as chapters of your paper. In this example, we have 7 sections. Below we set up a list for adding to the menu on left. You could use chapter 1, chapter 2 or give text titles, as required.
```html
<div class="row">
  <div class="col-md-3 scrollspy">
    <div id="sticky-menu ">
      <ul id="nav" class="nav c4sr-nav" data-spy="affix">
        <!-- <li><a href="#section_id"><img src="img/dot-1.png" />Chapter_Name</a></li>-->
        <li><a href="#Text1"><img src="img/dot-1.png" />Introduction</a></li>
        <li><a href="#Text2"><img src="img/dot-1.png" />Text with Annotation</a></li>
        <li><a href="#Text3"><img src="img/dot-1.png" />Text with PDF</a></li>
        <li><a href="#Text4"><img src="img/dot-1.png" />Text with Image</a></li>
        <li><a href="#Text5"><img src="img/dot-1.png" />Text with Video</a></li>
        <li><a href="#Text6"><img src="img/dot-1.png" />Text with Interactive</a></li>
        <li><a href="#Text7"><img src="img/dot-1.png" />Text with Map</a><li>
      </ul>
    </div>
  </div>
```

* Add Chapter: Text
Next, you will add text paragraphs for each chapter. This methods allows visitors to go to specific sections of your case study. THe title of your chapter can be different from the one you use for the Table of Contents. It could be a longer version. 
```html
     <!-- <h5 id="section_id">Section Title</h5> -->
     <h5 id="Text1">Introduction to the course</h5>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. <br/><br/>Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. <br/><br/>
```

* Add Text with Annotations:
We have designed annotations, so that they are responsive to where you are on the case study. These appear on the right column next to the footnote. To add a footnote, insert the following line of code. Please change numbers in order. Everytime, you add a footnote, you will be required to go to the footnote section of the code, to add in the text and link. To add a footnote, insert the following code next to where you want the foot note. Start from #1, and change as you proceed.
```html
<div class="footnote footnote-1">1</div> 
```
Here's how it would look in the paragraph:
```
<h5 id="Text2">Text with Annotation</h5>
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. <div class="footnote footnote-1">1</div> Add Text: Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.<div class="footnote footnote-2">2</div> It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. <br/><br/>
```
Then Add details to `Footnotes Section` at end of the code. 
```html
<div class="col-md-3">
  <div class="footnotes">
    <div class="footnote-ref footnote-ref-1"><sup>1</sup>Title <a href= "www.c4sr.columbia.edu"> “Descriptive text”</a> Date </div>
    <div class="footnote-ref footnote-ref-2"><sup>2</sup>Test2 <a href= "www.c4sr.columbia.edu"> “Description ”</a> Date </div>
  </div>
</div>
</div>
```

* Add PDFs:
<br>To add a link to a PDF, save the file in the same folder and update link text. Insert the following code: 
```html
<a href='sample_report.pdf'>Download Report</a><br/><br/>
```
* Add Image:
<br>To add an Image, save the file in the <img> folder. Insert the following code:
```html
<img src="img/Sample_Image.png" class="img-responsive"/><br/>
```
* Add Video:
<br>To add a Video, either upload to vimeo or use Youtube link. Insert the following code: 
```html
<div class="embed-responsive embed-responsive-4by3">
  <<iframe class="embed-responsive-item" src="https://player.vimeo.com/video/152612971"></iframe>
</div>
```
* Add Interactive:
<br>As part of the project, you might design an interactive website. If you would like to include that in the case study, the easiest way might be linking that to an image. We suggest this as oppose to integrating them into your case study. Interactives might be heavier files and be difficult to load, instantly. Below, there are 3 examples.

1. Linking Image to an Interactive html:
```html 
<a href="filename.html"><img src="img/filename_interactive.png" class="img-responsive"/></a>
```

2. Embedding Interactive (This is ok if it's a couple of layers)

```html
<iframe width='100%' height='500px' frameBorder='0' src='interactive.html'></iframe>
```

3. Embedding an entire website (As case study is responsive, test ! test !)

```html
<iframe width='100%' height='500px' frameBorder='0' src= "http://c4sr.columbia.edu/conflict-urbanism-aleppo/index.html" name="iframe_x"></iframe> 
<p><a href="http://c4sr.columbia.edu/conflict-urbanism-aleppo/index.html" target="iframe_x">Aleppo Site</a></p>
```
* Add Map:
<br>You can bring any project from mapbox editor, using the iframe method. In [tutorial 4](), we go over Mapbox basics, to make such an interactive map in mapbox editor.

Following is the code that you copy/paste from mapbox editor
```html
<iframe width='100%' height='500px' frameBorder='0' src='https://a.tiles.mapbox.com/v4/c4sr.p194inbb/attribution,zoompan,zoomwheel,geocoder,share.html?access_token=pk.eyJ1IjoiYzRzciIsImEiOiJjaWdhN2ptaHkwZmxidWxrcnBscjM5N2trIn0.Rcac0rnnmYf2eXZOL0tT5A'></iframe>
```
Note: You can bring in any project, with the above code as long as you have your mapbox API key and map id

* Add your Name:
```html
<hr>
Your Name: <br/><br/>Description (Program, Year, Expertise)
<hr>
```

### Deliverables:
Upload a Case Study titled: Neighborhood
