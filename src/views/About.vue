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
      zoom: 4, // starting zoom
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
