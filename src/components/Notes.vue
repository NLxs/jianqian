<template>
  <div>
    <label class="notes">
      <span class="name">备注: </span>
      <input type="text" v-model="value" placeholder="在这输入内容">
    </label>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Prop} from 'vue-property-decorator';
  @Component

  export default class Notes extends Vue {
    value = '';
    oninput(event: KeyboardEvent) {
      const input = event.target as HTMLInputElement;
      this.value = input.value;
    }
  }
</script>

<style lang="scss" scoped>
  @import "~@/assets/helper.scss";
  .notes {
    display: block;
    background: #f5f5f5;
    padding-left: 16px;
    display: flex;
    align-items: center;
    .name {
      padding-right: 12px;
    }
    input {
      height: 64px;
      flex-grow: 1;
      background: transparent;
      border: none;
    }
  }
</style>