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
      fill: false,
    },
  });

  // 盒子
  const box = viewer.entities.add({
    position: Cesium.Cartesian3.fromDegrees(119, 30, 2000),
    box: {
      dimensions: new Cesium.Cartesian3(2000, 1000, 3000),
      material: Cesium.Color.PINK,
    },
  });

  // 椭圆
  const ellipse = viewer.entities.add({
    position: Cesium.Cartesian3.fromDegrees(118, 30, 2000),
    ellipse: {
      semiMajorAxis: 200,
      semiMinorAxis: 100,
      material: Cesium.Color.VIOLET,
      rotation: Math.PI / 4,
    },
  });

  // 矩形
  const rectangle = viewer.entities.add({
    rectangle: {
      coordinates: Cesium.Rectangle.fromDegrees(120,40,123,45),
      extrudedHeight:200000,
      material: "/src/assets/0760.png_300.png"
    },
  });

  viewer.zoomTo(rectangle);
});
</script>

<style scoped></style>
