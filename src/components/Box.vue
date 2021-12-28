<template>
  <div class="ox_box col-4 border-1" @click="markBox">
    <div class="inner_ox_box flex justify-content-center align-items-center h-6rem text-4xl"></div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, toRef } from 'vue';
const props = defineProps<{
  index: number
}>()
const index = toRef(props, 'index')


function markBox() {
  console.log(index.value)
}
</script>


<style scoped>
.ox_box:hover {
  background-color: rgb(130, 230, 230);
  cursor: pointer;
}
</style>

