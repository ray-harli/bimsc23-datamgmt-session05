<template>
  <div id="top-bar">
    <div id="title-container">
      <img class="logo-image" alt="Iaac logo" src="./assets/iaac-white.png" />
      <h2>Digital Tools for Cloud-based Data Management</h2>
    </div>
  </div>

  <div id="content">
    <div>
      <SliderInput title="Height" v-bind:min="1" v-bind:max="50" v-bind:step="1" v-on:updateValue="updateValue" />
      <ToggleInput title="Run?" v-on:updateValue="updateToggle" />
    </div>

    <div id="geometry-view">
      <GeometryView :size="firstSlider" :toggle="runToggle" />
    </div>
  </div>
</template>

<script setup>
import SliderInput from "./components/SliderInput.vue";
import ToggleInput from "./components/ToggleInput.vue";
import GeometryView from "./components/GeometryView.vue";
import { ref } from "vue";

var firstSlider = ref(25);
var runToggle = ref(false);

function updateValue(newValue, parameterName) {
  if (parameterName === "Height") {
    firstSlider.value = newValue;
  }
}

function updateToggle(newValue) {
  runToggle.value = newValue;
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#top-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: rgba(0, 0, 0, 0.7);
}

#title-container {
  display: flex;
  align-items: center;
  color: white;
  margin-right: 1.5rem;
}

#content {
  display: flex;
  justify-content: space-between;
  margin-top: 2rem;
}

.logo-image {
  height: 3.25rem;
  padding: 0.5rem;
}

h2 {
  font-size: 1.125rem;
  font-weight: 600;
  letter-spacing: -0.05em;
  font-size: 1.125rem;
  font-weight: 600;
  letter-spacing: 0.01em;
}

#geometry-view {
  margin-left: 2rem;
}
</style>
