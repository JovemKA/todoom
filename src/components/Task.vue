<script lang="ts" setup>
import { ref } from 'vue'

export type Task = {
    id: number,
    text: string,
    done: boolean
}

const props = defineProps<{
  task: Task
}>()

const emit = defineEmits(['remove', 'toggle'])

const showRemove = ref(false)

const onRightClick = (event: MouseEvent) => {
  event.preventDefault()
  showRemove.value = !showRemove.value
}
</script>

<template>
  <li class="task" @contextmenu="onRightClick">
    <label>
      <input type="checkbox" :checked="task.done" @change="$emit('toggle')" />
      <span :class="{ done: task.done }">{{ task.text }}</span>
    </label>
    <button v-if="showRemove" class="remove-btn" @click="$emit('remove')">
        X
    </button>
  </li>
</template>

<style scoped>
.task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.75rem;
  margin-bottom: 0.5rem;
  background-color: #fff;
  border: 4px solid #000; /* borda grossa estilo HQ */
  box-shadow: 4px 4px 0px #000; /* sombra chapada */
  gap: 0.5rem;
  position: relative; 
  transition: transform 0.15s, box-shadow 0.15s;
}

.task:hover {
  transform: translate(-2px, -2px);
  box-shadow: 6px 6px 0px #000;
}

label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  flex: 1;
  font-family: 'Comic Neue', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

input[type="checkbox"] {
  width: 18px;
  height: 18px;
  accent-color: #0f3d2e; /* Verde Doctor Doom */
  cursor: pointer;
}

.done {
  text-decoration: line-through;
  text-decoration-thickness: 3px;
  text-decoration-color: #ff0000; /* riscado vermelho dramático */
  color: #888;
}

.remove-btn {
  background-color: #ff0000; /* Vermelho HQ */
  border: 3px solid #000;
  color: #fff;
  font-weight: bold;
  cursor: pointer;
  padding: 0.4rem 0.6rem;
  box-shadow: 2px 2px 0px #000;
  transition: transform 0.15s, box-shadow 0.15s;
}

.remove-btn:hover {
  transform: translate(-1px, -1px);
  box-shadow: 4px 4px 0px #000;
}
</style>
