<template>
  <div class="to_do_app">
    <div class="tlt_block">
      <img src="../images/icon.png" alt="Icon" class="title_icon" />
      <h2>To Do List</h2>
    </div>
    <TodoForm @add-todo="addTodo" />
    <TodoList :todos="localTodos" @handle-complete="handleComplete" @delete-todo="deleteTodo" />
  </div>
</template>

<script>
import TodoForm from './TodoForm.vue';
import TodoList from './TodoList.vue';

export default {
  components: {
    TodoForm,
    TodoList
  },
  props: {
    todos: Array
  },
  data() {
    return {
      localTodos: [...this.todos]
    };
  },
  methods: {
    addTodo(todo) {
      this.localTodos.unshift(todo);
      this.$emit('update-todos', this.localTodos);
    },
    handleComplete(id) {
      const todo = this.localTodos.find(todo => todo.id === id);
      if (todo) {
        todo.completed = !todo.completed;
        this.$emit('update-todos', this.localTodos);
      }
    },
    deleteTodo(id) {
      this.localTodos = this.localTodos.filter(todo => todo.id !== id);
      this.$emit('update-todos', this.localTodos);
    }
  },
  watch: {
    todos: {
      handler(newTodos) {
        this.localTodos = [...newTodos];
      },
      deep: true
    }
  }
}
</script>