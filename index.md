<style>
.cells {
  fill: #aaa;
}

.label {
  text-anchor: start;
  font: 24px sans-serif;
}
 
 .slidecontainer {
  width: 100%; /* Width of the outside container */
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
  background: #04AA6D; /* Green background */
  cursor: pointer; /* Cursor on hover */
}

.slider::-moz-range-thumb {
  width: 25px; /* Set a specific slider handle width */
  height: 25px; /* Slider handle height */
  background: #04AA6D; /* Green background */
  cursor: pointer; /* Cursor on hover */
}
</style>
<script>
    
function updateAnswer(questionNumber){
  var slider = document.getElementById("range" + questionNumber);
  var output = document.getElementById("your-answer" + questionNumber);
  output.innerHTML = slider.value;
}
</script>

<table border="0">
 <tr><td colspan="2" align="center"><img src="images.png"></td></tr>
 <tr>
  <td style="line-height: 150%;"><font size="8">W</font>e the people of the United States of America must start to recognize the inherant social costs of gun violence and the domino effect repercussions. The US gun homicide rate is 25 times that of other high-income countries. We find ourselves in a political quagmire that has paralyzed our nations legislative bodies. The truth however is in the data and the countless number of victims.  </td>
 </tr>
<table>
 
<div id="q1_slider_answer"><p align="center"><span id="your-answer1"></span></p></div>
<div class="slidecontainer" id="question1" onclick="updateAnswer(1);">
  <input type="range" min="1" max="1000" value="50" class="slider" id="range1">
</div> 
 <div>
  <svg width="600" height="600"></svg>
 </div>
 

<svg width="960" height="990"></svg>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>
var formatNumber = d3.format(",d");

var svg = d3.select("svg");

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

function update(n1) {
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

(function interval() {
  update(Math.floor(Math.random() * 100 * 100));
  setTimeout(interval, updateDelay * 100 * 100 + updateDuration + 1000);
})();

d3.select(self.frameElement).style("height", height + "px");

</script>

