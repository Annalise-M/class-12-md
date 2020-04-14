### class 12 reading notes on the following articles:

* https://www.webdesignerdepot.com/2013/11/easily-create-stunning-animated-charts-with-chart-js/

* https://www.chartjs.org/docs/latest/
___
        Stunning Animated Charts with Chart.js

    "Charts are far better for displaying data visually than tables and have the added benefit that no one is ever going to press-gang them into use as a layout tool. They’re easier to look at and convey data quickly, but they’re not always easy to create."
---
        chart.js is a javaScript plug in that uses HTML5's canvas element. ie.
        - bar charts
        - line charts
        - pie charts, etc.
---
    Set up:
    1st. download Chart.js
    2nd. copy Chart.min.js out of the unzipped folder and into the directory (you'll be working in).
    3rd. Create a new html pg. and import the script
---
    ex.

<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <title>Chart.js demo</title>
        <script src='Chart.min.js'></script>
    </head>
    <body>
    </body>
</html>

____
### For line charts:

    1. create element in your html.
        ex. 

<canvas id="buyers" width="600" height="400"></canvas>

    2. now write  a script that will retrieve the context of the canvas (so add to the food of the body in html.)
        ex.

<script>
    var buyers = document.getElementById('buyers').getContext('2d');
    new Chart(buyers).Line(buyerData);
</script>

    3. inside the same script tags we need to create our data. (The example holds that it's an object that contains labels for the base of the chart and datasets to describe the values on the chart. This is ADDED immediately above the line that begins 'var buyers=')
        ex.

var buyerData = {
	labels : ["January","February","March","April","May","June"],
	datasets : [
		{
			fillColor : "rgba(172,194,132,0.4)",
			strokeColor : "#ACC26D",
			pointColor : "#fff",
			pointStrokeColor : "#9DB86D",
			data : [203,156,99,251,305,247]
		}
	]
}
---
### For drawing a pie chart:

    1. bring in the canvas element

<canvas id="countries" width="600" height="400"></canvas>

    2. next get the context and instantiate the chart

var countries= document.getElementById("countries").getContext("2d");
new Chart(countries).Pie(pieData, pieOptions);

    (adding more options to the chart)

    3. crate the data (make sure to supply a value and a color for each section)

var pieData = [
	{
		value: 20,
		color:"#878BB6"
	},
	{
		value : 40,
		color : "#4ACAB4"
	},
	{
		value : 10,
		color : "#FF8153"
	},
	{
		value : 30,
		color : "#FFEA88"
	}
];

    4. and then immediately after the pieData we add our options:

var pieOptions = {
	segmentShowStroke : false,
	animateScale : true
}
    (note: These options do two things, first they remove the stroke from the segments, and then they animate the scale of the pie so that it zooms out from nothing.)
---
### For drawing a bar chart:
    1. add the canvas element

<canvas id="income" width="600" height="400"></canvas>

    2. next, retrieve the element and create the graph

var income = document.getElementById("income").getContext("2d");
new Chart(income).Bar(barData);

    3. lastly, we add the bar chart's data

var barData = {
	labels : ["January","February","March","April","May","June"],
	datasets : [
		{
			fillColor : "#48A497",
			strokeColor : "#48A4D1",
			data : [456,479,324,569,702,600]
		},
		{
			fillColor : "rgba(73,188,170,0.4)",
			strokeColor : "rgba(72,174,209,0.4)",
			data : [364,504,605,400,345,320]
		}

	]
}
    (note: the data is largely the same, except this time we’ve chosen to use RGBA to specify our colors which allows us to add transparency.)
---
### full script demo below:

<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <title>Chart.js demo</title>
        <!-- import plugin script -->
        <script src='Chart.min.js'></script>
    </head>
    <body>
        <!-- line chart canvas element -->
        <canvas id="buyers" width="600" height="400"></canvas>
        <!-- pie chart canvas element -->
        <canvas id="countries" width="600" height="400"></canvas>
        <!-- bar chart canvas element -->
        <canvas id="income" width="600" height="400"></canvas>
        <script>
            // line chart data
            var buyerData = {
                labels : ["January","February","March","April","May","June"],
                datasets : [
                {
                    fillColor : "rgba(172,194,132,0.4)",
                    strokeColor : "#ACC26D",
                    pointColor : "#fff",
                    pointStrokeColor : "#9DB86D",
                    data : [203,156,99,251,305,247]
                }
            ]
            }
            // get line chart canvas
            var buyers = document.getElementById('buyers').getContext('2d');
            // draw line chart
            new Chart(buyers).Line(buyerData);
            // pie chart data
            var pieData = [
                {
                    value: 20,
                    color:"#878BB6"
                },
                {
                    value : 40,
                    color : "#4ACAB4"
                },
                {
                    value : 10,
                    color : "#FF8153"
                },
                {
                    value : 30,
                    color : "#FFEA88"
                }
            ];
            // pie chart options
            var pieOptions = {
                 segmentShowStroke : false,
                 animateScale : true
            }
            // get pie chart canvas
            var countries= document.getElementById("countries").getContext("2d");
            // draw pie chart
            new Chart(countries).Pie(pieData, pieOptions);
            // bar chart data
            var barData = {
                labels : ["January","February","March","April","May","June"],
                datasets : [
                    {
                        fillColor : "#48A497",
                        strokeColor : "#48A4D1",
                        data : [456,479,324,569,702,600]
                    },
                    {
                        fillColor : "rgba(73,188,170,0.4)",
                        strokeColor : "rgba(72,174,209,0.4)",
                        data : [364,504,605,400,345,320]
                    }
                ]
            }
            // get bar chart canvas
            var income = document.getElementById("income").getContext("2d");
            // draw bar chart
            new Chart(income).Bar(barData);
        </script>
    </body>
</html>