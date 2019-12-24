<template>
    <carousel-3d :height="isTiny ? 70 : 420" :disable3d="isTiny" :space="isTiny ? 380 : 270" :controls-visible="isTiny" :class="{'g-tiny': isTiny}">
      <slide :index="i" v-for="(x, i) in collectionPanels" :key="x.name" class="g-collection-panel">
        <template slot-scope="{ isCurrent }">
          <div @click="isCurrent || isTiny ? $nuxt.$router.push({name: `Collections-${x.name}`}) : null">
            <img :src="x.bg">
            <span class="g-panel-descriptor">{{x.name}}</span>
          </div>
        </template>
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
        {name: 'Pencil', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099475458654250/pencil-min.png', icon: 'mdi-pencil'},
        {name: 'Pastel', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099471255961627/pastel-min.png', icon: 'mdi-grease-pencil'},
        {name: 'Paint', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655099476297515019/paint-min.png', icon: 'mdi-brush'},
        {name: 'Pen', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655435257931235360/pen-min.png', icon: 'mdi-brush'},
        {name: 'College', bg: 'https://cdn.discordapp.com/attachments/519416362607837198/655437345348124713/college-min.png', icon: 'mdi-brush'}

      ],
      isTiny: false,

    }
  },
  created(){
    this.isTiny = this.$route.name.includes('-')
  },
  methods: {
  },
  watch: {
    $route(v){
      this.isTiny = v.name.includes('-')

    }
  }

}
</script>

<style lang="scss" scoped>
  @import './assets/Collections';
</style>