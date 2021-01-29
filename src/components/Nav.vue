<template>
  <nav>
    <router-link to="/money" class="item" active-class="selected">
      <Icon name="money" />
      记账
    </router-link>
    <router-link to="/labels" class="item" active-class="selected">
      <Icon name="label" />
      标签
    </router-link>
    <router-link to="/statistics" class="item" active-class="selected">
      <Icon name="statistics" />
      统计
    </router-link>
  </nav>
</template>

<script lang="ts">
  export default({
    name: 'Nav'
  })
</script>

<style lang="scss" scoped>
  @import "~@/assets/helper.scss";
  nav {
    @extend %outerShadow;
    display: flex;
    flex-direction: row;
    font-size: 12px;
    > .item {
      width: 33.33333%;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      padding: 5px 0;
        .icon {
          width: 28px;
          height: 28px;
        }
    }
    > .item.selected {
      color: $color-highlight;
    }
  }
</style>