<template>
  <v-app>
    <div class="g-bg-container"></div>
    <div class="g-content-container">
      <!-- Toolbar -->
      <div :class="{'g-toolbar': true, 'border': $nuxt.$route.name == 'All'}">
        <nuxt-link to="/"><v-btn text class="g-home-btn"><span class="weight">victoria.</span>gallery</v-btn></nuxt-link>
        <template v-if="$nuxt.$route.name != 'index'">
          <div class="g-h-divider btn-left"></div>
          <div class="g-current-page">{{$nuxt.$route.name}}</div>
        </template>
        <v-btn text class="g-collection-btn">Collections</v-btn>
        <div class="g-h-divider btn-left btn-right"></div>
        <v-btn icon class="g-search"><v-icon size="17">mdi-magnify</v-icon></v-btn>
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
    }
  }
}
</script>

<style lang="scss">
  @import './assets/Global';
</style>