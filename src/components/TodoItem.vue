<template>
  <div>
    <input type="checkbox" v-model="todo.completed" @change="toggleTodo" />
    <span @click="toggleCheckbox" :style="{ 'text-decoration': todo.completed ? 'line-through' : 'none', cursor: 'pointer' }">{{ todo.text }}</span>
    <button class="delete-button" @click="deleteTodo">Delete</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  props: ['todo'],
  methods: {
    toggleTodo() {
      this.$emit('toggle');
    },
    toggleCheckbox() {
      this.$emit('toggle');
    },
    deleteTodo() {
      this.$emit('delete');
    }
  }
});
</script>
