<template>
  <v-app>
    <div class="g-bg-container"></div>
    <div class="g-content-container">
      <!-- Toolbar -->
      <div :class="{'g-toolbar': true, 'border': $nuxt.$route.name == 'All', 'g-tool-bg': $route.name.includes('-')}">
        <nuxt-link to="/"><v-btn text class="g-home-btn"><span class="weight">victoria.</span>gallery</v-btn></nuxt-link>
        <template v-if="$nuxt.$route.name != 'index' && !is1024">
          <div class="g-h-divider btn-left"></div>
          <div class="g-current-page">
            <nuxt-link :to="{path: x.path}" v-for="x in $route.matched" :key="x.path">{{ x.name.includes('-') ? x.name.split('-')[1] : x.name }}</nuxt-link>
          </div>
        </template>
        <!-- Whatever pages added in future will (probably) go here -->
        <nuxt-link to="/Collections" class="v-btn g-collection-btn">
          <v-btn text class="g-collection-btn">
            <template v-if="is1024">
              <v-icon size="17">mdi-image-multiple</v-icon> 
            </template>
            <template v-else>
              Collections
            </template>
          </v-btn>
        </nuxt-link>
        <div class="g-h-divider btn-left btn-right"></div>
        <nuxt-link to="/Search"><v-btn icon class="g-search"><v-icon size="17">mdi-magnify</v-icon></v-btn></nuxt-link>
      </div>
      <nuxt />
    </div>
  </v-app>
</template>

<script>
export default {
  components: {

  },
  data() {
    return {
      is1024: false

    }
  },
  async mounted(){
    this.testFunc();
    window.addEventListener('resize', this.testFunc);
  },
  methods: {
    // yes this is not good practice
    testFunc(){
      this.is1024 = window.innerWidth <= 1024;
    }
  },
  beforeDestroy(){
    window.removeEventListener('resize',this.testFunc)
  }
}
</script>

<style lang="scss">
  @import './assets/Global';
</style>