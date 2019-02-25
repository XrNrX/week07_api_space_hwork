<template lang="html">
  <div>
    <label>Search: </label>
    <input type="text" v-model="searchInput" v-on:input="searchForItem">
  </div>

</template>

<script>

import { eventBus } from '../main.js'

export default {
  name: 'SpaceSearch',
  props: ['spaceData'],
  data(){
    return {
      searchInput: "",
      searchedItems: []
    }
  },
  methods: {
    searchForItem(){
      this.searchedItems = this.spaceData.filter((item) => item.data.author.toLowerCase().includes(this.searchInput.toLowerCase()))

      eventBus.$emit('searched-items', this.searchedItems)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
