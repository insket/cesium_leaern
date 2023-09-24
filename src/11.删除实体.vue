<template>
  <div id="cesiumContainer"></div>
  <button class="remove" @click="remove">remove</button>
</template>

<script setup>
import * as Cesium from "cesium";
import { onMounted, version } from "vue";

let viewer;
let point;
let point2;

let pointArr = [];

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  viewer = new Cesium.Viewer("cesiumContainer", {});

  point = viewer.entities.add({
    id: "point",
    position: Cesium.Cartesian3.fromDegrees(121, 30),
    point: {
      color: Cesium.Color.RED,
      pixelSize: 20,
    },
  });
  pointArr.push(point);
  point2 = viewer.entities.add({
    id: "point2",
    position: Cesium.Cartesian3.fromDegrees(121.0001, 30),
    point: {
      color: Cesium.Color.BLUE,
      pixelSize: 20,
    },
  });
  pointArr.push(point2);

  viewer.zoomTo(point);
});

const remove = () => {
  // viewer.entities.remove(point);

  // 删除所有
  // viewer.entities.removeAll()

  // 根据id删
  // viewer.entities.removeById("point")

  // 拿到id再删
  // const point = viewer.entities.getById("point")
  // viewer.entities.remove(point)

  pointArr.forEach((item) => viewer.entities.remove(item));
  pointArr = [];
};
</script>

<style scoped>
.remove {
  position: absolute;
  top: 50px;
  left: 50px;
  z-index: 99;
}
</style>
