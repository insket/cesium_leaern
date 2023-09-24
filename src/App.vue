<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted, version } from "vue";

let viewer;
let lon,
  lat,
  num = 0;

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  viewer = new Cesium.Viewer("cesiumContainer", {});

  // 动态line
  const line = viewer.entities.add({
    polyline: {
      positions: new Cesium.CallbackProperty(() => {
        num += 0.005;
        lon = 120 + num;
        lat = 30 + num;
        if (lon < 121) {
          return Cesium.Cartesian3.fromDegreesArray([120, 30, lon, lat]);
        } else {
          line.polyline.positions = Cesium.Cartesian3.fromDegreesArray([120, 30, 121, 31]);
        }
      }, false),
      width: 5,
      material: Cesium.Color.RED,
    },
  });

  viewer.zoomTo(line);
});
</script>

<style scoped>
.remove {
  position: absolute;
  top: 50px;
  left: 50px;
  z-index: 99;
}
</style>
