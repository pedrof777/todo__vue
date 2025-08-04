<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue';
import Formulario from './components/Formulario.vue';
import ListaDeTarefas from './components/ListaDeTarefas.vue';

    const estado = reactive({
        filtro: 'todas',
        tarefaTemp: '',
        tarefas: [
            // {
            // titulo: 'Estudar ES6',
            // finalizada: false,    
            // },
            // {
            // titulo: 'Estudar SASS',
            // finalizada: false   ,    
            // },        
            // {
            // titulo: 'Ir para academia',
            // finalizada: true,    
            // }    
        ]
    })

    const getTarefaPendente = () => {
        return estado.tarefas.filter(tarefa => !tarefa.finalizada)
    }

    const getTarefaFinalizada = () => {
        return estado.tarefas.filter(tarefa => tarefa.finalizada)
    }

    const getTarefaFiltrada = () => {
        const {filtro} = estado;

        switch (filtro) {
            case 'pendentes':
                return getTarefaPendente();
            case 'finalizada':
                return getTarefaFinalizada();
            default:
                return estado.tarefas;
        }
    }

    const cadastraTarefa = () => {
        const tarefaNova = {
            titulo: estado.tarefaTemp,
            finalizada: false
        }
        estado.tarefas.push(tarefaNova);
        estado.tarefaTemp = '';
    }
</script>

<template>
    <div class="container">
        <Cabecalho :tarefas-pendente="getTarefaPendente().length"/>
        <Formulario :tarefa-temporaria="estado.tarefaTemp" :filtro="evento => estado.filtro = evento.target.value" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :cadastra-tarefa="cadastraTarefa"/>
        <ListaDeTarefas :tarefas="estado.tarefas.length" :tarefa-filtrada="getTarefaFiltrada()" />
    </div>
    
</template>


