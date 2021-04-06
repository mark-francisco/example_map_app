<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div id="map"></div>
    <!-- <button v-on:click="setUpMap()">Show Map</button> -->
  </div>
</template>

<script>
// you can use the require syntax, the import syntax, or the global comment syntax
var mapboxgl = require("mapbox-gl/dist/mapbox-gl.js");
// if you use the import syntax, the file path assumes "node_modules" as the root folder
// import mapboxgl from "mapbox-gl/dist/mapbox-gl.js";

export default {
  name: "Home",
  mounted() {
    this.setUpMap();
  },
  methods: {
    setUpMap: function () {
      mapboxgl.accessToken = process.env.VUE_APP_MAPBOX_API_KEY;
      var map = new mapboxgl.Map({
        container: "map",
        style: "mapbox://styles/mapbox/streets-v11",
        center: [-9, 31], // starting position [lng, lat]
        zoom: 4, // starting zoom
      });
      // Create a default Marker and add it to the map.
      new mapboxgl.Marker().setLngLat([-9, 31]).addTo(map);

      // // Create a new Pop-up
      // var popup = new mapboxgl.Popup({ offset: 25 }).setText("hi!");

      // var el = document.createElement("div");
      // el.id = "marker";

      // // create the marker
      // new mapboxgl.Marker(el)
      //   .setLngLat([-9, 31])
      //   .setPopup(popup) // sets a popup on this marker
      //   .addTo(map);
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
#map {
  height: 500px;
  width: auto;
}
</style>
