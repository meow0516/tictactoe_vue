<script setup lang="ts">
import { ref } from "vue";

defineProps<{ msg: string }>();

const count = ref(0);
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
