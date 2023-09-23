<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted, version } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  const viewer = new Cesium.Viewer("cesiumContainer", {});

  const billoboard = viewer.entities.add({
    position: Cesium.Cartesian3.fromDegrees(120, 30, 100),
    billboard: {
      image: "/src/assets/touno.png",
      scale: 0.9,
      color: Cesium.Color.WHITE,
      transparent: true,
    },
    polyline: {
      positions: Cesium.Cartesian3.fromDegreesArrayHeights([120, 30, 0, 120, 30, 100]),
      material: Cesium.Color.AQUA,
    },
    position: Cesium.Cartesian3.fromDegrees(120, 30, 100),
    label: {
      text: "xxx小区",
      fillColor: Cesium.Color.AZURE,
      pixelOffset: new Cesium.Cartesian2(0, -60),
    },
  });

  viewer.zoomTo(billoboard);
});
</script>

<style scoped></style>
