<template lang="html">
  <div v-if="item">
    <p> {{ item.title }} </p>
    <img :src="item.url" alt="">
    <p>Author: {{ item.author }} </p>
  </div>
</template>

<script>
export default {
  name: 'space-detail',
  props: ['item']
}
</script>


<style lang="css" scoped>

div img {

  width: 650px;
  height: 650px;
  border: solid greenyellow 4px;
  border-radius: 20px;
  background: black;
  opacity: 0.675;
  margin-left: 22.5%;

}

p {
  text-align: center;
}

</style>
