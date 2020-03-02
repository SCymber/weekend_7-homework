<template lang="html">
<div v-if="joke" id="jokeDetails">
<h2>{{joke.joke}}</h2>
<p>Joke Category: {{joke.category}}</p>
<!-- <p>Food:</p> -->
<ul>
<!-- <li v-for="food in joke.food_pairing">{{food}}</li> -->
</ul>
<button v-on:click="addToFavourites">Add To Favourites</button>
</div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'joke-details',
  props: ['joke'],
  methods: {
    addToFavourites: function(){
eventBus.$emit('joke-fav', this.joke)
},
}
}
</script>

<style lang="css" scoped>
</style>
