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

  viewer = new Cesium.Viewer("cesiumContainer");

  const rectangleInstance = new Cesium.GeometryInstance({
    geometry: new Cesium.RectangleGeometry({
      rectangle: Cesium.Rectangle.fromDegrees(-140.0, 30.0, -100.0, 40.0),
      vertexFormat: Cesium.PerInstanceColorAppearance.VERTEX_FORMAT,
    }),
    id: "rectangle",
    attributes: {
      color: new Cesium.ColorGeometryInstanceAttribute(0.0, 1.0, 1.0, 0.5),
    },
  });

  const cyanPolygon = new Cesium.GeometryInstance({
    geometry: new Cesium.PolygonGeometry({
      polygonHierarchy: new Cesium.PolygonHierarchy(
        Cesium.Cartesian3.fromDegreesArray([-100.0, 43.0, -90, 35, -100.0, 27.0])
      ),
    }),
    attributes: {
      color: new Cesium.ColorGeometryInstanceAttribute(0.0, 1.0, 1.0, 0.5),
    },
  });

  viewer.scene.primitives.add(
    new Cesium.Primitive({
      geometryInstances: [rectangleInstance, cyanPolygon],
      appearance: new Cesium.PerInstanceColorAppearance(),
    })
  );
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
