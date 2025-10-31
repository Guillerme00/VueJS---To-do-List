<script setup>
import { reactive } from 'vue';

const estado = reactive({
  filter: 'All tasks',
  temporary: '',
  tarefas: [
    {tittle: "Estudar ES6+", finish: false},
    {tittle: "Estudar SASS", finish: false},
    {tittle: "Estudar VueJS", finish: false},
  ]
});

  const getPending = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finish );
  };

  const getFinished = () => {
    return estado.tarefas.filter(tarefa => tarefa.finish );
  };

  const FilteredTasks = () => {
    const filter = estado.filter;

    switch (filter) {
        case 'pending':
          return getPending()
        case 'finished':
          return getFinished()
        default:
          return estado.tarefas
    }

    
  }
  const RegisterTask = (e) => {
    const newTask = {
      tittle: estado.temporary,
      finish: false
    }
    estado.tarefas.push(newTask);
    estado.temporary = '';
  }
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>My tasks</h1>
      <p>
        You have <span>{{ getPending().length }}</span> pending tasks.
      </p>
    </header>
    <form @submit.prevent="RegisterTask">
      <div class="row">
        <div class="col">
          <input :value="temporary" @change="evento => estado.temporary = evento.target.value" required type="text" class="form-control" placeholder="Descrição da tarefa">
        </div>
        <div class="col-md-1">
          <button type="submit" class="btn btn-primary">Register</button>
        </div>
        <div class="col-md-2">
          <select @change="evento => estado.filter = evento.target.value" class="form-control">
            <option value="all">All tasks</option>
            <option value="pending">Pending tasks</option>
            <option value="finished">Finished tasks</option>
            </select>
        </div>
      </div>
    </form>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in FilteredTasks()">
        <input @change="evento => tarefa.finish = evento.target.checked" v-model="tarefa.finish" :id="tarefa.tittle" type="checkbox">
        <label :class="{done: tarefa.finish}" class="ms-3" :for="tarefa.tittle">
          {{tarefa.tittle}}
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>
  .done {
    text-decoration: line-through;
  }
</style>
