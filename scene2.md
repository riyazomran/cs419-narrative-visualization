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


<table>
<tr>
<td><img src="images.png"></td>
<td style="vertical-align: middle;" class="banner banner0">
    <font size="10" color="#ffffff">Cost of Gun Violence in America </font>
</td>
</tr>
</table>

<table>
<tr>
<td colspan="3" style="vertical-align:top;"><br><p>
<font size="5">Compare and contrast different states with highest level of gun violence (least restrictive gun polcies) vs. those with the lowest level of gun violence (most restrictive gun policies) between 2014 - 2019. <b>Click the color coded cubes at opposite ends of the spectrum to select your home state and compare it to other states across a 5 year period. </b></font></p>
<p> <font size="5">Take note that the death rates shown across the year is color coded with the thresholds mapped to years of highest level of gun violence vs. lowest levels of gun violence. <br><i>For example compare <b><font color="blue">Hawaii</font></b> to <font color="red">Wyoming</font> year-over-year to see how state gun policies impact death rates.</i></font>.</p>
</td>
<td><img src="https://github.com/riyazomran/cs419-narrative-visualization/raw/gh-pages/legend.png" width="626" height="240"></td>
</tr>
</table>

<div>

<div class="w3-light-grey">
  <div class="w3-blue" style="height:24px;width:75%"></div>
</div>
<div>Challenge Question &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Choose Your Path &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Explore Gun Violence by State</div>

</div><br>

<div>
    <button id="scene1" class="button2"  onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/index';">Start Over</button>
    <button id="scene2" class="button2"  onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/chooseyourpath';">Expore More: Choose Your Path</button>
    <button id="quickLink1" class="button2" onclick="clearGraph();">Reset Visualization</button>
</div>
<div><hr></div>

<div id="graphTitle" style="text-align : left; display:none;"><font size="6">  &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gun Violence State Death Rate by Year (2014-2019)</font><br></div>
<svg id="state_heat_map"></svg>
<svg id="graphSVG" width="1220" height="750" ></svg>
<div id="learnmore" style="display:none;">
<font size="6"> Learn More Through CDC Wonder Data</font><br>
<iframe id="learnMoreCDC" src="" title="Dig Deeper with CDC Wonder Data" width="1200" height="800" style="display:none;">
</iframe>
  
</div>





<script src="https://d3js.org/d3.v4.min.js" type="text/JavaScript"></script>
<script src="https://d3js.org/d3-scale-chromatic.v1.min.js"></script>  
<script src="https://d3js.org/colorbrewer.v1.min.js"></script>
<script src="https://rawgit.com/susielu/d3-annotation/master/d3-annotation.min.js"></script>
<script>

function clearGraph() {
    location.reload();
}

function clearAnnotations() {
   d3.selectAll(".annotation-group").remove();
}

function colorLogic(rate, option){

  if(option == 1){
     return " rgb(128,128,128)";
  } else {
 
     if(rate > 19){
        return "rgb(255, 0, 0)";
     } else if (rate <19 && rate >15){
        return "rgb(0, 191, 255)";
     } else if (rate <15 && rate >9){
        return "rgb(0, 128, 255)";
     } else if(rate <9 && rate >5){
        return "rgb(0, 64, 255)";
     } else {
        return "rgb(0, 0, 255)";
     }
 }
}

 function stateBubbleSort(arr, stateDomain) {

        for (var i = 0; i < arr.length; i++) {

          for (var j = 0; j < (arr.length - i - 1); j++) {

            if (arr[j].DEATHS > arr[j + 1].DEATHS) {

              var temp = arr[j];
              arr[j] = arr[j + 1];
              arr[j + 1] = temp;

              var temp2 = stateDomain[j];
              stateDomain[j] = stateDomain[j + 1];
              stateDomain[j + 1] = temp2;

            }
          }
        }
      }


d3.csv("https://raw.githubusercontent.com/riyazomran/cs419-narrative-visualization/gh-pages/Wonder-CDC-US%20-States-Gun-Violence.csv",function(data) {


// set the dimensions and margins of the graph
var margin = {top: 20, right: 25, bottom: 20, left: 120},
  width = 200 - margin.left - margin.right,
  height = 750 - margin.top - margin.bottom;

// append the svg object to the body of the page
var svg = d3.select("#state_heat_map")
  .attr("width", width + margin.left + margin.right)
  .attr("height", height + margin.top + margin.bottom)
.append("g")
  .attr("transform",
        "translate(" + margin.left + "," + margin.top + ")");

var groupByYears = d3.map(data, function(d){return d.YEAR;}).keys();
var groupByState=  d3.map(data, function(d){return d.STATE;}).keys().reverse();

//stateBubbleSort(data,groupByState);

var x = d3.scaleBand()
    .range([ 0, width ])
    .domain(groupByYears)
    .padding(0.05);
  svg.append("g")
    .style("font-size", 15)
    .attr("transform", "translate(0," + height + ")")
    .call(d3.axisBottom(x).tickSize(0))
    .select(".domain").remove();

  // Build Y scales and axis:
  var y = d3.scaleBand()
    .range([height, 0 ])
    .domain(groupByState)
    .padding(0.05);
    
  svg.append("g")
    .style("font-size", 15)
    .call(d3.axisLeft(y).tickSize(0))
    .select(".domain").remove();
   
      var myColor = d3.scaleLinear().domain([1,26]);

 
     
      //d3.scaleSequential()
    //.interpolator(d3.interpolateInferno)
    //.domain([1,25])
   
      var Tooltip = d3.select("#state_heat_map")
    .append("div")
    .style("opacity", 0)
    .attr("class", "tooltip")
    .style("background-color", "white")
    .style("border", "solid")
    .style("border-width", "2px")
    .style("border-radius", "5px")
    .style("padding", "5px");
   
    var mouseover = function(d) {
    Tooltip
      .style("opacity", 1);
    d3.select(this)
      .style("stroke", "black")
      .style("opacity", 1);
  }
  var mousemove = function(d) {
    Tooltip
      .html("State Gun Related Death Rate " + d.RATE)
      .style("left", (d3.mouse(this)[0]+70) + "px")
      .style("top", (d3.mouse(this)[1]) + "px");
  }
  var mouseleave = function(d) {
    Tooltip
      .style("opacity", 0);
    d3.select(this)
      .style("stroke", "none")
      .style("opacity", 0.8);
  }
 
  var onclick = function(d) {
d3.csv("https://raw.githubusercontent.com/riyazomran/cs419-narrative-visualization/gh-pages/cdcdata.csv",function(data) {
			lineChart(data,d.STATE);
});
  }


    svg.selectAll()
    .data(data, function(d) {return d.YEAR+':'+d.STATE;})
    .enter()
    .append("rect")
      .attr("x", function(d) { return x(d.YEAR) })
      .attr("y", function(d) { return y(d.STATE) })
      .attr("rx", 4)
      .attr("ry",4)
      .attr("width", x.bandwidth())
      .attr("height", y.bandwidth())
      .style("fill", function(d) { return colorLogic(d.RATE,2)} )
      .style("stroke-width", 4)
      .style("stroke", "none")
      .style("opacity", 0.8)
    .on("mouseover", mouseover)
    .on("mousemove", mousemove)
    .on("mouseleave", mouseleave)
    .on("click",onclick);
    
    

})

function stateRecordCount(data,state){

var recordCount =0;
for(var i=0; i < data.length; i++){
       
        var stateName = data[i].STATE;
       
        if(stateName == state){
            recordCount++;
        }
    }
return recordCount;
}

function getCDCURL(data,state){

var recordCount =0;
for(var i=0; i < data.length; i++){
       
        var stateName = data[i].STATE;
       
        if(stateName == state){
            return data[i].URL;
        }
    }
return "-1";
}

function refine(data,state){

    var array = new Array(stateRecordCount(data,state));
    var j =0;
   
    for(var i=0; i < data.length; i++){
       
        var stateName = data[i].STATE;
       
        if(stateName == state){
            array[j] = data[i];
            j++;
        }
    }

  return array;
}

function lineChart(data, state) {

document.getElementById("learnmore").style.display="block";
document.getElementById("graphTitle").style.display="block";
document.getElementById("learnMoreCDC").src= "https://www.cdc.gov/" + getCDCURL(data,state);
document.getElementById("learnMoreCDC").style.display ="block";
data= refine(data,state);

//set canvas margins
var leftMargin=70;
var topMargin=30;

//format the year
var parseTime = d3.timeParse("%Y");

data.forEach(function (d) {
    d.YEAR = parseTime(d.YEAR);
});


var xExtent = d3.extent(data, d => d.YEAR);
xScale = d3.scaleTime().domain(xExtent).range([leftMargin, 900]);


var yMax=d3.max(data,d=>d.RATE);
yScale = d3.scaleLinear().domain([0, 25]).range([600, 0]);

xAxis = d3.axisBottom()
    .scale(xScale);
   
var graphSVG = d3.select("#graphSVG")
.append("svg")
  .attr("width", "1500")
  .attr("height", "750");
   
    graphSVG.append("g")
    .attr("class", "axis")
    .attr("transform", "translate(0,620)")
    .call(xAxis)
    .append("text")
    .attr("x", (900+70)/2)
    .attr("y", "50")
    .text("Year");


yAxis = d3.axisLeft()
    .scale(yScale)
    .ticks(10);

graphSVG.append("g")
    .attr("class", "axis")
    .attr("transform", `translate(${leftMargin},20)`)
    .call(yAxis)
    .append("text")
    .attr("transform", "rotate(-90)")
    .attr("x", "-150")
    .attr("y", "-50")
    .attr("text-anchor", "end")
    .text("Death Rate");

yAxis = d3.axisLeft()
    .scale(yScale)
    .ticks(10);


var sumstat = d3.nest()
    .key(d => d.STATE)
    .entries(data);

//var state = sumstat.map(d => d.STATE);
var color = d3.scaleOrdinal().domain(state).range(colorbrewer.Set2[6]);

graphSVG.selectAll(".line")
    .append("g")
    .attr("class", "line")
    .data(sumstat)
    .enter()
    .append("path")
    .attr("d", function (d) {
        return d3.line()
            .x(d => xScale(d.YEAR))
            .y(d => yScale(d.RATE)).curve(d3.curveCardinal)
            (d.values)
    })
    .attr("fill", "none")
    .attr("stroke", d => color(d.key))
    .attr("stroke-width", 2);

graphSVG.selectAll("circle")
    .append("g")
    .data(data)
    .enter()
    .append("circle").transition()
    .duration(5000)
    .attr("r", 6)
    .attr("cx", d => xScale(d.YEAR))
    .attr("cy", d => yScale(d.RATE))
    .style("fill", d => color(.094));


const annotations = data.map(function(d, i){
    return {
      note: {
        title: d.RATE,
        label: d.STATE,
        wrap: 100, 
        align: 'right', 
      },
      connector: {end: 'arrow'}, 
      x: xScale(+d.YEAR),
      y: yScale(+d.RATE),
      dy: 10, 
      dx: 70,
      color: colorLogic( d.RATE,0) 
    }
  })

  const makeAnnotations = d3.annotation()
    .type(d3.annotationCalloutCircle)
    .annotations(annotations)

  graphSVG
    .append("g")
    .attr("class", "annotation-group")
    .call(makeAnnotations)

   var dynamicAnnotations = ["Hawaii : Violent crime rate: 309.2 per 100,000 (21st lowest)|Poverty rate: 9.3% (2nd lowest)", "Alabama: Violent crime rate: 532.3 per 100,000 (7th highest)|Poverty rate: 17.1% (7th highest)", "Alaska : Violent crime rate: 804.2 per 100,000 (the highest) | Poverty rate: 9.9% (6th lowest)","Arizona : Violent crime rate: 470.1 per 100,000 (12th highest)|Poverty rate: 16.4% (8th highest)","Arkansas : Violent crime rate: 550.9 per 100,000 (6th highest)|Poverty rate: 17.2% (6th highest)","California : Violent crime rate: 445.3 per 100,000 (15th highest)|Poverty rate: 14.3% (20th highest)", "Colorado : Total firearm deaths 2016: 812 (suicides: 613, homicides: 161)|Poverty rate: 11.0% (12th lowest)", "Connecticut : Violent crime rate: 227.1 per 100,000 (5th lowest)|Poverty rate: 9.8% (4th lowest)","Delaware : Violent crime rate: 508.8 per 100,000 (9th highest)|Poverty rate: 11.7% (16th lowest)", "Florida : Violent crime rate: 430.3 per 100,000 (18th highest)|Poverty rate: 14.7% (16th highest)", "Georgia : Violent crime rate: 397.6 per 100,000 (21st highest)|Poverty rate: 16.0% (10th highest)","Idaho : Violent crime rate: 230.3 per 100,000 (6th lowest) | Violent crime rate: 230.3 per 100,000 (6th lowest)", "Illinois : Violent crime rate: 436.3 per 100,000 (16th highest)|Poverty rate: 13.0% (24th lowest)", "Indiana : Violent crime rate: 404.7 per 100,000 (20th highest)|Poverty rate: 14.1% (21st highest)","Iowa : Violent crime rate: 290.6 per 100,000 (16th lowest) | Poverty rate: 11.8% (18th lowest)","Kansas : Violent crime rate: 380.4 per 100,000 (22nd highest) | Poverty rate: 12.1% (20th lowest)", "Kentucky : Violent crime rate: 232.3 per 100,000 (7th lowest)|Poverty rate: 18.5% (4th highest)", " Louisiana : Violent crime rate: 566.1 per 100,000 (5th highest)|Poverty rate: 20.2% (2nd highest)", "Maine : Violent crime rate: 123.8 per 100,000 (the lowest) | Violent crime rate: 123.8 per 100,000 (the lowest)", "Maryland : Violent crime rate: 472.0 per 100,000 (11th highest)|Poverty rate: 9.7% (3rd lowest)", "Massachusetts : Violent crime rate: 376.9 per 100,000 (23rd highest)| Poverty rate: 10.4% (9th lowest)", "Michigan : Violent crime rate: 459.0 per 100,000 (13th highest)|Poverty rate: 15.0% (15th highest)", "Minnesota : Violent crime rate: 242.6 per 100,000 (9th lowest)|Poverty rate: 9.9% (6th lowest)", "Missouri : Violent crime rate: 519.4 per 100,000 (8th highest)|Violent crime rate: 519.4 per 100,000 (8th highest)","Montana : Violent crime rate: 368.3 per 100,000 (25th lowest)|Poverty rate: 13.3% (24th highest)", "Nebraska : Violent crime rate: 291.0 per 100,000 (17th lowest)|Poverty rate: 11.4% (15th lowest)","Nevada : Violent crime rate: 678.1 per 100,000 (3rd highest)|Poverty rate: 13.8% (23rd highest)", "New Hampshire : Violent crime rate: 197.6 per 100,000 (3rd lowest)|Poverty rate: 7.3% (the lowest)", "New Jersey : Violent crime rate: 245.0 per 100,000 (12th lowest) | Poverty rate: 10.4% (9th lowest)", " New Mexico : Violent crime rate: 702.5 per 100,000 (2nd highest) | Poverty rate: 19.8% (3rd highest)" , " New York :Violent crime rate: 376.2 per 100,000 (24th highest)| Poverty rate: 14.7% (16th highest)","North Carolina : Violent crime rate: 372.2 per 100,000 (25th highest)| Poverty rate: 15.4% (13th highest)", "North Dakota : Violent crime rate: 251.1 per 100,000 (13th lowest) | Poverty rate: 10.7% (10th lowest)", " Ohio : Violent crime rate: 300.3 per 100,000 (18th lowest) | Poverty rate: 14.6% (18th highest)","Oklahoma : Violent crime rate: 449.8 per 100,000 (14th highest)|Poverty rate: 16.3% (9th highest)", "Oregon : Violent crime rate: 264.6 per 100,000 (14th lowest) | Poverty rate: 13.3% (24th highest)", " Pennsylvania : Violent crime rate: 316.4 per 100,000 (22nd lowest)| Poverty rate: 12.9% (23rd lowest)", "Rhode Island : Violent crime rate: 238.9 per 100,000 (8th lowest)|Poverty rate: 12.8% (22nd lowest)", "South Carolina : Violent crime rate: 501.8 per 100,000 (10th highest)|Poverty rate: 15.3% (14th highest)", "South Dakota : Violent crime rate: 418.4 per 100,000 (19th highest)|Poverty rate: 13.3% (24th highest)", "Tennessee : Violent crime rate: 632.9 per 100,000 (4th highest)|Poverty rate: 15.8% (11th highest)", "Texas : Violent crime rate: 434.4 per 100,000 (17th highest) | Poverty rate: 15.6% (12th highest)", "Utah : Violent crime rate: 242.8 per 100,000 (10th lowest) | Poverty rate: 10.2% (7th lowest)", "Vermont : Violent crime rate: 158.3 per 100,000 (2nd lowest)|Poverty rate: 11.9% (19th lowest) ", "Virginia : Violent crime rate: 217.6 per 100,000 (4th lowest)|Poverty rate: 11.0% (12th lowest)", "Washington : Violent crime rate: 302.2 per 100,000 (19th lowest)|Poverty rate: 11.3% (14th lowest)", "West Virginia :Violent crime rate: 358.1 per 100,000 (24th lowest)| Poverty rate: 17.9% (5th highest) ", "Wisconsin : Violent crime rate: 305.9 per 100,000 (20th lowest)|Poverty rate: 11.8% (18th lowest) ", "Wyoming : Violent crime rate: 244.2 per 100,000 (11th lowest)|Poverty rate: 11.3% (14th lowest)"];
   
	 var dynamicAnnotationsIndex = ["Hawaii", "Alabama","Alaska", "Arizona", "Arkansas", "California", "Colorado", "Connecticut", "Delaware", "Florida", "Georgia", "Idaho", "Illinois", "Indiana","Iowa","Kansas", "Kentucky", "Louisiana", "Maine", "Maryland", "Massachusetts", "Michigan", "Minnesota", "Missouri","Montana", "Nebraska", "Nevada", "New Hampshire", "New Jersey", "New Mexico", "New York", "North Carolina", "North Dakota", "Ohio", "Oklahoma", "Oregon", "Pennsylvania", "Rhode Island", "South Carolina", "South Dakota", "Tennessee", "Texas", "Utah", "Vermont", "Virginia", "Washington", "West Virginia", "Wisconsin", "Wyoming"];
   
 	 var dynamicAnnotationsCoordinates = ["900.01587301587307|494.4|-100.46825396825403|270", "900|67|10.46825396825403|270", "900|14.399999999999977|10.46825396825403|270", "900|237.60000000000002|10.46825396825403|270", "900|136.8|10.46825396825403|270", "900|427.2|10.46825396825403|270", "900|259.20000000000005|10.46825396825403|270", "900|472.8|10.46825396825403|270", "900|362.4|10.46825396825403|270", "900|295.2|10.46825396825403|270", "900|220.8|10.46825396825403|270",  "900|259.20000000000005|10.46825396825403|270", "900|340.79999999999995|10.46825396825403|270",  "900|261.6|10.46825396825403|270", "900|381.6|10.46825396825403|270", "900|271.20000000000005|10.46825396825403|270", "900|242.40000000000003|10.46825396825403|270", "900|69.60000000000002|10.46825396825403|270", "900|324|10.46825396825403|270", "900|324|10.46825396825403|270", "900|518.4|10.46825396825403|270", "900|309.6|10.46825396825403|270", "900|309.6|10.46825396825403|270", "900|105.59999999999997|10.46825396825403|270", "900|144|10.46825396825403|270", "900|350.4|10.46825396825403|270", "900|232.8|10.46825396825403|270", "900|343.28|10.46825396825403|270", "900|501.6|10.46825396825403|270", "900|64.79999999999995|10.46825396825403|270" , "900|506.4|10.46825396825403|270", "900|285.59999999999997|10.46825396825403|270", "900|302.4|10.46825396825403|270", "900|280.79999999999995|10.46825396825403|270", "900|297.6|10.46825396825403|270", "900|297.6|10.46825396825403|270",  "900|319.20000000000005|10.46825396825403|270",  "900|489.6|10.46825396825403|270",  "900|122.40000000000003|10.46825396825403|270", "900|285.59999999999997|10.46825396825403|270", "900|158.40000000000003|10.46825396825403|270", "900|295.2|10.46825396825403|270",  "900|292.8|10.46825396825403|270",  "900|376.79999999999995|10.46825396825403|270",  "900|319.20000000000005|10.46825396825403|270",  "900|343.2|10.46825396825403|270",  "900|201.59999999999997|10.46825396825403|270",  "900|360|10.46825396825403|270",  "900|64.79999999999995|10.46825396825403|270"];  


   function getAnnotationIndex(state){
   	    
        for(var i=0; i < dynamicAnnotationsIndex.length; i++){
        	   if(state == dynamicAnnotationsIndex[i]){
             			return i;
             }
        }
   }
   
   function getTitleLabel(state){
   
   		var index = getAnnotationIndex(state);   
      var splitArray = String(dynamicAnnotations[index]).split("|");

   		return splitArray;
   
   }
   
   function getCoordinates(state){
   
   		var index = getAnnotationIndex(state);
      var splitArray = String(dynamicAnnotationsCoordinates[index]).split("|");
   
   		return splitArray;
   
   }

   const annotation1 = [{

            note: {
              title: getTitleLabel(state)[0],
              label: getTitleLabel(state)[1],
              wrap: 200,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: parseInt(getCoordinates(state)[0]),
            y:  parseInt(getCoordinates(state)[1]),
            dy: parseInt( getCoordinates(state)[2]),
            dx:  parseInt(getCoordinates(state)[3]),
            color: "black"
          },
          
          ];

          const makeAnnotations1 = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation1);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations1);
}
  

</script>
