<template>
  <div class="g-all-container">
    <v-btn icon class="g-fixed-mobile-menu" @click="nav = !nav"><v-icon>mdi-menu</v-icon></v-btn>
    <v-navigation-drawer absolute mobile-break-point="1024" v-model="nav">
      <simplebar class="height-fix">
        <div class="g-panel" v-ripple v-for="(x, i) in art" :key="i" @click="(activeImg = x), ($nuxt.$route.query.id = x.id)">
          <parallax-container>
            <parallax-element :parallaxStrength="20" type="depth" tag="div" class="g-panel-img">
              <img :src="x.thumbSrc" :alt="x.name">
            </parallax-element>
          </parallax-container>
          <div class="g-panel-text">
            <div class="g-panel-text-title">{{x.name}}</div>
            <div class="g-panel-text-desc">{{x.desc.length ? x.desc : 'No description'}}</div>
            <div class="g-panel-text-desc">{{x.date}}</div>
          </div>
        </div>
      </simplebar>
    </v-navigation-drawer>
    <div class="g-gallery-main">
      <v-btn icon class="g-gallery-up"><v-icon>mdi-chevron-up</v-icon></v-btn>
      <v-btn icon class="g-gallery-down"><v-icon>mdi-chevron-down</v-icon></v-btn>
      <v-responsive :aspect-ratio="16/9" max-height="100%" style="background: 'red'">
        <!-- <transition name="component-fade"> -->
          <img :src="activeImg.src" alt="" :key="activeImg.src">
        <!-- </transition> -->
      </v-responsive>
    </div>
  </div>
</template>

<script>
import simplebar from 'simplebar-vue';
import 'simplebar/dist/simplebar.min.css';
import Vue from 'vue'
import { ParallaxContainer, ParallaxElement } from 'vue-mouse-parallax'
import art from '../assets/art'

Vue.component('parallax-container', ParallaxContainer)
Vue.component('parallax-element', ParallaxElement)

export default {
  components: {
    simplebar
  },
  data(){
    return {
      nav: true,
      art: art,
      activeImg: {}
    }
  },
  created(){
    this.activeImg = this.art[0];

    const queryId = this.$nuxt.$route.query.id

    if(queryId){
      const found = art.find(x => x.id === parseInt(queryId))
      if(found) this.activeImg = found
    }
  },
  methods: {
    e(){}
  },
}
</script>

<style lang="scss" scoped>
  @import './assets/All';
</style>
