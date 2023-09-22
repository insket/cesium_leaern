<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted, version } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  const viewer = new Cesium.Viewer("cesiumContainer", {});

  const position = Cesium.Cartesian3.fromDegrees(110, 20, 20000);

  // viewer.camera.flyTo({
  //   destination: position,
  //   duration: 2,
  //   orientation: {
  //     heading: Cesium.Math.toRadians(0),
  //     pitch: Cesium.Math.toRadians(0),
  //     roll: Cesium.Math.toRadians(0),
  //   },
  // });

  const position2 = Cesium.Cartesian3.fromDegrees(110, 20);
  viewer.camera.lookAt(
    position2,
    new Cesium.HeadingPitchRange(Cesium.Math.toRadians(0), Cesium.Math.toRadians(-90), 20000)
  );
});
</script>

<style scoped></style>
