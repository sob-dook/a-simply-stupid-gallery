simply-stupid-gallery
=============

I couldn't find a simple and free media gallery online anywhere. Fotorama was pretty good, but I had problems with it running inside in-app browsers. I decided to make my own using a little jQuery and some CSS. It's not perfect, but here you go. 

Description
----------------
Uses jQuery & CSS to show/hide images by clicking on left/right arrows. 

Demo
----------------
	navigate to 'working_sample_site' folder
		open 'index.html' in your browser of choice. 

How to use? 
-------------

	Navigate to 'working_sample_site' folder
		open 'index.html' in your text-editor

	Navigate to 'css'
		open 'websites.css' in your text-editor

HTML / CSS Layout 
-------------

CSS
------

Switch to 'websites.css' in your text-editor:

	The sample-site is set up using CSS-Grids with grid-template-areas.
		In 'websites.css' you'll see this defined between the /*GRID DEFINED*/ tags. 

		IMPORTANT!
			1. '.wrapper' defines the grid
			2. '.boxwelcome' defines the box dimensions inside the grid

	The gallery itself is contained within a seperate 'div' with a class of '.gallery_container'. 
		In 'websites.css' this is contained between the /*GALLERY_CONTAINER DEFINED*/ tags. 

		IMPORTANT!
			1. '.gallery_container' has a set height of 200px. This can be changed. However without a set height, the gallery collapses between image transitions. 
			2. '.gallery_container img' defines the dimensions of the images in the gallery. This is also set to 200px.


	Inside '.gallery_container' you will find a series of 'img' tags with their own id's, these are the images in the gallery. 

		IMPORTANT!
			Each of these images is seperately defined in 'websites.css' between the /*GALLERY IMAGES*/ tags
				#img2 - 10 are set to display:none 
				#img1 is not

	Below the img tags you will see a series of id's between the /*GALLERY ARROWS*/. They are named ranging from "mediaarrow_r0" thru "mediaarrow_r7" and "mediaarrow_l0" thru "mediaarrow_l8". These are the arrows on either side of the images. 

	the r indicates a right arrow, the l a left arrow. The number after indicates the order in which is is animated.

		example: '#mediaarrow_l8 {
				  display:none;
				  position:absolute;
				  top:50%;
				  left:3%;
				  color:grey;
				  opacity:.6;
				  font-size:2em;
				  -webkit-tap-highlight-color: rgba(0,0,0,0);
				}'

		IMPORTANT! 
			If you want to style your arrows you need to change the styling in each of the '#mediaarrow' id's 
				For instance to make all the arrows 'red' you have to change color:'grey' to color:'red' in each '#media_arrow_"X"' id.

				You could also style each arrow individually so that it changes colors as you progress through the gallery... idk.

HTML
------

Switch to 'index.html' in your text-editor:

	In the head of the HTML you will see the links to your stylesheets and to googles jquery library. 'normalize.css' is a reset-overide style sheet, and should always be placed before your own custom sheet.

		example: 

		<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

		<link rel="stylesheet" href="css/normalize.css">
    	<link rel="stylesheet" href="css/websites.css">


	The rest of the HTML body is laid out as follows:
		<body>
     		<div class="wrapper">
				<div class="boxwelcome welcome">
					<div class="gallery_container">
						<img id="img'X'>
						...
						<sup id="mediaarrow_'X'>
						...
					</div>
				</div>
			</div>
			<script>
		</body>

		The animation for the gallery is written out between the 'script' tags located just above the closing body tag. 

			example: $(document).ready(function(){
					    $("#mediaarrow_r1").click(function(){
					        $("#mediaarrow_r1").hide();
					        $("#mediaarrow_r2").show();
					        $("#mediaarrow_l2").show();
					            $("#img1").hide(600).fadeOut(600);
					            $("#img2").show(600).fadeIn(600);
					                $("#mediaarrow_l2").click(function(){
					                    $("#mediaarrow_r1").show();
					                    $("#mediaarrow_r2").hide();
					                    $("#mediaarrow_l2").hide();
					                        $("#img2").hide(600).fadeOut(600);
					                        $("#img1").show(600).fadeIn(600);
					    });

			To change the duration between images simply delete (600) in the relevent function  

				example: if you want to change the duration between #img1 and #img2, go to: 

					$("#img1").hide(600).fadeOut(600);
					            $("#img2").show(600).fadeIn(600);

				and change it to make it slower like so:

					$("#img1").hide(1200).fadeOut(1200);
					            $("#img2").show(1200).fadeIn(1200);

			Each transition time can be changed in this way. 

FIN
------
if you're having issues lmk (https://twitter.com/sobdes)
