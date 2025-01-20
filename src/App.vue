<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Formulario from './components/Formulario.vue';
  import ListaDeTarefas from './components/ListaDeTarefas.vue';

  const estado = reactive({
    filtro: 'todas',
    tarefaTemp: '',
    tarefas: [
      {
        titulo: 'Estudar ES6',
        finalizada: false,
      },
      {
        titulo: 'Estudar SASS',
        finalizada: false,
      },
      {
        titulo: 'Ir para academia',
        finalizada: true,
      },
    ]
  })

  const getTarefasPendentes = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
  }

  const getTarefasFinalizadas = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
  }

  //Filtro de tarefas 
  const getTarefasFiltradas =() => {
    const { filtro } = estado;

    switch (filtro) {
      case 'pendentes':
        return getTarefasPendentes();
      case 'finalizadas':
        return getTarefasFinalizadas();
      default:
        return estado.tarefas;
    }
  }

  //Cadastrar tarefas
  const cadastroTarefa = () => {
    const tarefaNova = {
      titulo: estado.tarefaTemp,
      finalizado: false,
    }
    estado.tarefas.push(tarefaNova);
    estado.tarefaTemp = '';
  }
</script>

<template>
<body class="bg-info">  
  <div class="container"> 
    <Cabecalho />
    <Formulario />
    <ListaDeTarefas />   
  </div>
</body>
</template>

<style scoped>
  .done {
    text-decoration: line-through;
  }
</style>
