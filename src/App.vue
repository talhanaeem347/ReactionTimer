<script setup lang="ts">
import { ref } from 'vue';
import Block from './components/Block.vue';
import Result from './components/Result.vue';

let isPlaing = ref(false);
let showResult = ref(false)
let delay = ref<number>();
let score = ref<number>();
let start = () => {
  delay.value = 500 + Math.random() * 5000;
  isPlaing.value = true;
  showResult.value = false

}
let gameEnd = (rectionTime: number) => {
  score.value = rectionTime / 1000;
  isPlaing.value = false;
  showResult.value = true;
}

</script>
<template>
  <h1 class="text-2xl text-center font-bold ">Reaction timer</h1>
  <p class="text-center">let's check How much time you need to react</p>
  <button @click="start" :disabled="isPlaing" 
    class="border rounded flex justify-center w-20 pb-1 bg-indigo-500 hover:bg-indigo-600  mx-auto">play</button>
  <component v-if="isPlaing" :is="Block" :delay="delay" @end="gameEnd"></component>
  <component v-if="showResult" :is='Result' :score="score"></component>
  </template>