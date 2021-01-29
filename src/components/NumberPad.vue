<template>
  <div class="NumberPad">
    <div class="output">{{output}}</div>
    <div class="nums">
      <button @click="inputContent">1</button>
      <button @click="inputContent">2</button>
      <button @click="inputContent">3</button>
      <button @click="remove">删除</button>
      <button @click="inputContent">4</button>
      <button @click="inputContent">5</button>
      <button @click="inputContent">6</button>
      <button @click="clear">清空</button>
      <button @click="inputContent">7</button>
      <button @click="inputContent">8</button>
      <button @click="inputContent">9</button>
      <button class="ok" @click="ok">确定</button>
      <button class="zero" @click="inputContent">0</button>
      <button @click="inputContent">.</button>
    </div>
  </div>
</template>

<script lang='ts'>
  import Vue from 'vue';
  import {Component, Prop} from 'vue-property-decorator';

  @Component
  export default class NumberPad extends Vue{
    output: string = '';
    inputContent(event: MouseEvent) {
      const button = (event.target as HTMLButtonElement); // 强制指定类型
      const input = button.textContent!; // 加 ! 表示不会为空
      if(this.output.length === 16) { return; } // 只能输入16位
      if(this.output === '') {
        if('123456789'.indexOf(input)) {
          this.output = input; // 将0替换为1-9
        } else {
          this.output += input; // 在数字后面加上.
        }
        return;
      }
      if(this.output.indexOf('.') >= 0 && input === '.') { return; } // . 只能输入一次
      this.output += input; // 正常输入
    };
    remove() {
      if(this.output.length === 1) {
        this.output = '0'; // 删除所有默认显示0
      } else {
        this.output = this.output.slice(0, -1); // 删除最后一项
      }
    };
    clear() {
      this.output = '0' // 删除所有默认显示0
    };
    ok() {

    }
  }
</script>

<style lang="scss" scoped>
  @import "~@/assets/helper.scss";
  .NumberPad {
    .output {
      font-size: 46px;
      font-family: Consolas, monospace;
      padding: 9px 16px;
      text-align: right;
      height: 87px;
      @extend %innerShadow;
    }
    .nums {
      @extend %clearFix;
      button {
        width: 25%;
        height: 64px;
        float: left;
        border: none;
        background: transparent;
        &.ok {
          height: 64*2px;
          float: right;
        }
        &.zero {
          width: 50%;
        }
        $bg: #f2f2f2;
        &:nth-child(1) {
          background: $bg;
        }
        &:nth-child(2), &:nth-child(5) {
          background: darken($bg, 4%);
        }
        &:nth-child(3), &:nth-child(6), &:nth-child(9) {
          background: darken($bg, 4*2%);
        }
        &:nth-child(4), &:nth-child(7), &:nth-child(10) {
          background: darken($bg, 4*3%);
        }
        &:nth-child(8), &:nth-child(11), &:nth-child(13) {
          background: darken($bg, 4*4%);
        }
        &:nth-child(14) {
          background: darken($bg, 4*5%);
        }
        &:nth-child(12) {
          background: darken($bg, 4*6%);
        }
      }
    }
  }
</style>