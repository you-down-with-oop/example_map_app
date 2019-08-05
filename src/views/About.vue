<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div id="map"></div>
  </div>
</template>

<style>
#map {
  height: 400px;
}
</style>

<script>
/* global mapboxgl */
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!"
    };
  },
  mounted: function() {
    mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_ACCESS_TOKEN;
    var map = new mapboxgl.Map({
      container: "map", // container id
      style: "mapbox://styles/mapbox/streets-v11", // stylesheet location
      center: [-74.5, 40], // starting position [lng, lat]
      zoom: 9 // starting zoom
    });
  },
  methods: {}
};
</script>
