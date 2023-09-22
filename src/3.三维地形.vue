<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  const esri = new Cesium.ArcGisMapServerImageryProvider({
    url: "https://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/Mapserver",
    enablepickFeatures: false,
  });

  const viewer = new Cesium.Viewer("cesiumContainer", {
    baseLayerPicker: false,
    imageryProviderViewModels: [esri], // 自定义图层  要把 baseLayerPicker 设为false
    terrain: Cesium.Terrain.fromWorldTerrain(), // 三维地形
  });
});
</script>

<style scoped></style>
