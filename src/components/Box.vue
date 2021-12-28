<template>
  <div class="ox_box col-4 border-1" @click="markBox">
    <div
      class="inner_ox_box flex justify-content-center align-items-center h-6rem text-4xl"
    >{{ mark }}</div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, toRef, ref } from 'vue';
const props = defineProps<{
  index: number
  usedNumber: Array<number>
  isOddPlayerTurn: boolean
}>()
const index = toRef(props, 'index')
let isOddPlayerTurn = toRef(props, 'isOddPlayerTurn')
let usedNumber = props.usedNumber
let mark = ref()


function markBox() {
  console.log(index.value)
  if (!usedNumber.includes(index.value)) {
    if (isOddPlayerTurn.value) {
      mark.value = 'O'
    }
    else mark.value = 'X'
  }
  // console.log('turn: ' + isOddPlayerTurn.value)
  // console.log('usednumber: ' + usedNumber)
  // emit('myClick', index.value);
  // hasn't choosed -> mark box, don't change background color
  // already choosed -> unable to mark box
}


</script>


<style scoped>
.ox_box:hover {
  background-color: rgb(130, 230, 230);
  cursor: pointer;
}
</style>

