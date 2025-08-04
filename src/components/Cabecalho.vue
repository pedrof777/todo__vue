<script setup>
const props = defineProps(['tarefasPendente'])
</script>
<template>
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
            <h1>Minha tarefas</h1>
            <p>
                Você possui {{props.tarefasPendente}} tarefas pendentes
            </p>
        </header>
</template>