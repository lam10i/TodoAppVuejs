<template>
  <form class="input_block" @submit.prevent="handleSubmit">
    <input type="text" id="input_box" placeholder="Add your todo" v-model="input" />
    <button id="add_button">Add</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      input: '',
      productId: 0
    };
  },
  methods: {
    handleSubmit() {
      if (!this.input.trim()) return;
      const todoItem = {
        id: this.productId++,
        text: this.input,
        completed: false
      };
      this.$emit('add-todo', todoItem);
      this.input = '';
    }
  }
}
</script>