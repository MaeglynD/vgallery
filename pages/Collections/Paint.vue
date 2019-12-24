<template>
  <div class="temp">
    <div>{{$route.name.split('-')[1]}}</div>
    <span>coming soon</span>
  </div>
</template>

<script>

export default {
  components: {
  },
}
</script>

<style lang="scss" scoped>
  // @import './assets/Search';
  .temp{
    font-size: 30px;
    letter-spacing: 10px;
    font-weight: 200;
    text-transform: uppercase;
    line-height: 2;
    text-align: center;
  }
</style>