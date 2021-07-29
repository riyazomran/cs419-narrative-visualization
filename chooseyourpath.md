<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
<style>

.axis path{
    stroke:black;
    stroke-width:2px ;
}  

.axis line{
   stroke: black;
   stroke-width: 1.5px;
}
 
.axis text{
    fill: black;
    font-weight: bold;
    font-size: 14px;
    font-family:"Arial Black", Gadget, sans-serif;
}

.legend text{
    fill:  black;
    font-family:"Arial Black", Gadget, sans-serif;
}

.body {
  font-family: 'Courier New', monospace;
}

.banner{
width:100%;
height: 200px;
margin:7px auto;
-moz-box-shadow: 0 1px 3px rgba(0,0,0,0.5);
-webkit-box-shadow: 0 1px 3px rgba(0,0,0,0.5);
-moz-border-radius: 15px;
-webkit-border-radius: 15px;

}

.banner0{ background: #0066cc  url(banner0.png) no-repeat center left;
 }
 
.cells {
  fill: #bf3737;
}

.label {
  text-anchor: start;
  font: 24px sans-serif;
}
 
 .slidecontainer {
  width: 90%; /* Width of the outside container */
}

/* The slider itself */
.slider {
  -webkit-appearance: none;  /* Override default CSS styles */
  appearance: none;
  width: 100%; /* Full-width */
  height: 25px; /* Specified height */
  background: #d3d3d3; /* Grey background */
  outline: none; /* Remove outline */
  opacity: 0.7; /* Set transparency (for mouse-over effects on hover) */
  -webkit-transition: .2s; /* 0.2 seconds transition on hover */
  transition: opacity .2s;
}

/* Mouse-over effects */
.slider:hover {
  opacity: 1; /* Fully shown on mouse-over */
}

/* The slider handle (use -webkit- (Chrome, Opera, Safari, Edge) and -moz- (Firefox) to override default look) */
.slider::-webkit-slider-thumb {
  -webkit-appearance: none; /* Override default look */
  appearance: none;
  width: 25px; /* Set a specific slider handle width */
  height: 25px; /* Slider handle height */
  background: #0066cc; /* Green background */
  cursor: pointer; /* Cursor on hover */
}

.slider::-moz-range-thumb {
  width: 25px; /* Set a specific slider handle width */
  height: 25px; /* Slider handle height */
  background: #04AA6D; /* Green background */
  cursor: pointer; /* Cursor on hover */
}

.button {
  transition-duration: 0.4s;
}

.button:hover {
  background-color: #4CAF50; /* Green */
  color: white;
}

.button2 {
  background-color: white;
  color: black;
  border: 2px solid #008CBA;
  font-size: 40px;
}

.button2:hover {
  background-color: #008CBA;
  color: white;
}

.axis path{
  stroke:black;
  stroke-width:2px ;
}  

.axis line{
  stroke: black;
  stroke-width: 1.5px;
}
 
.axis text{
  fill: black;
  font-weight: bold;
  font-size: 14px;
  font-family:"Arial Black", Gadget, sans-serif;
}

.legend text{
   fill:  black;
   font-family:"Arial Black", Gadget, sans-serif;
}https://jsfiddle.net/#run
</style>


<table >
<tr>
<td><img src="images.png"></td>
<td style="vertical-align: middle;" class="banner banner0">
    <font size="10" color="#ffffff">Cost of Gun Violence in America </font>
</td>
</tr>
</table>
<br>

<div>

<div class="w3-light-grey" style="width:700px;">
  <div class="w3-blue" style="height:24px;width:100%"></div>
</div>
<div>Challenge Question &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Choose Your Path &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Explore Gun Violence by State</div>

</div><br>
<div><hr></div>

<table width="1600" height="900" border="0" style="text-align:center;">
<tr>
<td align="middle" colspan="4">
 <font size="10" color="black">Choose Your Path for Exploring</font>
 </td>
</tr>
<tr>
<td style="vertical-align:top;text-align:center;">
 <button id="btn1" class="button2" onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/scene2';">Gun Violence State Death Rate By Year Trend Analysis</button>
 </td>
<td style="vertical-align:top;;text-align:center;"> <button id="btn2" class="button2" onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/sc3';">Death Count by State Across Different Periods of Time</button>
</td>
</tr>
</table>

