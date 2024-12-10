<template>
  <ul class="list_item">
    <li v-for="todo in todos" :key="todo.id" @click="handleComplete(todo.id)" :class="{ checked: todo.completed }">
      {{ todo.text }}
      <span class="delete_icon" @click.stop="deleteTodo(todo.id)">
        <img src="../images/trash.jpg" alt="Delete" class="delete_icon_image" />
      </span>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todos: Array
  },
  methods: {
    handleComplete(id) {
      this.$emit('handle-complete', id);
    },
    deleteTodo(id) {
      this.$emit('delete-todo', id);
    }
  }
}
</script>