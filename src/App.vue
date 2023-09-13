<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken =import.meta.env.VITE_APP_ION_KEY

  const widget = new Cesium.CesiumWidget("cesiumContainer");
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
