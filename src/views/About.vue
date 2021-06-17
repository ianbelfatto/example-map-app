<template>
  <div class="about">
    <h1>Mapbox Map</h1>
    <div id="map">Map Page Here</div>
  </div>
</template>

<style scoped>
#map {
  width: 100%;
  height: 500px;
}
</style>

<script>
/* global mapboxgl */
export default {
  data: function () {
    return {
      places: [
        { lat: -25.363, lng: 131.044, description: "A place in Australia" },
        { lat: -33.8675, lng: 151.207, description: "The main city!" },
        { lat: 37.4221, lng: -122.078827, description: "Google HQ!" },
      ],
    };
  },
  mounted: function () {
    mapboxgl.accessToken =
      "pk.eyJ1IjoiaWJlbGZhdHRvIiwiYSI6ImNrcTExbnl2MjBhaXYyd2sxMnljeWc5aDgifQ.BAOYySyRiLY8iGwyugHqEw";
    var map = new mapboxgl.Map({
      container: "map", // container id
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [-73.9973608, 41.9270367], // starting position [lng, lat]
      zoom: 1, // starting zoom
    });

    // Map Marker Loop Using 'places' Array

    this.places.forEach((place) => {
      var placeCoords = [place.lng, place.lat];
      var placeDescription = place.description;
      var descriptionPopup = new mapboxgl.Popup({ offset: 25 }).setText(placeDescription).addTo(map);
      new mapboxgl.Marker({ color: "yellow" }).setLngLat(placeCoords).setPopup(descriptionPopup).addTo(map);
    });

    // Map Popups

    var popup = new mapboxgl.Popup({ offset: 25 }).setText("My aunt lives here!").addTo(map);
    console.log(popup);
    var popup2 = new mapboxgl.Popup({ offset: 25 }).setText("I live here!").addTo(map);
    console.log(popup);

    // Map Markers

    new mapboxgl.Marker({ color: "green" }).setLngLat([-73.9973608, 41.9270367]).setPopup(popup2).addTo(map);
    // new mapboxgl.Marker({ color: "blue" }).setLngLat([-117, 32.7]).addTo(map);
    var marker2 = new mapboxgl.Marker({ color: "blue" }).setLngLat([-117, 32.7]).setPopup(popup).addTo(map);
    console.log(marker2);
  },
};
</script>
