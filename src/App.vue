<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted } from "vue";

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;


  const viewer = new Cesium.Viewer("cesiumContainer", {
  });

  // 经纬度转笛卡尔 返回笛卡尔坐标
  const cartesian = Cesium.Cartesian3.fromDegrees(110,20,20)
  console.log('%c [ cartesian ]-17', 'font-size:13px; background:#4e1042; color:#925486;', cartesian)

  // 笛卡尔转弧度坐标
  const cartographic = Cesium.Cartographic.fromCartesian(cartesian)
  console.log('%c [ cartographic ]-20', 'font-size:13px; background:#2a8a34; color:#6ece78;', cartographic)

  // 弧度转经纬度
  let lon = Cesium.Math.toDegrees(cartographic.longitude)
  let lat = Cesium.Math.toDegrees(cartographic.latitude)
  console.log('%c [ lon ]-24', 'font-size:13px; background:#507d86; color:#94c1ca;', lon,lat,cartographic.height)
});
</script>

<style scoped></style>
