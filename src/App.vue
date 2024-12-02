<script setup>

import { reactive } from 'vue';
import Header from './components/Header.vue';
import Form from './components/Form.vue';
import List from './components/List.vue'

const estado = reactive({
  filtro: 'todas',
  novaTarefa: '',
  tarefas: []
})

const listaPendentes = () => {
  return estado.tarefas.filter(tarefa => !tarefa.finalizada)
}

const listaFinalizadas = () => {
  return estado.tarefas.filter(tarefa => tarefa.finalizada)
}

const listaFiltradas = () => {
  const { filtro } = estado; // Desestruturação, equivalente a const filtro = estado.filtro;

  switch (filtro) {
    case 'pendentes':
      return listaPendentes();
    case 'finalizadas':
      return listaFinalizadas();
    default:
      return estado.tarefas;
  }

}

const adicionaTarefa = () => {
  estado.tarefas.push({
    titulo: estado.novaTarefa,
    finalizada: false
});
estado.novaTarefa = '';
}

</script>

<template>
  <div class="container">
    <!-- Componente -->
    <Header :lista-pendentes-length="listaPendentes().length" />

    <!-- Antes da componentização -->
    <!-- <header class="p-5 my-4 bg-light rounded-3">
      <h1>Minhas tarefas</h1>
      <p>Você possui {{ listaPendentes().length }} tarefas</p>
    </header> -->

    <!-- Componente -->
    <Form :adiciona-tarefa="adicionaTarefa"
    :estado-nova-tarefa="estado.novaTarefa"
    :altera-nova-tarefa="evento => estado.novaTarefa = evento.target.value"
    :altera-filtro="evento => estado.filtro = evento.target.value"/>

    <!-- <form @submit.prevent="adicionaTarefa">
      <div class="row">
        <div class="col">
          <input
          @change="evento => estado.novaTarefa = evento.target.value"
          :value="estado.novaTarefa"
          required 
          class="form-control" 
          type="text" 
          placeholder="Digite uma nova atividade" >
        </div>
        <div class="col-md-2">
          <button type="submit" class="btn btn-primary">Adicionar</button>
        </div>
        <div @change="evento => estado.filtro = evento.target.value" class="col-md-2">
          <select class="form-control">
            <option value="todas">Todas</option>
            <option value="pendentes">Pendentes</option>
            <option value="finalizadas">Finalizadas</option>
          </select>
        </div>
      </div>
    </form> -->

    <!-- Componente -->
    <List :lista-filtradas="listaFiltradas()"/>

    <!-- <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in listaFiltradas()">
        <input 
          @change="evento => tarefa.finalizada = evento.target.checked"
          :checked="tarefa.finalizada" 
          :id="tarefa.titulo" 
          type="checkbox">
        <label 
        class="ms-3" 
        :class="{done: tarefa.finalizada}" 
        :for="tarefa.titulo">
          {{  tarefa.titulo }}
        </label>
      </li>
    </ul> -->
  </div>
</template>