<!-- filepath: /src/App.vue -->
<template>
  <div>
    <div class="grid">
      <div
        v-for="(cell, index) in cells"
        :key="index"
        :style="{ backgroundColor: cell }"
        class="cell"
        @contextmenu.prevent="onRightClick" 
        @click="onLeftClick"
      ></div>
    </div>
    <div 
      class="frame">
      {{ message }}
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const cells = ref([]) // tableau qui contiendra la couleur de chaque cellule
const message = ref('')

// Remplit la grille en une seule ligne de code
function fillGrid() {
  cells.value = Array(500 * 500).fill('black').map(() => Math.random() < 0.1 ? 'white' : 'black')
}

// Appel de la fonction qui remplit la grille
fillGrid()

function onRightClick() {
  message.value = "clic droit"
}

function onLeftClick() {
  message.value = "clic gauche"
}
</script>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(500, 2px);
  gap: 0;
}
.cell {
  width: 2px;
  height: 2px;
}
.frame {
  margin-top: 20px;
  border: 1px solid black;
  padding: 10px;
  width: fit-content;
  user-select: none;
}
</style>