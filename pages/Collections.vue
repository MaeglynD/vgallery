<template>
  <div class="g-collection-simple-container">
    <client-only>
      <carousel></carousel>
    </client-only>
    <nuxt-child />
  </div>
</template>

<script>

export default {
  components: {
    // nuxt is retarded
    carousel: () => import('@/components/carousel.vue')
  },
  data(){
    return {
    }
  }
}

</script>

<style lang="scss" scoped>
  @import './assets/Collections';
</style>