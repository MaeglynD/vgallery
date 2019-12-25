<template>
  <div class="g-all-container">
    <v-btn icon class="g-fixed-mobile-menu" @click="nav = !nav"><v-icon>mdi-menu</v-icon></v-btn>
    <v-navigation-drawer absolute mobile-break-point="1024" v-model="nav">
      <simplebar class="height-fix">
        <div :class="{'g-panel': true, 'g-panel-active': x.id === activeImg.id }" v-ripple v-for="(x, i) in art" :key="i" @click="(activeImg = x), ($nuxt.$route.query.id = x.id)">
          <parallax-container>
            <parallax-element :parallaxStrength="20" type="depth" tag="div" class="g-panel-img">
              <img :src="x.thumbSrc" :alt="x.name">
              <!-- <img src="../assets/bob-min.png" :alt="x.name">  -->
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
      <v-btn icon class="g-gallery-up" :disabled="art.indexOf(activeImg) === 0" @click="changeActiveImg(-1)"><v-icon>mdi-chevron-up</v-icon></v-btn>
      <v-btn icon class="g-gallery-down" :disabled="art.indexOf(activeImg) === art.length - 1" @click="changeActiveImg(1)"><v-icon>mdi-chevron-down</v-icon></v-btn>
      <v-responsive :aspect-ratio="16/9" max-height="100%">
        <!-- <transition name="component-fade"> -->
          <img :src="activeImg.src" alt="" :key="activeImg.src">
          <!-- Seems like an anti-pattern when positions are just css properties, but the keys in :style arent reactive (i think) -->
          <div :class="['g-active-img-text', ...activeImg.textPosition]">
            <input class="g-invis-id" ref="activeImg-id" />
            <div class="head">
              {{activeImg.name}}
              <v-tooltip bottom transition="fade">
                <template v-slot:activator="{ on }">
                  <v-btn @click="copyURL()" v-on="on" dark icon><v-icon>mdi-paperclip</v-icon></v-btn>
                </template>
               {{ activeCopy === activeImg.id ? 'Copied!' : 'Copy URL'}}
              </v-tooltip>
            </div>
            <div class="desc">{{activeImg.desc.length ? activeImg.desc : 'no description'}}</div>
            <div class="date"><span>Created: </span> {{activeImg.date}}</div>
            <div class="tags"><span>Tags: </span>{{activeImg.tags.length ? activeImgs.tags.join(', ') : 'no tags'}}</div>
          </div>
          <!-- <img src="../assets/bob-compressor.png" alt="" :key="activeImg.src"> -->
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
      activeImg: {},
      activeCopy: null
    }
  },
  created(){
    this.activeImg = this.art[0];

    
  },
  mounted(){
    // the following code, if put in created, doesnt work for production build, idk why
    const queryId = this.$nuxt.$route.query.id

    if(queryId){
      const found = art.find(x => x.id === parseInt(queryId))
      if(found) this.activeImg = found
    }
  },
  methods: {
    copyURL(){
      // Copying to clipboard in js is basically still in the fucking stoneage
      const ref = this.$refs['activeImg-id'];
      ref.value = `${window.location.toString().split('?')[0]}?id=${this.activeImg.id}`
      ref.select();
      document.execCommand('copy');
      this.activeCopy = this.activeImg.id
    },
    changeActiveImg(amount){
      // Current index
      const currentIndex = this.art.indexOf(this.activeImg);
      // Current positive / negative
      const currentSign = Math.sign(amount);
      // If its available, display it
      if(!(currentIndex === this.art.length - 1 && currentSign == 1) && !(currentIndex === 0 && !currentSign)){
        this.activeImg = this.art[currentIndex + amount];
      }
    }
  },
}
</script>

<style lang="scss" scoped>
  @import './assets/All';
</style>
