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
  background-color: #f0f0f0;
  padding: 2rem;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  margin-bottom: 1rem;
}

.board-header {
  justify-items: center;
}

.board {
  display: flex;
  gap: 1rem;
  justify-content: center;
}
</style>