<script lang="ts" setup>
import { ref } from 'vue';

const text = ref('')

const emit = defineEmits<{
    (e: 'add', text: string): void
}>();

const submit = () => {
    if (text.value.trim()) {
        emit('add', text.value)
        text.value = '';
    }
}

</script>
<template>
    <div class="input-container">
        <input 
        v-model="text"        
        type="text"
        placeholder="Nova Tarefa"
        class="input"
        @keyup.enter="submit"
        />
    </div>

</template>
<style scoped>
.input-container {
    display: flex;
    flex-direction: column;
}

.input {
    background-color: #ddd;
    border: 1px solid #ccc;
    border-radius: 6px;
    padding: 0.75rem;
    font-size: 1rem;
    resize: none;
}

</style>
