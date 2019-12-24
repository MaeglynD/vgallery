<template>
  <div class="g-search-container">
    <v-text-field
      name="name"
      label="Search art genre, medium, title or tags"
      single-line
      class="g-text-field"  
      solo
    ></v-text-field>
  </div>
</template>

<script>

export default {
  components: {
  }
}
</script>

<style lang="scss" scoped>
  @import './assets/Search';
</style>