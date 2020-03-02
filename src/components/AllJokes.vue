<template lang="html">
<div>
<ul>
  <list-item v-for="(joke, index) in jokes" :joke="joke" :key="index"></list-item>
</ul>

</div>
</template>

<script>
import ListItem from './ListItem.vue'
import {eventBus} from '../main.js'
export default {
  name: 'joke-select',
  props: ['jokes'],
  components: {
    "list-item": ListItem
  },
  methods: {
    handleChange(event){
      eventBus.$emit('joke-change', this.joke)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
