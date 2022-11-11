<template>
  <div id="map-container"></div>
</template>

<script setup>
import { onMounted } from "vue";

let map = null;

function initMap(mapElement = "map-container") {
  const mapOptions = {
    // viewMode: '3D', //使用3D视图
    zoom: 12,
    zooms: [2, 22],
  };
  AMapLoader.load({
    key: "490579eee171cd7c97c9aff423e3fda5",
    version: "2.0", // 默认为 1.4.15
    plugins: [
      "AMap.ToolBar",
      "AMap.Scale",
      "AMap.MarkerCluster",
      "AMap.MoveAnimation",
    ],
  }).then((AMap) => {
    map = new AMap.Map(mapElement, mapOptions);
    map.on("complete", function () {
      // 地图图块加载完成后触发
      console.log("地图图块加载完成");
    });
  });
}

onMounted(() => {
  initMap();
});
</script>
<style scoped>
#map-container {
  height: 100vh;
  width: 100vh;
}
</style>
