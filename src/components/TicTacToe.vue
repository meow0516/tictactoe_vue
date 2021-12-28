<template>
  <header class="text-center p-3">
    <h1>This is a Tic Tac Toe!</h1>
  </header>
  <main id="ox_page_container">
    <p>Current Player: {{ currentPlayer }}</p>
    <div class="text-center">
      <button class="restart">Reset</button>
    </div>
    <div class="ox_box_container flex flex-wrap w-full">
      <Box :index="index" v-for="index in 9" :key="index" />
      <!-- <div class="ox_box col-4 border-1">
        <div
          class="
            inner_ox_box
            flex
            justify-content-center
            align-items-center
            h-6rem
            text-4xl
          "
        >
          1
        </div>
      </div>
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
        >
          2
        </div>
      </div>
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
        >
          3
        </div>
      </div>
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
        >
          4
        </div>
      </div>
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
        >
          5
        </div>
      </div>
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
        >
          6
        </div>
      </div>
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
        >
          7
        </div>
      </div>
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
        >
          8
        </div>
      </div>
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
        >
          9
        </div>
      </div>-->
    </div>
    <div class="result">
      <p>Winner is: {{ winner }}</p>
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue';
import Box from './Box.vue';
import '/node_modules/primeflex/primeflex.min.css';
import '/node_modules/primeflex/themes/arya-blue.css';

export type TicTacToeProps = {
  oddPlayer?: object;
  evenPlayer?: object;
}
const currentPlayer = 'hello!'
const winner = 'oddPlayer';

</script>
<style scoped></style>
