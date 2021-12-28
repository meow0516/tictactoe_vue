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
      <Box
        v-for="index in 9"
        :key="index"
        :index="index"
        :isOddPlayerTurn="isOddPlayerTurn"
        :usedNumber="usedNumber"
        @click="checkBox(index)"
      />
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

let isOddPlayerTurn = ref(true);
let usedNumber = reactive([])

function checkBox(index) {
  let isNumberUsed = usedNumber.includes(index)
  if (!isNumberUsed) {
    usedNumber.push(index)
    players.odd.chosenNumber.push(index)

    isOddPlayerTurn.value = !isOddPlayerTurn.value
    console.log('parents turn: ' + isOddPlayerTurn.value)
  }
  else {
    alert('this box has been choosed!')
  }


}
</script>
<style scoped></style>
