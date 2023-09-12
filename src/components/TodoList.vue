<template>
  <div class="list">
    <TodoItem v-for="(todo, index) in todos" :key="index" :todo="todo" @toggle="toggleTodo(index)" @delete="deleteTodo(index)" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TodoItem from './TodoItem.vue';

export default defineComponent({
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    toggleTodo(index: number) {
      this.todos[index].completed = !this.todos[index].completed;
      this.saveTodos();
    },
    deleteTodo(index: number) {
      this.todos.splice(index, 1);
      this.saveTodos();
    },
    saveTodos() {
      localStorage.setItem('todos', JSON.stringify(this.todos));
    }
  }
});
</script>
