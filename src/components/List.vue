<script lang="ts" setup>
import {ref } from 'vue'
import Task from '@/components/Task.vue'
import Input from '@/components/Input.vue'
import type { Task as TaskType } from '@/components/Task.vue'

const todos = ref<TaskType[]>([])

const addTodo = (text: string) => {
  if (text.trim()) {
    todos.value.push({
      id: Date.now(),
      text,
      done: false
    })
  }
}

const removeTodo = (id: number) => {
  todos.value = todos.value.filter(todo => todo.id !== id)
}

const toggleDone = (id: number) => {
  const todo = todos.value.find(t => t.id === id)
  if (todo) todo.done = !todo.done
}
</script>

<template>
  <div class="list-wrapper">
    <ul class="todo-list">
      <Task
        v-for="todo in todos"
        :key="todo.id"
        :task="todo"
        @remove="removeTodo(todo.id)"
        @toggle="toggleDone(todo.id)"
      />
      <li class="input-wrapper">
        <Input 
          @add="addTodo" 
        />
      </li>
    </ul>
  </div>
</template>

<style scoped>
.list-wrapper {
  background-color: #0f3d2e; /* verde escuro Doctor Doom */
  padding: 1rem;
  border-radius: 8px;
  width: 100%;
  max-width: 400px;
  border: 4px solid #000; /* borda estilo HQ */
  box-shadow: 6px 6px 0px #000; /* sombra chapada */
}

.todo-list {
  margin: 0;
  padding: 0;
  list-style: none;
}

.input-wrapper {
  margin-top: 1rem;
}

/* Pequeno detalhe de "tira de HQ" nas tasks */
.todo-list li + li {
  margin-top: 0.5rem;
}

/* Placeholder do input em estilo HQ */
.input input::placeholder {
  color: #888;
  font-style: italic;
  font-family: 'Comic Neue', cursive;
  text-shadow: 1px 1px 0px #000;
}

</style>
