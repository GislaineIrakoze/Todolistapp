<template>
  <div class="todo-container">
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Enter a Task to do">
    <input v-model="searchTerm" placeholder="search...">
    <ul>
      <li v-for="(todo, index) in filteredTodos" :key="index">
        <span>{{ todo.text }}</span>
        <div class="btns">
          <button @click="editTodo(index)">📝</button>
          <button @click="deleteTodo(index)">delete</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      searchTerm: '',
      todos: [],
    };
  },
  computed: {
    filteredTodos() {
      return this.todos.filter((todo) =>
        todo.text.toLowerCase().includes(this.searchTerm.toLowerCase())
      );
    },
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({ text: this.newTodo });
        this.newTodo = '';
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    editTodo(index) {
      const newText = prompt('Edit your Task:', this.todos[index].text);
      if (newText !== null && newText.trim() !== '') {
        this.todos[index].text = newText;
      }
    },
  },
};
</script>

<style>
.todo-container {
  max-width: 400px;
  margin: 30px auto;
  padding: 20px;
  border: 2px solid lightblue;
  border-radius: 10px;
  background-color: white;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

input {
  width: 100%;
  padding: 8px;
  margin: 8px 0; /* fixed the comma */
  border: 1px solid lightblue;
  border-radius: 4px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  background-color: #f5f5f5;
  color: #0f172a; 
  margin: 10px 0;
  padding: 10px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

button {
  background-color: orange;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 4px;
  cursor: pointer;
}
</style>
