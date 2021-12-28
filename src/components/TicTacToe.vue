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
      <p v-show="isGameEnd">Winner is: {{ winner }}</p>
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref, reactive, computed } from 'vue';
import Box from './Box.vue';
import '/node_modules/primeflex/primeflex.min.css';
import '/node_modules/primeflex/themes/arya-blue.css';

export type TicTacToeProps = {
  oddPlayer?: object;
  evenPlayer?: object;
}
const winnerArray = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
  [1, 4, 7],
  [2, 5, 8],
  [3, 6, 9],
  [1, 5, 9],
  [3, 5, 7],
];
const currentPlayer = computed(() => {
  return isOddPlayerTurn.value ? players.odd.mark : players.even.mark
})
let winner = ref();
let players = reactive({
  odd: {
    name: 'Odd',
    chosenNumber: [],
    mark: 'O',
  },
  even: {
    name: 'Even',
    chosenNumber: [],
    mark: 'X',
  },
})
let isOddPlayerTurn = ref(true);
let usedNumber = reactive([])
let isGameEnd = ref(false)

function checkBox(index: number) {
  let isNumberUsed = usedNumber.includes(index)
  if (!isNumberUsed) {
    if (isOddPlayerTurn.value) {
      players.odd.chosenNumber.push(index)
      checkWinner(players.odd)

    }
    else {
      players.even.chosenNumber.push(index)
      checkWinner(players.even)
    }
    usedNumber.push(index)

    isOddPlayerTurn.value = !isOddPlayerTurn.value
  }
  else {
    alert('this box has been choosed!')
  }
}
function checkWinner(currentPlayer: Players) {
  for (const arr of winnerArray) {
    if (arr.every((value) => currentPlayer.chosenNumber.includes(value))) {
      winner.value = currentPlayer.name
      isGameEnd.value = true;
    }
  }
}
</script>


<style scoped></style>
