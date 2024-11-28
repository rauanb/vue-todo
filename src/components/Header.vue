<script setup>
    const props = defineProps(['listaPendentesLength'])
</script>

<template>
    <header class="p-5 my-4 bg-light rounded-3">
        <h1>Minhas tarefas</h1>
        <!-- <p>Você possui {{ listaPendentes().length }} tarefas</p> -->
        <!-- Componentização -->
        <p>Você possui {{ props.listaPendentesLength }} tarefas</p>
    </header>
</template>