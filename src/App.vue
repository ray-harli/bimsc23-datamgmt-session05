<!-- // Script is in some way equivalent to script.js. This is place
to define variables, methods and imports of other Vue compoennts. -->
<script setup>
// Imports from packages
import ButtonCount from './components/ButtonCount.vue'
import { ref } from "vue";

var button1 = "Height"
var button2 = "Width"
var button3 = "Length"

var totalCount= ref(0)

function bringCount(countFromChild){

  totalCount.value += countFromChild
  console.log(totalCount.value)

}


</script>

<!-- Template is a HTML-based syntax that allows you to bind the rendered DOM elements
with data, objects, functions etc. -->
<template>

  <div id="top-bar">
    <div id="title-container">
      <img class="logo-image" alt="Iaac logo" src="./assets/iaac-white.png" />
      <h2>Digital Tools for Cloud-based Data Management</h2>
    </div>
  </div>

  <div>

    <ButtonCount v-bind:title = "button1"  v-on:updateCount="bringCount"/>

    <ButtonCount v-bind:title = "button2"  v-on:updateCount="bringCount"/>
    
    <ButtonCount v-bind:title = "button3"  v-on:updateCount="bringCount"/>


  </div>

  <div>
    <p> Total Count of sliders is {{ totalCount }}</p>
  </div>

</template>

<!-- Style is for CSS styling -->
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
</style>
