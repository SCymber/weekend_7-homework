<template>
  <div id="app">
    <joke-select :jokes='jokes'></joke-select>
    <joke-details :joke='selectedJoke'></joke-details>
    <joke-fav :favouriteJokes='favouriteJokes'></joke-fav>
  </div>
</template>

<script>
import AllJokes from './components/AllJokes.vue';
import JokeDetails from './components/JokeDetails.vue';
import favouriteJokes from './components/FavouriteJokes.vue';
import {eventBus} from './main.js';
export default {
  name: 'App',
  data(){
    return {
      favouriteJokes: [],
      jokes: [],
      selectedJoke: null
    }
  },
  mounted(){
    fetch('http://api.icndb.com/jokes')
    .then(res => res.json())
    .then(data => this.jokes = data)
    eventBus.$on('joke-change', (joke) => {
      this.selectedJoke = joke;
    })
    eventBus.$on('joke-fav', (joke) => {
      this.favouriteJokes.push(this.selectedJoke)
    })
  },
methods: {
  },
  components: {
    "joke-select": AllJokes,
    "joke-details": JokeDetails,
    "joke-fav": favouriteJokes
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
