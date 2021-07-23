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
}
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
<td colspan="3" style="vertical-align:top;"><br><font size="5">Compare and contrast different states and death rates between 2014 & 2019. <b>Click the color coded cubes representing each state to the right to view the death rate curve across a 5 year period.</b> Use the quick link buttons to view the safest states and most dangerous states based on the number of gun related deaths.</font>
</td>
<td><img src="https://github.com/riyazomran/cs419-narrative-visualization/raw/gh-pages/legend.png" width="626" height="240"></td>
</tr>
</table>
<svg id="state_heat_map"></svg>
<svg id="graphSVG" width="1220" height="750" ></svg>





<script src="https://d3js.org/d3.v4.min.js" type="text/JavaScript"></script>
<script src="https://d3js.org/d3-scale-chromatic.v1.min.js"></script>  
<script src="https://d3js.org/colorbrewer.v1.min.js"></script>
<script src="https://rawgit.com/susielu/d3-annotation/master/d3-annotation.min.js"></script>
<script>

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
var groupByState=  d3.map(data, function(d){return d.STATE;}).keys();


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

var state = sumstat.map(d => d.STATE);
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
}
  

</script>
