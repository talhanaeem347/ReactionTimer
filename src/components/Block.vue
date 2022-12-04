<script setup lang="ts">
import { ref } from 'vue';

const props = defineProps<{ delay: number }>()
const emit = defineEmits<{
  (e: 'end', timer: number): void
}>()
let showBlock = ref(false)
let timer = ref<number>(0)
let rectionTime = ref<number>(0)
let startTimer = () => {
  timer.value = setInterval(() => rectionTime.value += 10, 10);
}
let stopTimer = () => {
  clearInterval(timer.value)
  emit('end', rectionTime.value)

}
const vMyDirective = ({
  mounted: () => {
    setTimeout(() => {
      showBlock.value = true
      startTimer()
    }
      , props.delay);
  },
});
</script>
<template>
  <section v-my-directive class="w-full">
    <div v-if="showBlock" @click="stopTimer"
      class="border w-64 py-16 flex items-center justify-center mx-auto my-2 bg-green-300 hover:bg-green-400 active:bg-green-200 rounded-lg">
      click me</div>
  </section>
</template>