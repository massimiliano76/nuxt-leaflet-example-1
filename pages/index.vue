<template>
    <section>
    <leaflet-map style="min-height: 100vh; min-width: 100vh"></leaflet-map>
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
