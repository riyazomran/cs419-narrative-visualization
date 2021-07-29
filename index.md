
<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
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
  <!-- <td colspan="3" align="right">Click here to learn more <img src="image2.png"></td> -->
</tr>
</table>

<div><br></div>
<div style="line-weight:8px"><font size="5">We the people of the United States of America must start to recognize the inherant social costs of gun violence and the domino effect repercussions. The US gun homicide rate is 25 times that of other high-income countries. While we can't control random acts of violence, we must aim to learn from them. Take the challenge by clicking the the arrow below!</font>
</div>
<div><br></div>
<div>

<div class="w3-light-grey" style="width:200px;">
  <div class="w3-blue" style="height:24px;width:10%"></div>
</div>
<div>Challenge Question &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Choose Your Path &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Explore Gun Violence by State</div>

</div><br>
    <button id="chooseYourPath" class="button2" onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/chooseyourpath';">Explore More: Choose Your Path</button>
<div><hr></div>

<!-- QUESTION #1 -->

<table border="0">
<tr>
<td style="vertical-align: top;" width="400px">
 <div style="color:#0066cc;font-size:20px;vertical-align: top;"><b>How many people are shot and killed per day in the United States?</b></div> 
 <div id="q1_slider_answer">
    <p style="color:#0066cc;font-size:20px;">Your answer: &nbsp;&nbsp;&nbsp; 
    <span id="your-answer1" style="color:#0066cc;font-size:20px;">0</span>&nbsp;&nbsp;&nbsp;
    <button id="btn1" class="button2" onclick="update(Math.floor(316),'1');" style="display:none;">Lock in my answer!</button></p> 
 </div>
 <div class="slidecontainer" id="question1" onclick="updateAnswer(1);" style="white-space: nowrap;">
   <input type="range" min="1" max="1000" value="50" class="slider" id="range1">
 </div> 
</td>
<td style="vertical-align: top;text-align: center;" >
    <svg id="svg1" width="450" height="300"></svg>
</td>
<td>

<span id="explaindesc1" style="display: none;"> 
  <font size="4" style="text-align: center;">When we breakdown the <b>316 daily deaths</b>, we see the extent of the impact of normalizing gun ownership has : </font>
</span>
<ul id="explain1" style="display: none;">
  <li>106 people are shot and killed</li>
  <li>210 survive gunshot injuries</li>
  <li>95 are intentionally shot by someone else and survive</li>
  <li>39 are murdered</li>
  <li>64 die from gun suicide</li>
  <li>10 survive an attempted gun suicide</li>
  <li>1 is killed unintentionally</li>
  <li>90 are shot unintentionally and survive</li>
  <li>1 is killed by legal intervention</li>
  <li>4 are shot by legal intervention and survive</li>
  <li>1 died but the intent was unknown</li>
  <li>12 are shot and survive but the intent was unknown</li>
</ul>
</td>
</tr>
</table>

<table border="0">
<tr>
<td style="vertical-align: top;" width="400px">
 <div style="color:#0066cc;font-size:20px;vertical-align: top;"><b>How many daily gun violence incidents happen that impact children and teens (ages 1-17)?</b></div> 
 <div id="q1_slider_answer">
    <p style="color:#0066cc;font-size:20px;">Your answer: &nbsp;&nbsp;&nbsp; 
    <span id="your-answer2" style="color:#0066cc;font-size:20px;">0</span>&nbsp;&nbsp;&nbsp;
    <button id="btn2" class="button2" onclick="update(Math.floor(22),'2');" style="display:none;">Lock in my answer!</button></p> 
 </div>
 <div class="slidecontainer" id="question2" onclick="updateAnswer(2);" style="white-space: nowrap;">
   <input type="range" min="1" max="1000" value="50" class="slider" id="range2">
 </div> 
</td>
<td style="vertical-align: top;text-align: center;" >
    <svg id="svg2" width="450" height="300"></svg>
</td>
<td>

<span id="explaindesc2" style="display: none;"> 
  <font size="4" style="text-align: center;">Every day, <b>22 children and teens (1-17)</b> are shot in the United States. Among those: </font>
</span>
<ul id="explain2" style="display: none;">
  <li>5 die from gun violence</li>
  <li>2 are murdered</li>
  <li>17 children and teens survive gunshot injuries</li>
  <li>8 are intentionally shot by someone else and survive</li>
  <li>2 children and teens either die from gun suicide or survive an attempted gun suicide</li>
  <li>8 children and teens are unintentionally shot</li>
</ul>
</td>
</tr>
</table>

<table border="0">
<tr>
<td style="vertical-align: top;" width="400px">
 <div style="color:#0066cc;font-size:20px;vertical-align: top;"><b>On average how many people are shot annually in the United States of America? </b></div> 
 <div id="q1_slider_answer">
    <p style="color:#0066cc;font-size:20px;">Your answer: &nbsp;&nbsp;&nbsp; 
    <span id="your-answer3" style="color:#0066cc;font-size:20px;">0</span>&nbsp;&nbsp;&nbsp;
    <button id="btn3" class="button2" onclick="update(Math.floor(115551),'3');" style="display:none;">Lock in my answer!</button></p> 
 </div>
 <div class="slidecontainer" id="question3" onclick="updateAnswer(3);" style="white-space: nowrap;">
   <input type="range" min="1" max="200000" value="50" class="slider" id="range3">
 </div> 
</td>
<td style="vertical-align: top;text-align: center;" >
    <svg id="svg3" width="450" height="800"></svg>
</td>
<td style="vertical-align: top;">
<span id="explaindesc3" style="display: none;"> 
  <font size="4" style="text-align: center;">Every year, <b>115,551 people are shot</b>. Among those: </font>
</span>
<ul id="explain3" style="display: none;">
  <li>1,663 children and teens die from gun violence</li>
  <li>864 are murdered</li>
  <li>6,294 children and teens survive gunshot injuries</li>
  <li>2,788 are intentionally shot by someone else and survive</li>
  <li>662 die from gun suicide</li>
  <li>166 survive an attempted gun suicide</li>
  <li>10 are killed by legal intervention</li>
  <li>101 are shot by legal intervention and survive</li>
  <li>89 are killed unintentionally</li>
  <li>38 die but the intent was unknown</li>
  <li>380 are and survive shot but the intent is unknown</li>
</ul>
</td>
</tr>
</table>
 
<script src="//d3js.org/d3.v3.min.js"></script>
<script>



function update(n1, question_number) {

  
  var formatNumber = d3.format(",d");

var svg = d3.select("#svg" + question_number);

var width = +svg.attr("width"),
    height = +svg.attr("height");

var groupSpacing = 3,
    cellSpacing = 1,
    cellSize = Math.floor((width - 11 * groupSpacing) / 100) - cellSpacing,
    offset = Math.floor((width - 100 * cellSize - 90 * cellSpacing - 11 * groupSpacing) / 2);

var updateDuration = 125,
    updateDelay = updateDuration / 500;

var cell = svg.append("g")
    .attr("class", "cells")
    .attr("transform", "translate(" + offset + "," + (offset + 30) + ")")
  .selectAll("rect");

var label = svg.append("text")
    .attr("class", "label");
  
  var explanation = document.getElementById("explain" + question_number);
  var description = document.getElementById("explaindesc" + question_number);

  explanation.style.display="block";
  description.style.display="block";

  var n0 = cell.size();

  cell = cell
      .data(d3.range(n1));

  cell.exit().transition()
      .delay(function(d, i) { return (n0 - i) * updateDelay; })
      .duration(updateDuration)
      .attr("width", 0)
      .remove();

  cell.enter().append("rect")
      .attr("width", 0)
      .attr("height", cellSize)
      .attr("x", function(i) {
        var x0 = Math.floor(i / 100) % 10, x1 = Math.floor(i % 10);
        return groupSpacing * x0 + (cellSpacing + cellSize) * (x1 + x0 * 10);
      })
      .attr("y", function(i) {
        var y0 = Math.floor(i / 1000), y1 = Math.floor(i % 100 / 10);
        return groupSpacing * y0 + (cellSpacing + cellSize) * (y1 + y0 * 10);
      })
    .transition()
      .delay(function(d, i) { return (i - n0) * updateDelay; })
      .duration(updateDuration)
      .attr("width", cellSize);

  label
      .attr("x", offset + groupSpacing)
      .attr("y", offset + groupSpacing)
      .attr("dy", ".71em")
    .transition()
      .duration(Math.abs(n1 - n0) * updateDelay + updateDuration / 2)
      .ease("linear")
      .tween("text", function() {
        var i = d3.interpolateNumber(n0, n1);
        return function(t) {
          this.textContent = formatNumber(Math.round(i(t)));
        };
      });
}

d3.select(self.frameElement).style("height", height + "px");

</script>
