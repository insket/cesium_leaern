<template>
  <div id="cesiumContainer"></div>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted } from "vue";

onMounted(() => {
  const viewer = new Cesium.Viewer("cesiumContainer", {
    geocoder: false, // search 按钮
    homeButton: false, // home 按钮
    sceneModePicker:false, // 视图按钮
    baseLayerPicker:false,  // 地图模式
    navigationHelpButton:false,  // ？ 按钮
    animation:false, // 左下角动画 按钮
    // creditContainer:"credit",
    timeline:false, // time 时间线
    fullscreenButton:false, //全屏
  });
  viewer.scene.debugShowFramesPerSecond = true; // 显示帧数 fps
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
