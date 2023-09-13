<script setup>
import { ref } from 'vue'

const heading = ref('Compute Product')
const compute = ref(true)

let num1 = 5
let num2 = 3

function comp(){
  compute.value = !compute.value
}

</script>

<template>
  <h1>{{heading}}</h1>
  <img src="https://shorturl.at/uxJR3" alt="Electronics!" height="500">
  <button v-if="compute" @click="comp" style="display: block; padding:2%; margin-top: 2%;">Compute!</button>
  <p v-else>The product is: {{num1*num2}}</p>
</template>
