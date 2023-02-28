<template>
  <div id="viewport" class="flex flex-col p-4">
    <div id="threejs-container" class="py-5"></div>
  </div>
</template>

<script setup>
import { onMounted, onUpdated, ref } from "vue";
import * as THREE from "three";
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls";

const props = defineProps(["size"]);

let renderer, camera, scene, controls, geometry;
let boxMaterial = ref(new THREE.MeshNormalMaterial());
let toggleValue = ref(false);

let width = 600;
let heigh = 700;

function init() {
  renderer = new THREE.WebGLRenderer();
  renderer.setSize(width, heigh);
  renderer.setPixelRatio(window.devicePixelRatio);
  document.getElementById("threejs-container").appendChild(renderer.domElement);

  camera = new THREE.PerspectiveCamera(75, width / heigh, 0.1, 1000);
  camera.position.set(0, 0, 40);

  scene = new THREE.Scene();
  scene.background = new THREE.Color("#f5f6fa");

  controls = new OrbitControls(camera, renderer.domElement);

  createBox(25, 25, 25);
  animate();
}

function animate() {
  requestAnimationFrame(animate);
  controls.update();
  renderer.render(scene, camera);
}

function createBox(l, w, h) {
  geometry = new THREE.BoxGeometry(l, w, h);
  const sphere = new THREE.Mesh(geometry, boxMaterial.value);
  scene.add(sphere);
}

function onSliderChange() {
  scene.remove(scene.children[0]);
  if (toggleValue.value) {
    boxMaterial.value = new THREE.MeshBasicMaterial({ color: 0xff0000 });
  } else {
    boxMaterial.value = new THREE.MeshNormalMaterial();
  }
  createBox(props.size, props.size, props.size);
}

onMounted(() => {
  init();
  animate();
});

onUpdated(() => {
  onSliderChange();
});
</script>

<style scoped>
#viewport {
  border-style: dashed;
  border-color: #d2dfe8;
  border-width: 4px;
  border-radius: 10px;
  margin: 12px;
  height: calc(100vh - 105px);
  width: 600px;
  min-width: 200px;
  position: inherit;
}
</style>
