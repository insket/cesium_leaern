<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY

  new Cesium.Viewer("cesiumContainer");
});
</script>

<style scoped></style>

<style>

</style>
