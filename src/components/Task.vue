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
  padding: 0.5rem 0;
  border-bottom: 1px solid #ddd;
  gap: 0.5rem;
  position: relative; 
}

label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  flex: 1;
}

.done {
  text-decoration: line-through;
  color: #888;
}

.remove-btn {
  background: none;
  border: none;
  color: red;
  cursor: pointer;
  padding: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
