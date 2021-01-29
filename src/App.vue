<template>
  <div id="app">
    <router-view/>
  </div>
</template>
<script lang="ts">
  import Vue from 'vue';
  export default Vue.extend({
    components: {

    }
  })
</script>
<style lang="scss">
  @import "~@/assets/reset.scss";
  @import "~@/assets/helper.scss";
  body {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #333;
    line-height: 1.5;
    font-family: $font-hei;
    font-size: 16px;
  }
</style>
