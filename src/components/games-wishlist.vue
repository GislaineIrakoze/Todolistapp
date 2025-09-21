<template>
    <div>
      <h1>Games Wishlist</h1>
  
      <form @submit.prevent="addGame">
        <input v-model="newGame.name" placeholder="Game name" required />
        <input v-model="newGame.type" placeholder="Game type" required />
        <input v-model="newGame.image" placeholder="Image URL" required />
        <button type="submit">Add Game</button>
      </form>
  
      <ul>
        <li v-for="game in Games" :key="game.id">
          <img :src="game.image" :alt="game.name" width="150" />
          <p><strong>{{ game.name }}</strong> ({{ game.type }})</p>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: "GamesWishlist",
    data() {
      return {
        Games: [
          {
            id: 1,
            name: "Checkers",
            type: "Board Game",
            image: "checkers.jpg"
          },
          {
            id: 2,
            name: "Chess",
            type: "Board Game",
            image: "chess.jpg"
          },
          {
            id: 3,
            name: "Billiards",
            type: "Table Game",
            image: "billiard.jpg"
          },
          {
            id: 4,
            name: "Ludo",
            type: "Family Game",
            image: "ludo.jpg"
          },
          {
            id: 5,
            name: "Poker",
            type: "Card Game",
            image: "poker.jpg"
          },
          {
            id: 6,
            name: "Snakes and ladders",
            type: "Board Game",
            image: "snakes.and.ladders.jpg"
          },
          {
            id: 7,
            name: "Dart",
            type: "Pub Game",
            image: "dart.jpg"
          },
        ],
        newGame: {
          name: "",
          type: "",
          image: ""
        }
      };
    },
    methods: {
      addGame() {
        const newId = this.Games.length + 1;
        const gameToAdd = {
          id: newId,
          name: this.newGame.name,
          type: this.newGame.type,
          image: this.newGame.image
        };
        this.Games.push(gameToAdd);
  
        // Reset form
        this.newGame.name = "";
        this.newGame.type = "";
        this.newGame.image = "";
      }
    }
  };
  </script>
  
  <style scoped>
  h1 {
    color: #2c3e50;
  }
  
  form {

    margin-bottom: 20px;
  }
  
  form input {
    margin-right: 10px;
    padding: 5px;
  }
  
  ul {
    list-style: none;
    padding: 0;
    display: flex;
    flex-wrap: wrap;
  }
  
  li {
    margin: 10px;
    text-align: center;
    max-width: 200px;
  }
  
  img {
    border-radius: 8px;
    width: 100%;
    height: auto;
  }
  </style>
  