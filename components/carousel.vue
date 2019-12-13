<template>
    <carousel-3d :height="420">
      <slide :index="i" v-for="(x, i) in collectionPanels" :key="x.name" class="g-collection-panel">
          <img :src="x.bg">
          <span class="g-panel-descriptor">{{x.name}}</span>
      </slide>
    </carousel-3d>
  
    <!-- <div class="g-collection-simple-container">
        <simplebar class="height-fix g-collection-core">
        <div class="g-collection-panel" v-for="x in collectionPanels" :key="x.name">
        <!-- <img src="../assets/offline-placeholder.png" alt="">
        
        <img :src="x.bg">
        <span class="g-panel-descriptor">{{x.name}}</span>
    </div>
    </simplebar>
    </div> -->
</template>

<script>
import { Carousel3d, Slide } from 'vue-carousel-3d';

export default {
  components: {
    Carousel3d,
    Slide
  },
  data(){
    return {
      collectionPanels: [
        {name: 'pencil', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099475458654250/pencil-min.png', icon: 'mdi-pencil'},
        {name: 'pastel', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099471255961627/pastel-min.png', icon: 'mdi-grease-pencil'},
        {name: 'paint', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099476297515019/paint-min.png', icon: 'mdi-brush'},
        {name: 'paint1', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099476297515019/paint-min.png', icon: 'mdi-brush'},
        {name: 'paint2', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099476297515019/paint-min.png', icon: 'mdi-brush'},
        {name: 'paint3', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099476297515019/paint-min.png', icon: 'mdi-brush'},
        {name: 'paint4', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099476297515019/paint-min.png', icon: 'mdi-brush'},

      ]
    }
  },

}
</script>

<style lang="scss" scoped>
  @import './assets/Collections';
</style>