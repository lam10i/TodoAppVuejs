<template>
  <div class="container">
    <TodoComponent :todos="todos" @update-todos="updateTodos" />
  </div>
</template>

<script>
import TodoComponent from './components/TodoComponent.vue';

export default {
  components: {
    TodoComponent
  },
  data() {
    return {
      todos: []
    };
  },
  mounted() {
    const storedTodos = JSON.parse(localStorage.getItem('todos'));
    if (storedTodos) {
      this.todos = storedTodos;
    }
  },
  methods: {
    updateTodos(todos) {
      this.todos = todos;
      localStorage.setItem('todos', JSON.stringify(todos));
    }
  }
}
</script>

<style>
@import './App.css';
</style>