<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  const viewer = new Cesium.Viewer("cesiumContainer", {});

  const position = Cesium.Cartesian3.fromDegrees(110, 20, 20000);

  // 相机跳转目的地
  viewer.camera.setView({
    destination: position,
    orientation: {
      heading: Cesium.Math.toRadians(0),
      pitch: Cesium.Math.toRadians(0),
      roll: Cesium.Math.toRadians(0),
    },
  });
});
</script>

<style scoped></style>
