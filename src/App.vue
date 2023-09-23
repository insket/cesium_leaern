<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted, version } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  const viewer = new Cesium.Viewer("cesiumContainer", {});

  // 线
  const polyline = viewer.entities.add({
    polyline: {
      //  返回笛卡尔坐标数组
      positions: Cesium.Cartesian3.fromDegreesArray([120, 20, 121, 20, 121, 21]),
      width: 10,
      material: Cesium.Color.RED,
    },
  });

  // 多边形
  const polygon = viewer.entities.add({
    polygon: {
      hierarchy: {
        positions: Cesium.Cartesian3.fromDegreesArray([120, 25, 121, 25, 121, 25.5, 120, 25.5]),
      },
      material: Cesium.Color.RED,
      height: 0,
      extrudedHeight: 50000,
      outline: true,
      outlineColor: Cesium.Color.BLUE,
      fill:false
    },
  });

  viewer.zoomTo(polygon);
});
</script>

<style scoped></style>
