<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted, version } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  const viewer = new Cesium.Viewer("cesiumContainer", {});

  // entity
  // const point = new Cesium.Entity({
  //   position: Cesium.Cartesian3.fromDegrees(120, 30,2000),
  //   point: {
  //     pixelSize: 20, // 像素点大小
  //     color: Cesium.Color.BLUE
  //   },
  // });
  // viewer.entities.add(point)


  const point = viewer.entities.add({
    id: "point",
    position: Cesium.Cartesian3.fromDegrees(120,30, 2000),
    point: {
      pixelSize: 20,
      color: Cesium.Color.BLUE,
    },
  });

  viewer.zoomTo(point)

});

</script>

<style scoped></style>
