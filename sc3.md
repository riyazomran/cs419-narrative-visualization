<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
<style>
  .axis path {
    stroke: black;
    stroke-width: 2px;
  }

  .axis line {
    stroke: black;
    stroke-width: 1.5px;
  }

  .axis text {
    fill: black;
    font-weight: bold;
    font-size: 14px;
    font-family: "Arial Black", Gadget, sans-serif;
  }

  .legend text {
    fill: black;
    font-family: "Arial Black", Gadget, sans-serif;
  }

  .body {
    font-family: 'Courier New', monospace;
  }

  .banner {
    width: 100%;
    height: 200px;
    margin: 7px auto;
    -moz-box-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
    -webkit-box-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
    -moz-border-radius: 15px;
    -webkit-border-radius: 15px;

  }

  .banner0 {
    background: #0066cc url(banner0.png) no-repeat center left;
  }

  .cells {
    fill: #bf3737;
  }

  .label {
    text-anchor: start;
    font: 24px sans-serif;
  }

  .slidecontainer {
    width: 90%;
    /* Width of the outside container */
  }

  /* The slider itself */
  .slider {
    -webkit-appearance: none;
    /* Override default CSS styles */
    appearance: none;
    width: 100%;
    /* Full-width */
    height: 25px;
    /* Specified height */
    background: #d3d3d3;
    /* Grey background */
    outline: none;
    /* Remove outline */
    opacity: 0.7;
    /* Set transparency (for mouse-over effects on hover) */
    -webkit-transition: .2s;
    /* 0.2 seconds transition on hover */
    transition: opacity .2s;
  }

  /* Mouse-over effects */
  .slider:hover {
    opacity: 1;
    /* Fully shown on mouse-over */
  }

  /* The slider handle (use -webkit- (Chrome, Opera, Safari, Edge) and -moz- (Firefox) to override default look) */
  .slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    /* Override default look */
    appearance: none;
    width: 25px;
    /* Set a specific slider handle width */
    height: 25px;
    /* Slider handle height */
    background: #0066cc;
    /* Green background */
    cursor: pointer;
    /* Cursor on hover */
  }

  .slider::-moz-range-thumb {
    width: 25px;
    /* Set a specific slider handle width */
    height: 25px;
    /* Slider handle height */
    background: #04AA6D;
    /* Green background */
    cursor: pointer;
    /* Cursor on hover */
  }

  .button {
    transition-duration: 0.4s;
  }

  .button:hover {
    background-color: #4CAF50;
    /* Green */
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

  .axis path {
    stroke: black;
    stroke-width: 2px;
  }

  .axis line {
    stroke: black;
    stroke-width: 1.5px;
  }

  .axis text {
    fill: black;
    font-weight: bold;
    font-size: 14px;
    font-family: "Arial Black", Gadget, sans-serif;
  }

  .legend text {
    fill: black;
    font-family: "Arial Black", Gadget, sans-serif;
  }

</style>

<body onload="renderChart(1,0);">

  <input id="sortState" type="hidden" value="-1">
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
      <td colspan="3" style="vertical-align:top;"><br>
        <p>
          <font size="4">In the previous visualization we focused on comparing death rate trends between states across 5 year period. In this slide we will start look at raw number of deaths by state and how gun violence actually impacts each life from state-to-state. We will also see if there are variances or change in gun violence in various year ranges between 2014-2019.  In the visualization below you will find quick link buttons that allow you to: <b><br>&nbsp;&nbsp;&nbsp;&nbsp;(1) View the data sorted year-over-year: <br>&nbsp;&nbsp;&nbsp; (2) View additional details of states with consistently high death counts year-over-year <br>&nbsp;&nbsp;&nbsp;&nbsp;(3) States that have historically show the lowest death counts year-over-year.</b></font><br>   
        </p>
        <p>
         <font size="4">Lastly use the slider below the visualization to view changes in gun violence across different periods of time OR limit the number of deaths to a specific threshold to see the states to see the states that fall under that threshold.</font>
        </p>
      </td>
    </tr>
  </table>
<div>

<div class="w3-light-grey" style="width:700px;">
  <div class="w3-blue" style="height:24px;width:100%"></div>
</div>
<div>Challenge Question &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Choose Your Path &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Explore Gun Violence by State</div>

</div><br>
  <div>
    <button id="scene1" class="button2"  onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/index';">Start Over</button>
    <button id="scene2" class="button2"  onclick="location.href = 'https://riyazomran.github.io/cs419-narrative-visualization/chooseyourpath';">Expore More: Choose Your Path</button>
  </div>

  <div>
    <hr>
  </div>
  <div>
    &nbsp;&nbsp;&nbsp;&nbsp;<button id="quickLink1" class="button2" onclick="clearFlags();">Clear Flags</button>
    <button id="quickLink4" class="button2" onclick="clearAndRender(parseInt(2019)- ((parseInt(2019) - document.getElementById('range1').value) + parseInt(2014)),'bubblesort'); document.getElementById('sortState').value=0;">Sort in Ascending Order (View Year-over-Year Variance in Rankings)</button>
  </div>
  <br>
  <div id="stateBarChart"></div>

  <br>
  <font size="5" color="#0066cc;"><b>
      <div id="sliderDateRange" style="color:#0066cc;text-align: center;">Gun Violence Data for 2014-2015 Time Period</div>
    </b></font>

  <div class="slidecontainer" id="question1" style="white-space: nowrap;">
    <font size="5"><b>1 Year</b></font> &nbsp;<input type="range" min="2014" max="2019" value="1" class="slider" id="range1" onclick="clearAndRender(parseInt(2019)- ((parseInt(2019) - this.value) + parseInt(2014)));">&nbsp;<font size="5"><b>5 Year</b></font>
  </div>
  <br>
    <font size="5" color="#0066cc;"><b>
      <div id="sliderDateRange2" style="color:#0066cc;text-align: center;">Aggregate Deaths Across Period of Time - <span id="sliderDeathCnt">3000</span></div>
    </b></font>
<div class="slidecontainer" id="question2" style="white-space: nowrap;">
    <font size="5"><b>100 Death</b></font> &nbsp;<input type="range" min="100" max="16000" value="3000" class="slider" id="range2" onclick="clearAndRenderByDeathCnt(this.value, 'deathCntSlider');document.getElementById('sliderDeathCnt').innerHTML = this.value;">&nbsp;<font size="5"><b>16,000 Deaths</b></font>
</div>


  <span id="your-answer1" style="color:#0066cc;font-size:20px;">
    <script src="https://d3js.org/d3.v4.min.js" type="text/JavaScript"></script>
    <script src="https://d3js.org/d3-scale-chromatic.v1.min.js"></script>
    <script src="https://d3js.org/colorbrewer.v1.min.js"></script>
    <script src="https://rawgit.com/susielu/d3-annotation/master/d3-annotation.min.js"></script>

    <script>
      function clearFlags() {
        d3.selectAll(".annotation-group").remove();
      }


      function flagWithLowestGunViolence() {
				//clearAndRender(document.getElementById("range1").value, "");
        var graphSVG = d3.selectAll("svg");
        var sortState = document.getElementById("sortState").value;

        if (sortState == -1) {

          const annotation1 = [{
            note: {
              title: "Hawaii : 40 Deaths on Average",
              label: "#1 state with lowest number of deaths related to gun violence (not per capita)",
              wrap: 100,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: 376.01587301587307,
            y: 608.3072739632903,
            dy: -350.46825396825403,
            dx: 300,
            color: "black"
          }];

          const makeAnnotations = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation1);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations);

        } else {

          const annotation1 = [{
            note: {
              title: "Rhode Island & Hawaii : 34 & 40 Deaths on Average per Year",
              label: "The 2 state with lowest number of deaths related to gun violence (not per capita)",
              wrap: 100,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: 156.19444444444449,
            y: 608.30727396329033,
            dy: -350.46825396825403,
            dx: 300,
            color: "black"
          }];

          const makeAnnotations = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation1);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations);


        }
      }


      function flagStatesWithHighGunViolence() {

				//clearAndRender(document.getElementById("range1").value, "");
        var graphSVG = d3.selectAll("svg");
        var sortState = document.getElementById("sortState").value;
        
        if (sortState == -1) {

          const annotation1 = [{
            note: {
              title: "California : 3683 Deaths on Average",
              label: "#1 top states highest death counts (not per capita)",
              wrap: 100,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: 229,
            y: -10,
            dy: 50.46825396825403,
            dx: 300,
            color: "black"
          }];


          const annotation2 = [{
            note: {
              title: "Texas: 2945 Deaths on Average",
              label: "#2 top state with highest gun related death counts (not per capita)",
              wrap: 100,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: 1157.6031746031745,
            y: -10,
            dy: 140.46825396825403,
            dx: 300,
            color: "black"
          }];


          const annotation3 = [{
            note: {
              title: "Florida: 2872 Deaths on Average",
              label: "#3 top state with highest gun related death counts (not per capita)",
              wrap: 100,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: 327.16666666666674,
            y: -10,
            dy: 80,
            dx: 10.654761904761903,
            color: "black"
          }];


          const makeAnnotations = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation1);

          const makeAnnotations2 = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation2);

          const makeAnnotations3 = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation3);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations2);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations3);

        } else {

          const annotation1 = [{
            note: {
              title: "California : 2945 Deaths on Average",
              label: "#2 top states highest death counts (not per capita)",
              wrap: 100,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: 1350,
            y: 0,
            dy: 200.46825396825403,
            dx: -400,
            color: "black"
          }];


          const annotation2 = [{
            note: {
              title: "Texas: 3683 Deaths on Average",
              label: "#1 top state with highest gun related death counts (not per capita)",
              wrap: 100,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: 1300.6031746031745,
            y: 0,
            dy: 180.46825396825403,
            dx: 150,
            color: "black"
          }];


          const annotation3 = [{
            note: {
              title: "Florida: 2872 Deaths on Average",
              label: "#3 top state with highest gun related death counts (not per capita)",
              wrap: 100,
              align: 'right',
            },
            connector: {
              end: 'arrow'
            },
            x: 1279.7261904761904,
            y: 220,
            dy: 10,
            dx: -200.654761904761903,
            color: "black"
          }];


          const makeAnnotations = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation1);

          const makeAnnotations2 = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation2);

          const makeAnnotations3 = d3.annotation()
            .type(d3.annotationCalloutCircle)
            .annotations(annotation3);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations2);

          graphSVG
            .append("g")
            .attr("class", "annotation-group")
            .call(makeAnnotations3);


        }
      }

      function getRandomInt(max) {
        return Math.floor(Math.random() * max);
      }

      function colorLogic(rate, option) {

        if (option == 1) {
          return " rgb(128,128,128)";
        } else {

          if (rate > 19) {
            return "rgb(255, 0, 0)";
          } else if (rate < 19 && rate > 15) {
            return "rgb(0, 191, 255)";
          } else if (rate < 15 && rate > 9) {
            return "rgb(0, 128, 255)";
          } else if (rate < 9 && rate > 5) {
            return "rgb(0, 64, 255)";
          } else {
            return "rgb(0, 0, 255)";
          }
        }
      }


      function getYearsArray(data, numberOfYears) {

        var yearsArray = new Array(numberOfYears);

        for (var j = 0; j < numberOfYears; j++) {
          yearsArray[j] = 2014 + j;
        }

        return yearsArray;

      }

      function yearRecordCount(data, numberOfYears) {

        var recordCount = 0;
        var yearsArray = getYearsArray(data, numberOfYears);

        for (var i = 0; i < data.length; i++) {

          var year = data[i].YEAR;

          if (yearsArray.includes(parseInt(year))) {
            recordCount++;
          }
        }

        return recordCount;

      }

      function createValueMap(data, numberOfYears) {

        var valueArray = new Array(yearRecordCount(data, numberOfYears));
        var yearsArray = getYearsArray(data, numberOfYears);

        for (var i = 0; i < data.length; i++) {

          var year = data[i].YEAR;

          if (yearsArray.includes(parseInt(year))) {
            valueArray[i] = data[i];
          }
        }

        return valueArray.filter(function(el) { return el != null;});

      }
      
      function createDeathCntMap(data, deathCount) {

        var valueArray = new Array(data.length);

        for (var i = 0; i < data.length; i++) {

          var deaths = data[i].DEATHS;

          if (parseInt(deaths) <= parseInt(deathCount)){
            console.log(deaths);
            valueArray[i] = data[i];
          }
        }

        return valueArray.filter(function(el) {return el != null;});

      }

      function totalDeathsByState(data, state) {

        var deaths = 0;
        for (var i = 0; i < data.length; i++) {

          var stateName = data[i].STATE;

          if (stateName == state) {
            deaths = parseInt(data[i].DEATHS) + parseInt(deaths);
          }
        }
        return deaths;
      }


      function buildStateDeathMappingArray(data, stateDomain) {

        var stateDeathArray = new Array(50);

        for (var i = 0; i < stateDomain.length; i++) {

          var state = stateDomain[i];
          var deathsForState = totalDeathsByState(data, state);
          stateDeathArray[i] = deathsForState;

        }

        return stateDeathArray;
      }

      function lookupStateIndex(stateDomain, state) {

        for (var i = 0; i < stateDomain.length; i++) {

          if (stateDomain[i] == state) {
            return i;
          }
        }

        return 0;

      }

      function stateBubbleSort(arr, stateDomain) {

        for (var i = 0; i < arr.length; i++) {

          for (var j = 0; j < (arr.length - i - 1); j++) {

            if (arr[j] > arr[j + 1]) {

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

      function renderChart(years, quicklink) {

        d3.csv("https://raw.githubusercontent.com/riyazomran/cs419-narrative-visualization/gh-pages/cdcdata.csv", function(data) {
          data = createValueMap(data, years);
          
          if(quicklink == "deathCntSlider"){
          	data = createDeathCntMap(data, document.getElementById("range2").value);
          }


          var leftMargin = 122;
          var topMargin = 30;
          var margin = {
            top: 20,
            right: 25,
            bottom: 20,
            left: 122
          };
          var width = 1500 - margin.left - margin.right;
          var height = 900 - margin.top - margin.bottom;

          var statesDomain = d3.map(data, function(d) {
            return d.STATE;
          }).keys();
          var deathsDomain = d3.map(data, function(d) {
            return d.DEATHS;
          }).keys();
          var stateDeathValueArray = buildStateDeathMappingArray(data, statesDomain);

          if (quicklink == "bubblesort") {
            stateBubbleSort(stateDeathValueArray, statesDomain);
          } 
          
          var xExtent = d3.extent(data, d => d.STATE);
          xScale = d3.scaleBand().domain(statesDomain).range([leftMargin, width]).padding(0.4);

          var yMax = d3.max(stateDeathValueArray);
          yScale = d3.scaleLinear().domain([0, yMax]).range([height, 0]);
          xAxis = d3.axisBottom().scale(xScale);

          var graphSVG = d3.select("#stateBarChart")
            .append("svg")
            .attr("width", "1500")
            .attr("height", "750");

          graphSVG.append("g")
            .attr("class", "axis")
            .attr("transform", "translate(0,620)")
            .call(xAxis)
            .selectAll("text")
            .style("text-anchor", "end")
            .attr("dx", "-.8em")
            .attr("dy", ".15em")
            .attr("transform", "rotate(-65)")
            .append("text")
            .attr("x", (900 + 70) / 2)
            .attr("y", "10")
            .text("States");


          yAxis = d3.axisLeft()
            .scale(yScale)


          graphSVG.append("g")
            .attr("class", "axis")
            .attr("transform", `translate(${leftMargin},-240)`)
            .call(yAxis)
            .append("text")
            .attr("transform", "rotate(-90)")
            .attr("x", "-300")
            .attr("y", "-70")
            .attr("text-anchor", "end")
            .text("Total Number of Deaths");

          graphSVG.selectAll("rect")
            .append("g")
            .data(data)
            .enter()
            .append("rect").transition().ease(d3.easeLinear).duration(2000)
            .attr("x", d => xScale(d.STATE))
            .attr("y", d => yScale(stateDeathValueArray[lookupStateIndex(statesDomain, d.STATE)]) - 240)
            .attr("width", xScale.bandwidth())
            .attr("height", function(d) {
              return height - yScale(stateDeathValueArray[lookupStateIndex(statesDomain, d.STATE)]);
            })
            .attr("fill", function(d) {

              var deaths = stateDeathValueArray[lookupStateIndex(statesDomain, d.STATE)];
              if (deaths > (yMax * .80)) {
                return "red";
              } else if (deaths < (yMax * .80) && deaths > (yMax * .25)) {
                return "rgb(0,191,255)";
              }
              return "blue";
            });
            
            if(quicklink != "deathCntSlider"){
							flagStatesWithHighGunViolence();
              flagWithLowestGunViolence();
            }
        })

      }


      function clearAndRender(years, quicklink) {

        if (years == 0) {
          years = 1;
        }

        var dateRangeText = "";

        if (years == 5) {
          dateRangeText = " Gun Violence Data for 2014-2019 Time Period";
        } else if (years == 4) {
          dateRangeText = "Gun Violence Data for 2014-2018 Time Period";
        } else if (years == 3) {
          dateRangeText = "Gun Violence Data for 2014-2017 Time Period";
        } else if (years == 2) {
          dateRangeText = "Gun Violence Data for 2014-2016 Time Period";
        } else {
          dateRangeText = "Gun Violence Data for 2014-2015 Time Period";
        }

        document.getElementById("sliderDateRange").innerHTML = dateRangeText;
        d3.select("#stateBarChart").selectAll("*").remove();
        renderChart(years, quicklink);
      }
      
      function clearAndRenderByDeathCnt(cntThreshold, quicklink) {

        if (cntThreshold == 0) {
          cntThreshold = 100;
        }
				clearFlags();
        d3.select("#stateBarChart").selectAll("*").remove();
        renderChart(document.getElementById('range1').value, "deathCntSlider");
      }

      function stateRecordCount(data, state) {

        var recordCount = 0;
        for (var i = 0; i < data.length; i++) {

          var stateName = data[i].STATE;

          if (stateName == state) {
            recordCount++;
          }
        }
        return recordCount;
      }

      function getCDCURL(data, state) {

        var recordCount = 0;
        for (var i = 0; i < data.length; i++) {

          var stateName = data[i].STATE;

          if (stateName == state) {
            return data[i].URL;
          }
        }
        return "-1";
      }

      function refine(data, state) {

        var array = new Array(stateRecordCount(data, state));
        var j = 0;

        for (var i = 0; i < data.length; i++) {

          var stateName = data[i].STATE;

          if (stateName == state) {
            array[j] = data[i];
            j++;
          }
        }

        return array;
      }

    </script>
  </span>
</body>
