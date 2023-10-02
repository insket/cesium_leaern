<template>
  <div id="cesiumContainer"></div>
  <button class="remove" @click="remove">remove</button>
</template>

<script setup>
import * as Cesium from "cesium";
import * as turf from "@turf/turf";
import { onMounted, version } from "vue";

let viewer;

onMounted(() => {
  Cesium.Ion.defaultAccessToken = import.meta.env.VITE_APP_ION_KEY;

  viewer = new Cesium.Viewer("cesiumContainer", {
    shouldAnimate: true,
  });

  const linestring1 = turf.lineString(
    [
      [-24, 63],
      [-23, 60],
      [-25, 65],
      [-20, 69],
    ],
    { name: "line 1" }
  );
  Cesium.GeoJsonDataSource.load(linestring1).then((res) => {
    const entity = res.entities.values[0];
    viewer.entities.add(entity);
    // viewer.zoomTo(entity)
  });

  const multiLine = turf.multiLineString([
    [
      [0, 0],
      [4, 4],
    ],
    [
      [6, 6],
      [10, 10],
    ],
  ]);
  Cesium.GeoJsonDataSource.load(multiLine).then((res) => {
    viewer.dataSources.add(res);
  });

  const polygon = turf.polygon(
    [
      [
        [-5, 52],
        [-4, 56],
        [-2, 51],
        [-7, 54],
        [-5, 52],
      ],
    ],
    { name: "poly1" }
  );
  Cesium.GeoJsonDataSource.load(polygon).then((res) => {
    viewer.dataSources.add(res);
    // viewer.zoomTo(res);
  });

  const topoJson = Cesium.GeoJsonDataSource.load("/src/assets/ne_10m_us_states.topojson").then(
    (res) => {
      // viewer.dataSources.add(res);
      // viewer.zoomTo(res);
    }
  );

  const kmz = Cesium.KmlDataSource.load("/src/assets/gdpPerCapita2008.kmz").then((res) => {
    // viewer.dataSources.add(res);
    // viewer.zoomTo(res);
  });

  const czml = Cesium.CzmlDataSource.load("/src/assets/Vehicle.czml").then((res) => {
    // viewer.dataSources.add(res);
    // let entity = res.entities.getById("Vehicle");
    // viewer.trackedEntity = entity;
  });
});

const remove = () => {
  viewer.entities.removeAll();
  viewer.dataSources.removeAll();
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
