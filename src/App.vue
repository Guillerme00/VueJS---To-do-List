<script setup>
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>My tasks</h1>
      <p>
        You have <span></span> pending tasks.
      </p>
    </header>
    <div class="form">
      <div class="row">
        <div class="col">
          <input type="text" class="form-control" placeholder="Descrição da tarefa">
        </div>
        <div class="col-md-1">
          <button type="submit" class="btn btn-primary">Register</button>
        </div>
        <div class="col-md-2">
          <select class="form-control">
            <option value="all">All tasks</option>
            <option value="pending">Pending tasks</option>
            <option value="finished">Finished tasks</option>
            </select>
        </div>
      </div>
    </div>
    <ul class="list-group mt-4">
      <li class="list-group-item">
        <input type="checkbox">
        <label class="ms-3" for="">
          Estudar ES6+
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>
</style>
