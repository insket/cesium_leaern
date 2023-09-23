<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted, version } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  const viewer = new Cesium.Viewer("cesiumContainer", {});

  const point = viewer.entities.add({
    id: "point",
    position: Cesium.Cartesian3.fromDegrees(120, 30, 2000),
    point: {
      pixelSize: 20,
      color: Cesium.Color.BLUE,
    },
  });

  // 标记
  const billboard = viewer.entities.add({
    position: Cesium.Cartesian3.fromDegrees(116, 40, 10),
    // billboard: {
    //   image: "/src/assets/0760.png_300.png",
    //   scale: 0.2,
    //   color: Cesium.Color.RED,
    // },
    label: {
      text: "label",
      showBackground:true,
      backgroundColor: new Cesium.Color(255, 255, 0),
    },
  });

  viewer.zoomTo(billboard);
});
</script>

<style scoped></style>
