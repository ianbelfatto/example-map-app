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
  mounted: function () {
    mapboxgl.accessToken =
      "pk.eyJ1IjoiaWJlbGZhdHRvIiwiYSI6ImNrcTExbnl2MjBhaXYyd2sxMnljeWc5aDgifQ.BAOYySyRiLY8iGwyugHqEw";
    var map = new mapboxgl.Map({
      container: "map", // container id
      style: "mapbox://styles/mapbox/streets-v11", // style URL
      center: [-73.9973608, 41.9270367], // starting position [lng, lat]
      zoom: 11, // starting zoom
    });
    // Map Markers
    new mapboxgl.Marker({ color: "green" }).setLngLat([-73.9973608, 41.9270367]).addTo(map);
    new mapboxgl.Marker({ color: "blue" }).setLngLat([-117, 32.7]).addTo(map);
  },
};
</script>
