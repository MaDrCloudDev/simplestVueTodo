<template>
  <div>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new todo" />
    <button class="add-button" @click="addTodo">Add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      newTodo: ''
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.$emit('add', this.newTodo.trim());
        this.newTodo = '';
      }
    }
  }
});
</script>
