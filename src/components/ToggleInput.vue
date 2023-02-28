<template>
    <form class="definition-input">
      <label class="input-title" for="toggle">{{ title }}</label>
  
      <div class="checkbox-wrapper-22">
        <label class="switch" for="checkbox">
          <input type="checkbox" id="checkbox" v-model="toggleValue" v-on:change="sendToggleUpdate" />
          <div class="slider round" :class="{ red: toggleValue }"></div>
        </label>
      </div>
    </form>
  </template>
  
  <script setup>
  import { ref, defineProps, defineEmits } from "vue";
  
  const props = defineProps(["title"]);
  const emits = defineEmits(["updateValue"]);
  const toggleValue = ref(false);
  
  function sendToggleUpdate() {
    emits("updateValue", toggleValue.value);
  }
  </script>
  
  <style scoped>
  .checkbox-wrapper-22 {
    display: inline-block;
    vertical-align: middle;
  }
  
  .switch {
    position: relative;
    display: inline-block;
    width: 52px;
    height: 24px;
    margin: 0;
    padding: 0;
    margin-left: 10px;
  }
  
  .switch input {
    opacity: 0;
    width: 0;
    height: 0;
  }
  
  .slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 34px;
  }
  
  .slider:before {
    position: absolute;
    content: "";
    height: 20px;
    width: 20px;
    left: 2px;
    bottom: 2px;
    background-color: white;
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 50%;
  }
  
  input:checked + .slider {
    background-color: #2196f3;
  }
  
  input:focus + .slider {
    box-shadow: 0 0 1px #2196f3;
  }
  
  input:checked + .slider:before {
    -webkit-transform: translateX(26px);
    -ms-transform: translateX(26px);
    transform: translateX(26px);
    background-color: red;
  }
  
  .slider.round {
    border-radius: 34px;
  }
  
  .slider.round:before {
    border-radius: 50%;
  }
  
  .red {
    background-color: red !important;
  }
  </style>
  