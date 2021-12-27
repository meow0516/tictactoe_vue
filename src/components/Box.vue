<template>
  <div class="ox_box col-4 border-1" @click="markBox">
    <div class="inner_ox_box flex justify-content-center align-items-center h-6rem text-4xl"></div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

defineProps<{ msg: string }>();

const count = ref(0);
function markBox() {
  console.log('mark');
}
</script>

<template>
  <div class="ox_box col-4 border-1">
    <div
      class="
        inner_ox_box
        flex
        justify-content-center
        align-items-center
        h-6rem
        text-4xl
      "
    ></div>
  </div>
</template>

<style scoped></style>
<style scoped>
.ox_box:hover {
  background-color: rgb(130, 230, 230);
  cursor: pointer;
}
</style>

