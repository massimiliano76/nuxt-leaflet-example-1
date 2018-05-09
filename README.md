# Nuxt Leaflet Example

Example of how you can combine Nuxt.JS with Vue2-Leaflet.

Run the project with

```bash
yarn dev
```

The steps below outlines what was done to make things work.

## Required packages

Install leaflet and Vue2Leaflet:

```bash
yarn add leaflet vue2-leaflet
```

## Nuxt Plugin

Create a plugin which makes the Vue2Leaflet components available:

```js
// ~/plugins/leaflet.js
import Vue from "vue";
import Vue2Leaflet from "vue2-leaflet";

Vue.component("l-circle", Vue2Leaflet.LCircle);
Vue.component("l-circle-marker", Vue2Leaflet.LCircleMarker);
Vue.component("l-control-attribution", Vue2Leaflet.LControlAttribution);
Vue.component("l-control-layers", Vue2Leaflet.LControlLayers);
Vue.component("l-control-scale", Vue2Leaflet.LControlScale);
Vue.component("l-control-zoom", Vue2Leaflet.LControlZoom);
Vue.component("l-feature-group", Vue2Leaflet.LFeatureGroup);
Vue.component("l-geo-json", Vue2Leaflet.LGeoJson);
Vue.component("l-icon-default", Vue2Leaflet.LIconDefault);
Vue.component("l-image-overlay", Vue2Leaflet.LImageOverlay);
Vue.component("l-layer-group", Vue2Leaflet.LLayerGroup);
Vue.component("l-map", Vue2Leaflet.LMap);
Vue.component("l-marker", Vue2Leaflet.LMarker);
Vue.component("l-polygon", Vue2Leaflet.LPolygon);
Vue.component("l-polyline", Vue2Leaflet.LPolyline);
Vue.component("l-popup", Vue2Leaflet.LPopup);
Vue.component("l-rectangle", Vue2Leaflet.LRectangle);
Vue.component("l-tile-layer", Vue2Leaflet.LTileLayer);
Vue.component("l-tooltip", Vue2Leaflet.LTooltip);
Vue.component("l-lwms-tile-layer", Vue2Leaflet.LWMSTileLayer);

// Build icon assets.
delete L.Icon.Default.prototype._getIconUrl;
L.Icon.Default.imagePath = "";
L.Icon.Default.mergeOptions({
  iconRetinaUrl:
    "https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.3.1/images/marker-icon-2x.png",
  iconUrl:
    "https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.3.1/images/marker-icon.png",
  shadowUrl:
    "https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.3.1/images/marker-shadow.png"
});
```

Add the plugin to your `nuxt.config.js` file. Set SSR to false:

```js
/*
** Plugins to load before mounting the App
*/
plugins: [
  {
    src: "~/plugins/leaflet",
    ssr: false
  }
],
```

## CSS

Leaflet requires the loading of a css file. You can either do this by including a style tag inside your component/page:

```html
<style src="leaflet/dist/leaflet.css"></style>
<style >
.mini-map {
  width: 100%;
  height: 100vh !important;
}
</style>
```

Or by adding it globally to your `nuxt.config.js`:

```js
/*
** Global CSS
*/
css: ["leaflet/dist/leaflet.css"],
```

## The map component

Finally, create use the leaflet components in your page / component:

```vue
<template>
  <div>
    <b-button variant="danger" @click="logPosition" >Log position</b-button>
    <no-ssr>
      <l-map class="mini-map" :zoom=13 :center="position">
        <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></l-tile-layer>
        <l-marker :lat-lng="position" :draggable="draggable">
          <l-popup :content="popupContent"></l-popup>
        </l-marker>
      </l-map>
    </no-ssr>
  </div>
</template>

<script>
export default {
  data: () => ({
    position: [55.607741796855734, 13.018133640289308],
    draggable: true,
    popupContent: "Sentian HQ"
  }),
  methods: {
    logPosition() {
      console.log(this.position);
    }
  }
};
</script>

<style src="leaflet/dist/leaflet.css">
</style>
<style >
.mini-map {
  width: 100%;
  height: 600px !important;
}
</style>
```
