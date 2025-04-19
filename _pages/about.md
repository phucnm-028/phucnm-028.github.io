---
permalink: /about/
title: "About"
---

<!-- 1. Link Leaflet CSS -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
     integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
     crossorigin=""/>

<!-- 2. Create a div container for map -->
<div id="map" style="height: 450px; width: 100%; margin-bottom: 20px;"></div>

<!-- 3. Leaflet JavaScript -->
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
     integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
     crossorigin=""></script>

<!-- 4. Make map -->
<script>
  // Initialize the map and set its view
  var map = L.map('map').setView([20, 0], 2); // Centered roughly, zoomed out

  // Add a tile layer (the background map image) from OpenStreetMap
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
  }).addTo(map);

  // Locations 
  var locations = [
    {lat: 21.315603, lng: -157.858093, name: "1. Honolulu, Hawaii - HPU undergrad, it all starts here."},
    {lat: 39.9526, lng: -75.1652, name: "2. Philadelphia - UPenn grad"},
    {lat: 48.1351, lng: 11.5820, name: "3. Munich - Brief PhD research period"},
    {lat: 10.8231, lng: 106.6297, name: "4. Ho Chi Minh - Back home with family, getting ready for next adventure"},
    {lat: 43.6532, lng: -79.3832, name: "5. Toronto - Current home with my wife (and expecting!!)"},
  ];

  // Extract lat and long pairs
  var latlngs = locations.map(function(location) {
    return [location.lat, location.lng];
  });
  // Create the polyline with styling options
  var polyline = L.polyline(latlngs, {
    color: "#4682B4",    
    weight: 2,       
    opacity: 0.5     
  }).addTo(map);

  // Add Markers 
  locations.forEach(function(location) {
    var marker = L.marker([location.lat, location.lng]).addTo(map);
    marker.bindPopup("<b>" + location.name + "</b>"); // Add popup text
  });
  // Adjust map
  map.fitBounds(polyline.getBounds());

</script>


