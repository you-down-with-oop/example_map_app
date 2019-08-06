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
      message: "Welcome to Vue.js!",
      places: [
        {
          lat: 37.974728,
          long: -122.03711,
          description: "Alpine Bakery in Concord, delicious pastries!"
        },
        {
          lat: 36.973804,
          long: -122.02575,
          description: "Marinis is my favorite ice cream in Santa Cruz"
        },
        {
          lat: 37.791852,
          long: -122.42127,
          description: "Bob's Donuts in SF makes gigantic donuts, good for sharing (or eating alone!)"
        }
      ]
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

    // var popup = new mapboxgl.Popup({ offset: 25 }).setText("Construction on the Washington Monument began in 1848.");

    // var marker = new mapboxgl.Marker()
    //   .setLngLat([30.5, 50.5])
    //   .setPopup(popup)
    //   .addTo(map);

    this.places.forEach(function(place) {
      var popup = new mapboxgl.Popup({ offset: 25 }).setText(place.description);
      var marker = new mapboxgl.Marker()
        .setLngLat([place.long, place.lat])
        .setPopup(popup)
        .addTo(map);
    });

    // for (var i = 0; i < this.places.length; i++) {
    //   var place = this.places[i];
    //   var popup = new mapboxgl.Popup({ offset: 25 }).setText(place.description);
    //   var marker = new mapboxgl.Marker()
    //     .setLngLat([place.long, place.lat])
    //     .setPopup(popup)
    //     .addTo(map);
    // }
  },
  methods: {}
};
</script>
