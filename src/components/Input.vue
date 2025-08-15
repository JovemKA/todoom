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
    background-color: #fff; /* fundo claro para o texto se destacar */
    border: 4px solid #000; /* borda grossa estilo quadrinhos */
    padding: 0.75rem;
    font-size: 1rem;
    font-family: 'Comic Neue', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    box-shadow: 3px 3px 0px #000; /* sombra chapada HQ */
    outline: none;
    transition: transform 0.15s, box-shadow 0.15s;
}

.input:focus {
    transform: translate(-2px, -2px);
    box-shadow: 5px 5px 0px #000;
    border-color: #d4af37; /* dourado Doctor Doom */
}

</style>
