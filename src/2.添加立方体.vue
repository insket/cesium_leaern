<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted } from "vue";

onMounted(() => {
  const viewer = new Cesium.Viewer("cesiumContainer");
  var redBox = viewer.entities.add({
    name: "Red box with black outline",
    position: Cesium.Cartesian3.fromDegrees(-107.0, 40.0, 300000.0),
    box: {
      dimensions: new Cesium.Cartesian3(200000.0, 300000.0, 500000.0), // x  y  z
      material: Cesium.Color.RED.withAlpha(0.2),
      outline: true,
      outlineColor: Cesium.Color.BLACK,
    },
  });

  viewer.zoomTo(viewer.entities);
});
</script>

<style scoped></style>

<style>
html,
body,
#app #cesiumContainer {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
</style>
