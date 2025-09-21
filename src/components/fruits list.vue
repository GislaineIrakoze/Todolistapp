<template>
    <!-- Add New Fruit -->
    <input v-model="newFruit" placeholder="Please enter the name of a fruit" />
    <button @click="checkFruit">Add</button>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newFruit: '',
        fruits: [
          { id: 1, name: 'Apple', color: 'Red' },
          { id: 2, name: 'Banana', color: 'Yellow' },
        ],
      };
    },
    methods: {
      checkFruit() {
        if (this.newFruit.trim() !== '') {
          this.fruits.push({
            id: Date.now(),
            name: this.newFruit,
            color: 'Unknown',
          });
          this.newFruit = '';
        }
      },
    },
  };
  </script>
  <style scoped>
  input {
    margin-bottom: 10px;
  }
  </style>
  
