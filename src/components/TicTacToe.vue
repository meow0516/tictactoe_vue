<template>
  <header class="text-center p-3">
    <h1>This is a Tic Tac Toe!</h1>
  </header>
  <main id="ox_page_container">
    <p>Current Player: {{ currentPlayer.mark }}</p>
    <div class="text-center">
      <button class="restart" @click="reset">Reset</button>
    </div>
    <div class="ox_box_container flex flex-wrap w-full">
      <Box v-for="(box,index) in boxes" :key="index" :box="box" @click="markBox(index)" />
    </div>
    <div class="result">
      <p v-if="isGameEnd && winner.length > 0">Winner is: {{ winner }}</p>
      <p v-else-if="isGameEnd">Draw</p>
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref, reactive, computed } from 'vue';
import Box from './Box.vue';


export type TicTacToeProps = {
  oddPlayer?: object;
  evenPlayer?: object;
}
export type Players = {
  name: string
  chosenNumber: Array<number>
  mark: string
  color?: string;
}
export type Box = {
  mark: string
  isUsed: boolean
  color?: string
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
  return isOddPlayerTurn.value ? players.odd : players.even
})
let winner = ref('');
let players = reactive({
  odd: {
    name: 'Odd',
    chosenNumber: [] as Array<number>,
    mark: 'O',
    color: 'text-pink-500'
  } as Players,
  even: {
    name: 'Even',
    chosenNumber: [] as Array<number>,
    mark: 'X',
    color: 'text-cyan-500'
  } as Players,
})
let isOddPlayerTurn = ref(true);
let isGameEnd = ref(false)
let boxes = reactive(<Array<Box>>[{ mark: '', isUsed: false, color: undefined }, { mark: '', isUsed: false, color: undefined }, { mark: '', isUsed: false, color: undefined }, { mark: '', isUsed: false, color: undefined }, { mark: '', isUsed: false, color: undefined }, { mark: '', isUsed: false, color: undefined }, { mark: '', isUsed: false, color: undefined }, { mark: '', isUsed: false, color: undefined }, { mark: '', isUsed: false, color: undefined }])

function markBox(index: number) {
  if (isGameEnd.value) {
    return alert('The game is ended, please reset')
  }

  let isNumberUsed = boxes[index].isUsed
  if (isNumberUsed) {
    return alert('This box has been chosen!')
  }

  Object.assign(boxes[index], currentPlayer.value, { isUsed: true })
  if (isOddPlayerTurn.value) {
    players.odd.chosenNumber.push(index + 1)
  }
  else {
    players.even.chosenNumber.push(index + 1)
  }
  checkWinner(currentPlayer.value)
  isOddPlayerTurn.value = !isOddPlayerTurn.value
}

function checkWinner(currentPlayer: Players) {
  for (const arr of winnerArray) {
    if (arr.every((value) => currentPlayer.chosenNumber.includes(value))) {
      winner.value = currentPlayer.name
      isGameEnd.value = true;
    }
    else {
      if (boxes.filter(box => box.isUsed).length === 9) {
        isGameEnd.value = true;
      }
    }
  }
}
function reset() {
  isOddPlayerTurn.value = true
  isGameEnd.value = false
  boxes.forEach(box => {
    box.mark = ""
    box.isUsed = false
  });
  winner.value = ''
  players.odd.chosenNumber = []
  players.even.chosenNumber = []
}



</script>


<style scoped></style>
