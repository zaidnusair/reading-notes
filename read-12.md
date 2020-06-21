#### drawing animated charts using JS
* **Chart.js**: a JavaScript plugin that uses HTML5’s canvas element to draw the graph onto the page.
* drawing a line chard:
1. create a canvas element in our HTML in which Chart.js can draw our chart. 
```
<canvas id="buyers" width="600" height="400"></canvas>
```
2. write a script that will retrieve the context of the canvas
```
<script>
    var buyers = document.getElementById('buyers').getContext('2d');
    new Chart(buyers).Line(buyerData);
</script>
```
3. create the data inside the script
```
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
  ```
  4. test browser to see line chart.
  * Drawing a pie chart:
  1.  create a canvas element in our HTML in which Chart.js can draw our chart.
  ```
  <canvas id="countries" width="600" height="400"></canvas>
  ```
  2. get the context and to instantiate the chart
  ```
  var countries= document.getElementById("countries").getContext("2d");
new Chart(countries).Pie(pieData, pieOptions);
  ```
  3.  create the data. This data is a little different to the line chart because the pie chart is simpler, we just need to supply a value and a color for each section
  ```
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
  ```
  4. after the pieData we’ll add our options. These options do two things, first they remove the stroke from the segments, and then they animate the scale of the pie so that it zooms out from nothing.
  ```
  var pieOptions = {
	segmentShowStroke : false,
	animateScale : true
}
  ```
  * Drawing a bar chart
  1. add the canvas element
  ```
  <canvas id="income" width="600" height="400"></canvas>
  ```
  2. retrieve the element and create the graph
  ```
  var income = document.getElementById("income").getContext("2d");
new Chart(income).Bar(barData);
  ```
  3. we add in the bar chart’s data
  ```
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
  ```
  
  
  
  
  
  
  
  
  
  
  
  
  
  
