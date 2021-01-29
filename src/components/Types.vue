<template>
  <div>
    <ul class="types">
      <li :class="type === '-' && 'selected'" @click="selectType('-')">支 出</li>
      <li :class="type === '+' && 'selected'" @click="selectType('+')">收 入</li>
    </ul>
  </div>
</template>

<script lang='ts'>
  import Vue from 'vue';
  import {Component, Prop} from 'vue-property-decorator';
  
  @Component

  export default class Types extends Vue{
    type = '-'; // - 支出 + 收入

    selectType(type: string) {
      if(type !== '-' && type !== '+') {
        throw new Error('type is unknow')
      }
      this.type = type
    }
    mounted() {

    }
  }
</script>

<style lang="scss" scoped>
  @import "~@/assets/helper.scss";
  .types {
    background: #c4c4c4;
    display: flex;
    text-align: center;
    font-size: 24px;
    font-weight: bold;
    > li {
      width: 50%;
      height: 64px;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      &.selected::after {
        content: '';
        position: absolute;
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 4px;
        background: #333;
      }
      // &.selected {
      //   // border-bottom: 4px solid #333333; // 使用border会出现选中时文字升高
      // }
    }
  }
</style>