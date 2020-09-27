# airbnb_ashvll<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Buncombe County Airbnbs (2020)</title>
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.0/dist/leaflet.css"/>
    <style>
html, body, #map { width: 100%; height: 100%; margin: 0; background: #fff; }
    </style>
    <script src="https://unpkg.com/leaflet@1.7.0/dist/leaflet.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet-ajax/2.1.0/leaflet.ajax.min.js"></script>
</head>
<body>
<!-- Our web map and content will go here -->
<div id="map"></div>
<script>
  // 1. Create a map object.
  var mymap = L.map('map', {
      center: [35.5946,-82.5540], //note that we've centered the map to downtown AVL
      zoom: 11, //this line adjusts the starting zoom level of the map
      maxZoom: 18,//this line sets the maximum zoom level
      minZoom: 11,//this line sets the minimum zoom level
      detectRetina: true // detect whether the sceen is high resolution or not.
  });

  // 2. Add a base map.
  L.tileLayer('http://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}.png').addTo(mymap);
  // 3. Add Airbnb GeoJSON Data
// Null variable that will hold Airbnb data
var airbnb_listings = null;
// add several extra spaces here.
//steps 4, 5, etc. will be inserted in this line location.
// Get GeoJSON and put it on the map when it loads
// Make sure you have the correct directory path below
// You can see we're also adding attribution information for our data sources
// We will also add lines of code around this airbnb_listings object as we adjust the style of the symbols
//Make sure and change your authorname in the attribute information
airbnb_listings = L.geoJson.ajax("assets/airbnb_listings.geojson",{
    attribution: 'Airbnb Listings &copy; Inside Airbnb | Asheville Zoning Districts &copy; City of Asheville Open Data | Base Map &copy; CartoDB | Map Author: '
});
// Add the Airbnbs to the map.
airbnb_listings.addTo(mymap);
</script>
</body>
</html>
