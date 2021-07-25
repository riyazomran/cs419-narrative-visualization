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

<body onload="renderChart(5);">

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
<font size="5">TBD</font></p>
</td>
</table>

<div>
    <button id="scene1" class="button2"  onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/index';">1</button>
    <button id="scene2" class="button2" style="background-color:grey;color:white;" onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/scene2';">2</button>
    <button id="scene3" class="button2">3</button>
</div>
<div><hr></div>


<div id="stateBarChart"></div>

<button class="button2" onclick=" clearAndRender(2)">;
 TEST
</button>


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


function getYearsArray(data,numberOfYears){

var yearsArray = new Array(numberOfYears);

   for(var j=0; j < numberOfYears; j++){
     yearsArray[j] = 2014 + j;
   }
   
return yearsArray;

}

function yearRecordCount(data,numberOfYears){

var recordCount =0;
var yearsArray = getYearsArray(data, numberOfYears);

    for(var i=0; i < data.length; i++){
       
        var year = data[i].YEAR;

        if(yearsArray.includes(parseInt(year))){
            recordCount++;
        }
    }

return recordCount;

}

function createValueMap(data,numberOfYears){

    var valueArray = new Array(yearRecordCount(data,numberOfYears));
		var yearsArray = getYearsArray(data, numberOfYears);
    
    for(var i=0; i < data.length; i++){
       
        var year = data[i].YEAR;
       
         if(yearsArray.includes(parseInt(year))){
            valueArray[i] = data[i];
        }
    }
   
   return valueArray.filter(function (el) {
       return el != null;
    });

}

function totalDeathsByState(data,state){

var deaths =0;
for(var i=0; i < data.length; i++){
       
        var stateName = data[i].STATE;
       
        if(stateName == state){
            deaths = parseInt(data[i].DEATHS) + parseInt(deaths);
        }
    }
return deaths;
}


function buildStateDeathMappingArray(data,stateDomain){

	var stateDeathArray = new Array(50);
	
  for(var i=0; i < stateDomain.length; i++){
  
  	  var state = stateDomain[i];
      var deathsForState = totalDeathsByState(data, state);
  	  stateDeathArray [i] = deathsForState;
  }

  return stateDeathArray;
}

function lookupStateIndex(stateDomain, state){

 for(var i=0; i < stateDomain.length; i++){
  
  	  if(stateDomain[i] == state){
          return i;
      }
  }
  
  return 0;

}

function renderChart(years){

  d3.csv("https://raw.githubusercontent.com/riyazomran/cs419-narrative-visualization/gh-pages/cdcdata.csv",function(data) {
  data = createValueMap(data,years);

  var leftMargin=122;
  var topMargin=30;
  var margin = {top: 20, right: 25, bottom: 20, left: 122};
  var width = 1500 - margin.left - margin.right;
  var height = 900 - margin.top - margin.bottom;
  var svg = d3.select("graphSVG");

  var statesDomain=  d3.map(data, function(d){return d.STATE;}).keys();

  data = data.sort(function(a, b) {
    return d3.ascending(a.DEATHS, b.DEATHS)
  })

  var deathsDomain =  d3.map(data, function(d){return d.DEATHS;}).keys();
  var stateDeathValueArray = buildStateDeathMappingArray(data,statesDomain);

  var xExtent = d3.extent(data, d => d.STATE);
  xScale = d3.scaleBand().domain(statesDomain).range([leftMargin, width]).padding(0.4);


  var yMax=d3.max(stateDeathValueArray);
  yScale = d3.scaleLinear().domain([0, yMax +1000]).range([height , 0]);
  xAxis = d3.axisBottom().scale(xScale);

  var graphSVG = d3.select("#stateBarChart")
  .append("svg")
    .attr("width", width)
    .attr("height", height + 300);

      graphSVG.append("g")
      .attr("class", "axis")
      .attr("transform", "translate(0," + height + ")")
      .call(xAxis)
      .selectAll("text")
      .style("text-anchor", "end")
      .attr("dx", "-.8em")
      .attr("dy", ".15em")
      .attr("transform", "rotate(-65)")
      .append("text")
      .attr("x", (1500+70)/2)
      .attr("y", "10")
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
      .attr("x", "-200")
      .attr("y", "-70")
      .attr("text-anchor", "end")
      .text("Total Number of Deaths");

  graphSVG.selectAll("rect")
      .append("g")
      .data(data)
      .enter()
      .append("rect").transition().duration(4000)
      .attr("x", d => xScale(d.STATE))
      .attr("y", d => yScale(stateDeathValueArray[lookupStateIndex(statesDomain,d.STATE)]))
      .attr("width",  xScale.bandwidth())
      .attr("height", function(d) { return height - yScale(stateDeathValueArray[lookupStateIndex(statesDomain,d.STATE)]); })
      .attr("fill", function(d) {
      
      var deaths = stateDeathValueArray[lookupStateIndex(statesDomain,d.STATE)];
      if (deaths>(yMax * .80)) {
        return "red";
      } else if (deaths < (yMax * .80) && deaths > (yMax * .25)) {
        return "orange";
      }
      return "green";
    });
    
    const annotations = data.map(function(d, i){
    
        return {
          note: {
            title: "Test",
            label: "1",
            wrap: 100, 
            align: 'right', 
          },
          connector: {end: 'arrow'}, 
          x: xScale(d.STATE),
          y: yScale(stateDeathValueArray[lookupStateIndex(statesDomain,d.STATE)]),
          dy: xScale.bandwidth(), 
          dx: height - yScale(stateDeathValueArray[lookupStateIndex(statesDomain,d.STATE)]),
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

  })
}

function clearAndRender(years){
   d3.select("#stateBarChart").selectAll("*").remove();
   renderChart(years);
}

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


  

</script>

</body>
