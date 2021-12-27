<script setup lang="ts">
import Box from "./Box.vue";
import "/node_modules/primeflex/primeflex.min.css";
import "/node_modules/primeflex/themes/arya-blue.css";
</script>

<template>
  <header class="text-center p-3">
    <h1>This is a Tic Tac Toe!</h1>
  </header>
  <main id="ox_page_container">
    <p>Current Player: {{}}</p>
    <div class="text-center">
      <button class="restart">Reset</button>
    </div>
    <!-- <div class="number_input flex justify-content-center">
      <input
        type="number"
        min="1"
        max="9"
        placeholder="input 1-9"
        id="inputValue"
        class="w-8rem uppercase"
      />
      <input type="submit" value="submit" class="submit w-5rem uppercase" />
    </div>-->

    <div class="ox_box_container flex flex-wrap w-full">
      <Box />
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
  </main>
</template>

<style scoped></style>
