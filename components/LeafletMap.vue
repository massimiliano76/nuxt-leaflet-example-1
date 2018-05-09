<template>
  <no-ssr>
    <l-map class="mini-map" :zoom=13 :center="[47.413220, -1.219482]">
      <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></l-tile-layer>
      <l-marker :lat-lng="[47.413220, -1.219482]"></l-marker>
    </l-map>
  </no-ssr>
</template>

<script>
// let Vue2Leaflet = {};
// if (process.browser) {
//   Vue2Leaflet = require("vue2-leaflet");
// }
// export default {
//   components: {
//     "v-map": Vue2Leaflet.Map,
//     "v-tilelayer": Vue2Leaflet.TileLayer,
//     "v-marker": Vue2Leaflet.Marker
//   }
// };
</script>

<style src="leaflet/dist/leaflet.css"></style>
<style>
.mni-map {
  width: 100%;
  height: 500px !important;
}
</style>

