<script setup>
import { ref } from "vue";
// Define properties that you will be able to access from parent component. 
// Those properties will be binded from parent to child. 
// Available JavaScript types: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures
defineProps(['title', 'min', 'max', 'step'])

// Define events that will be accessible from parent component
const emits = defineEmits(['updateValue'])

var value = ref(0)

</script>

<template>
<div>
	<form class="definition-input">
			<label class="input-title" for="range-slider">{{ title }}: {{ value }}</label>

			<input type="range" class="modern-range"
			v-bind:min="min" v-bind:max="max" v-bind:step="step"
			v-model="value" @input="emits('updateValue', value)"
			/>
	</form>
</div>


</template>

<style scoped>
.definition-input {
    padding: 20px;
		width: 300px;
}

.input-title {
  font-family: 'Roboto Mono', monospace;
  font-size: 1.2rem;
  text-align: left;
  color: #333;
  margin-bottom: 1rem;
}

.modern-range {
  -webkit-appearance: none;
  width: 100%;
  background: lightgrey;
  height: 15px;
  border-radius: 15px;
  margin: 10px 0px;
}

.modern-range::-webkit-slider-thumb {
  -webkit-appearance: none;
  height: 15px;
  width: 15px;
  border-radius: 15px;
  background-color: black;
  cursor: pointer;
}


</style>