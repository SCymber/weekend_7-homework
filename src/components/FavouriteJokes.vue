<template lang="html">
  <div>
    <p>Favourite Jokes:</p>
    <ul>
    <li v-for="joke in this.favouriteJokes">{{joke.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'joke-fav',
  props: ['favouriteJokes']
}
</script>

<style lang="css" scoped>
</style>
