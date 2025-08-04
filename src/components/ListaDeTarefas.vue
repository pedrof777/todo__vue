<script setup>
    const props = defineProps(['tarefaFiltrada', 'tarefas'])
</script>

<template>
    <p v-if="props.tarefas < 1">Nao há tarefas</p>
    <ul v-else class="list-group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefaFiltrada">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
</template>

<style scoped>
.done{
    text-decoration: line-through;
}
</style>