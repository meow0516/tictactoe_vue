<template>
  <header class="text-center p-3">
    <h1>This is a Tic Tac Toe!</h1>
  </header>
  <main id="ox_page_container">
    <p>Current Player: {{ currentPlayer }}</p>
    <div class="text-center">
      <button class="restart" @click="reset">Reset</button>
    </div>
    <div class="ox_box_container flex flex-wrap w-full">
      <Box
        v-for="index in 9"
        :key="index"
        :mark="boxes[index - 1].mark"
        :isUsed="boxes[index - 1].isUsed"
        :color="boxes[index - 1].color"
        @click="markBox(index); checkBox(index)"
      />
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
export type box = {
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
  return isOddPlayerTurn.value ? players.odd.mark : players.even.mark
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
let usedNumber = reactive([] as Array<number>)
let isGameEnd = ref(false)
let boxes = reactive([{ mark: '', isUsed: false }, { mark: '', isUsed: false }, { mark: '', isUsed: false }, { mark: '', isUsed: false }, { mark: '', isUsed: false }, { mark: '', isUsed: false }, { mark: '', isUsed: false }, { mark: '', isUsed: false }, { mark: '', isUsed: false }] as Array<box>)

function markBox(index: number) {
  if (isGameEnd.value) {
    alert('the game is ended')
  }
  else {
    if (!usedNumber.includes(index)) {
      if (isOddPlayerTurn.value) {
        boxes[index - 1].mark = players.odd.mark
        boxes[index - 1]['color'] = players.odd.color
      }
      else {
        boxes[index - 1].mark = players.even.mark
        boxes[index - 1]['color'] = players.even.color
      }
      boxes[index - 1].isUsed = true
    }
  }
}

function checkBox(index: number) {
  let isNumberUsed = usedNumber.includes(index)
  if (!isNumberUsed) {
    if (isOddPlayerTurn.value) {
      players.odd.chosenNumber.push(index)
      usedNumber.push(index)
      checkWinner(players.odd)
    }
    else {
      usedNumber.push(index)
      players.even.chosenNumber.push(index)
      checkWinner(players.even)
    }
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
    else {
      if (usedNumber.length == 9) {
        isGameEnd.value = true;
      }
    }
  }
}
function reset() {
  isOddPlayerTurn.value = true
  usedNumber = []
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
