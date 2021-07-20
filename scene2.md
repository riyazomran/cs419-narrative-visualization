<style>
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
}
</style>

<script>
    
function updateAnswer(questionNumber){
  var slider = document.getElementById("range" + questionNumber);
  var output = document.getElementById("your-answer" + questionNumber);
  var btn1 = document.getElementById("btn" + questionNumber);
  
  btn1.style.display="block";
  output.innerHTML = slider.value;
}
</script>

<table>
<tr>
<td><img src="images.png"></td>
<td style="vertical-align: middle;" class="banner banner0">
    <font size="10" color="#ffffff">Cost of Gun Violence in America </font>
</td>
</tr>
</table>

 <svg width="1200" height="750"></svg>

  <script src="https://d3js.org/d3.v4.min.js" type="text/JavaScript"></script> 
  <script src="https://d3js.org/colorbrewer.v1.min.js"></script>
<script>

d3.csv("Wonder-CDC-US -States-Gun-Violence.csv",function(data) {
   document.write(data);
}
</script>
