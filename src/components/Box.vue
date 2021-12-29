<template>
  <div class="ox_box col-4 border-1" :class="{ used_box: isUsed }">
    <div
      class="inner_ox_box flex justify-content-center align-items-center h-6rem text-4xl"
      :class="color"
    >{{ mark }}</div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, toRef, ref } from 'vue';
const props = defineProps<{
  index: number
  usedNumber: Array<number>
  isOddPlayerTurn: boolean
  currentPlayerMark: string
  mark: string
  isUsed: boolean
  color?: string
}>()
export type box = {
  mark: string
  isUsed: boolean
  color: string
}
const index = toRef(props, 'index')
let mark = toRef(props, 'mark')
let isUsed = toRef(props, 'isUsed')
let color = toRef(props, 'color')

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

