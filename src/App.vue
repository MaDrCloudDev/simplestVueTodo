<template>
    <div class="container">
      <h1>simplestVueTodo</h1>
      <AddTodo @add="addTodo" />
      <TodoList :todos="todos" @toggle="toggleTodo" @delete="deleteTodo" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AddTodo from './components/AddTodo.vue';
import TodoList from './components/TodoList.vue';

export default defineComponent({
  components: {
    AddTodo,
    TodoList
  },
  data() {
    return {
      todos: [] as { text: string; completed: boolean }[]
    };
  },
  methods: {
    addTodo(text: string) {
      this.todos.push({ text, completed: false });
      this.saveTodos();
    },
    toggleTodo() {
      this.saveTodos();
    },
    deleteTodo() {
      this.saveTodos();
    },
    saveTodos() {
      localStorage.setItem('todos', JSON.stringify(this.todos));
    }
  },
  created() {
    const savedTodos = localStorage.getItem('todos');
    this.todos = savedTodos ? JSON.parse(savedTodos) : [];
  }
});
</script>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
}

body {
  font-family: Arial, sans-serif;
  background-color: black;
  color: #fff;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  max-width: 400px;
  width: 100%;
  text-align: center;
  padding: 20px;
  background-color: #333;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.input-wrapper {
  display: flex;
  margin-bottom: 10px;
}

input[type='text'] {
  flex-grow: 1;
  padding: 8px;
  border: none;
  border-radius: 4px;
  margin-right: 10px;
}

.add-button,
.delete-button {
  padding: 8px 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-button {
  margin-left: 10px;
  background-color: green;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.add-button:hover {
  background-color: #2b8a3e;
}

.delete-button {
  margin-left: 10px; 
  margin-bottom: 5px;
  background-color: red;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.delete-button:hover {
  background-color: #a12424; 
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  background-color: #444;
  border-radius: 4px;
  margin-bottom: 5px;
}


input[type='checkbox'] {
  margin-right: 10px;
}

.completed span {
  text-decoration: line-through;
  opacity: 0.7;
}
</style>
