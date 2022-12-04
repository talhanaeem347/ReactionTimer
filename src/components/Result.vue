<script setup lang="ts">
import { ref } from 'vue';
const props = defineProps<{
  score: number
}>()
let rank = ref<string>()
const vMyDirective = ({
  mounted: () => {
    if (props.score <= 0.25)
      rank.value = 'Best Reaction Time'
    else if (props.score <= 0.4)
      rank.value = 'Good Reaction Time'
    else if (props.score > 1)
      rank.value = 'To   Lazzy'
    else
      rank.value = 'Average Reaction Time'
  },
})
</script>

<template>
  <section v-my-directive class="w-full">

    <div class="border w-64 py-16 flex items-center justify-center mx-auto my-2 bg-indigo-300  rounded-lg flex-col  ">
      <p>You Reacted in {{ score }} seconds</p>
      <p class="text-center text-xl text-red-400">{{    rank    }}</p>
    </div>
  </section>
</template>