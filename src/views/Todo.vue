<script lang="ts" setup>
import List from '@/components/List.vue'

</script>

<template>
  <div class="container">
    <div class="board-header">
      <h1>To Doom</h1>
    </div>

    <div class="board">
      <List/>
    </div>
  </div>
</template>

<style scoped>
.container {
  background-color: #0f3d2e; /* verde escuro Doctor Doom */
  padding: 2rem;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: 'Comic Neue', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

/* Cabeçalho estilo HQ */
h1 {
  margin-bottom: 1rem;
  color: #d4af37; /* dourado Doctor Doom */
  text-transform: uppercase;
  letter-spacing: 2px;
  text-shadow: 3px 3px #000; /* sombra chapada */
}

/* Centraliza o header */
.board-header {
  display: flex;
  justify-content: center;
  width: 100%;
}

/* Board mantém tasks centralizadas */
.board {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
  width: 100%;
  max-width: 1000px;
}
</style>