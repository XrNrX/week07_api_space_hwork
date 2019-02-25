<template lang="html">
  <div id="container">
    <ul>
      <space-list-item v-for="(item, index) in spaceData" :key="index" :item="item"></space-list-item>
    </ul>
  </div>
</template>

<script>

import SpaceItem from './SpaceItem.vue'

export default {
  name: 'space-list',
  props: ['spaceData'],
  components: {
    'space-list-item': SpaceItem
  }
}
</script>

<style lang="css" scoped>

#container  ul{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}


</style>
