<template lang="html">
  <div>
  <h1>SPACE! THE FINAL FRONTIER ( So Says Picard! )</h1>
  <button v-if="selectedItem" v-on:click="goBack">Previously Searched</button>
  <searched-items v-if="!selectedItem" :spaceData="spaceData"></searched-items>
  <space-list v-if="!selectedItem && !searchedItems" :spaceData="spaceData"></space-list>
  <space-list v-if="searchedItems && !selectedItem" :spaceData="searchedItems"></space-list>
  <space-detail v-if="selectedItem" :item="selectedItem"></space-detail>
</div>
</template>

<script>

import { eventBus } from './main.js';
import SpaceItem from './components/SpaceItem.vue';
import SpaceList from './components/SpaceList.vue';
import SpaceDetail from './components/SpaceDetail.vue';
import SpaceSearch from './components/SpaceSearch.vue';


export default {
  name: 'app',
  data(){
    return {
      spaceData: [],
      selectedItem: null,
      searchedItems: null
    };
  },
  mounted(){
    fetch('https://www.reddit.com/r/spaceporn/.json?limit=45')
    .then(res => res.json())
    .then(spaceData => this.spaceData = spaceData.data.children)

    eventBus.$on('space-item-selected', (item) => {
      this.selectedItem = item
    })

    eventBus.$on('searched-items', (spaceData) => {
      this.searchedItems = spaceData
    })
  },
  components: {
    'space-item': SpaceItem,
    'space-list': SpaceList,
    'space-detail': SpaceDetail,
    'searched-items': SpaceSearch
  },
  methods: {
    goBack() {
      this.selectedItem = null;
    }
  }
}
</script>

<style>

body {
  font-family: monospace;
  background: url('./assets/space-bground4.jpg');
  color: green;
}

div input, label{
  background-color: black;
  color: greenyellow;
  opacity: 0.5;
  margin-left: 45%;
}


</style>

<style lang="css" scoped>

h1 {
  text-align: center;
  color: green;
  font-size: 28px;
}

div button {
  background-color: black;
  color: greenyellow;
  opacity: 0.685;
  font-size: 22px;
  border-radius: 10px;
  font-family: monospace;
  margin-left: 40%;
}


</style>
