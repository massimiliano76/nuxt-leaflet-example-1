<template>
  <section class="container">
    <leaflet-map id="leafletmap"></leaflet-map>
  </section>
</template>

<script>
import LeafletMap from "~/components/LeafletMap.vue";

export default {
  components: {
    LeafletMap
  }
};
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
#leafletmap {
  min-height: 100vh;
  min-width: 100vh;
}
</style>
