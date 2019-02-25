<template lang="html">
  <div v-on:click="handleClick" id="items">
    <!-- <h3> {{ item.data.title }} </h3> -->
    <img :src="item.data.url" alt="">
    <p><b>Auth:</b> {{ item.data.author }}</p>
    <!-- <p>Subs: {{ item.data.subreddit_subscribers }} </p> -->
  </div>
</template>

<script>

import { eventBus } from '../main.js'

export default {
  name: 'space-item',
  props: ['item'],
  methods: {
    handleClick(){
      eventBus.$emit('space-item-selected', this.item.data)
    }
  }
}
</script>

<style lang="css" scoped>

img {
  height: 50px;
  width: 50px;
  padding: 10px;
}

#items {
  padding: 15px;
  display: flex;
  border: solid greenyellow 2px;
  margin: 15px;
  background-color: black;
  border-radius: 20px;
  opacity: 0.675;
  /* flex-direction: row; */

}

p {
  color: green;
}

p b {
  color: purple;
}

</style>
