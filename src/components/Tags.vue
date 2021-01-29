<template>
  <div class="tags">
    <div class="newTag">
      <button @click="create">新增标签</button>
    </div>
    <ul class="current">
      <li :class="{selected: selectedTags.indexOf(tag)>=0}" v-for="(tag, index) in dataSource" :key="index" @click="toggle(tag)">{{tag}}</li>
    </ul>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue'
  import {Component, Prop} from 'vue-property-decorator';
  @Component
  export default class Tags extends Vue{
    @Prop(Array) readonly dataSource: string[] | undefined;
    selectedTags: string[] = [];
    toggle(tag: string){
      const index = this.selectedTags.indexOf(tag)
      if(index >= 0){
        this.selectedTags.splice(index, 1);
      } else {
        this.selectedTags.push(tag)
      }
    }
    create() {
      const name = window.prompt('请输入标签名');
      if(name === '') {
        window.alert('标签名不能为空')
      } else if(this.dataSource) {
        this.$emit('update:dataSource', [...this.dataSource, name]);
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "~@/assets/helper.scss";
  .tags {
    display: flex;
    flex-direction: column-reverse;
    font-size: 14px;
    padding: 16px;
    > .current {
      display: flex;
      flex-wrap: wrap;
      > li {
        $bg: #d9d9d9;
        $h: 24px;
        padding: 0 16px;
        margin-right: 12px;
        margin-top: 4px;
        height: $h;
        line-height: $h; // 只有一行才能使用
        border-radius: ($h/2);
        background: $bg;
        &.selected {
          background: darken($bg, 50%);
          color: white;
        }
      }
    }
    > .newTag {
      padding-top: 16px;
      button {
        background: transparent;
        border: none;
        color: #999;
        border-bottom: 1px solid;
        padding: 0 4px;
      }
    }
  }
</style>