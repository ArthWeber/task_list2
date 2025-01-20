<script setup>
    const props = defineProps(['tarefasPendentes'])
</script>

<template>
    <header class="p-5 mb-4 mt-4 bg-dark rounded -3 text-light">
        <h1>Minhas Tarefas</h1>
        <p>
            Você possui {{ props.tarefasPendentes }} pendentes
        </p>
    </header>
</template>