<script setup>
    const props = defineProps(['cadastraTarefa', 'editaTarefaTemp', 'tarefaTemporaria', 'filtro'])
</script>

<template>
    <form @submit.prevent="props.cadastraTarefa">
        <div class="row">
            <div class="col ">
                <input :value="props.tarefaTemporaria" @change="props.editaTarefaTemp" class="form-control" type="text" required placeholder="Digite sua tarefa" >
            </div>
            <div class="col-md-2">
                <button type="submit" class="btn btn-primary">Cadastrar tarefa</button>
            </div>
            <div class="col-md-2">
                <select @change="props.filtro" class="form-control">
                    <option value="todas">Todas tarefas</option>
                    <option value="pendentes">Pendentes</option>
                    <option value="finalizada">Finalizadas</option>
                </select>
            </div>
        </div>
    </form>
</template>