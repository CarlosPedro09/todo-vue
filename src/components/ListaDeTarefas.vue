<script setup>
const props = defineProps(['tarefas']);
</script>

<template>
  <ul class="list-group mt-4">
    <li v-if="!props.tarefas || props.tarefas.length === 0" class="list-group-item text-center">
      Não existem tarefas pendentes
    </li>
    <li v-else v-for="tarefa in props.tarefas" :key="tarefa.titulo" class="list-group-item">
      <input 
        @change="evento => tarefa.finalizada = evento.target.checked" 
        :checked="tarefa.finalizada"
        :id="tarefa.titulo" 
        type="checkbox"
      >
      <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>
</template>

<style scoped>

    .done {
        text-decoration: line-through;
    }
</style>
