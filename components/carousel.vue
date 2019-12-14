<template>
    <carousel-3d :height="420">
      <slide :index="i" v-for="(x, i) in collectionPanels" :key="x.name" class="g-collection-panel">
          <img :src="x.bg">
          <span class="g-panel-descriptor">{{x.name}}</span>
      </slide>
    </carousel-3d>
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
        {name: 'pen', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655435257931235360/pen-min.png', icon: 'mdi-brush'},
        {name: 'college', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655437345348124713/college-min.png', icon: 'mdi-brush'},
        // {name: 'sketches', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099476297515019/paint-min.png', icon: 'mdi-brush'},

      ]
    }
  },

}
</script>

<style lang="scss" scoped>
  @import './assets/Collections';
</style>