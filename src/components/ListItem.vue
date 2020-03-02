<template lang="html">
  <li @click="handleChange">{{joke.value}}</li>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'list-item',
  props: ['joke'],
  methods: {
    handleChange(event){
      eventBus.$emit('joke-change', this.joke)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
