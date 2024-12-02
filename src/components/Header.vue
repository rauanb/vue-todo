<script setup>
    const props = defineProps(['listaPendentesLength'])
</script>

<template>
    <header class="p-5 my-4 bg-light rounded-3">
        <h1>Minhas tarefas</h1>
        <!-- <p>Você possui {{ listaPendentes().length }} tarefas</p> -->
        <!-- Componentização -->
        <div v-if="props.listaPendentesLength == 1">
            <p>Você possui {{ props.listaPendentesLength }} tarefa</p>
        </div>
        <div v-else-if="props.listaPendentesLength > 1">
            <p>Você possui {{ props.listaPendentesLength }} tarefas</p>
        </div>
        <p v-else>Parabéns! Não há tarefas pendentes :)</p>
    </header>
</template>