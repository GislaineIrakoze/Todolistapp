<template>
    <div>
      <h1>{{ welcomeMessage }}</h1>
      <p>Enjoy exploring classic board and card games!</p>
    </div>
  </template>
  
  <script>
  export default {
    name: "Welcome",
    data() {
      return {
        welcomeMessage: ""
      };
    },
    mounted() {
      // Set welcome message when component mounts
      this.welcomeMessage = "Welcome to the Games Wishlist Website!";
    }
  };
  </script>
  
  <style scoped>
  h1 {
    color: #42b983;
    font-size: 2rem;
    margin-bottom: 10px;
  }
  </style>
  