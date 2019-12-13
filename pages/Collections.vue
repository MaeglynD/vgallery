<template>
  <div class="g-collection-core">
    <div class="g-collection-panel" v-for="x in collectionPanels" :key="x.name">
      <img src="../assets/offline-placeholder.png" alt="">
      <span class="g-panel-descriptor">{{x.name}}</span>
    </div>
  </div>
</template>

<script>

export default {
  components: {
  },
  data(){
    return {
      collectionPanels: [
        {name: 'pencil', bg: '../assets/offline-placeholder.png'},
        {name: 'pastel', bg: '../assets/offline-placeholder.png'},
        {name: 'paint', bg: '../assets/offline-placeholder.png'},

      ]
    }
  },

}
</script>

<style lang="scss" scoped>
  @import './assets/Collections';
</style>