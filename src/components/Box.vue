<template>
  <div class="ox_box col-4 border-1" :class="{ used_box: isUsed }">
    <div
      class="inner_ox_box flex justify-content-center align-items-center h-6rem text-4xl"
      :class="color"
    >{{ mark }}</div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, toRef, toRefs } from 'vue';
const props = defineProps<{
  box: Box
}>()
export type Box = {
  mark: string
  isUsed: boolean
  color?: string
}
let box = toRef(props, 'box')
let { mark, isUsed, color } = toRefs(box.value)

</script>


<style scoped>
.ox_box:hover {
  background-color: rgb(130, 230, 230);
  cursor: pointer;
}
.used_box:hover {
  background-color: white;
  cursor: default;
}
</style>

