<template>
  <div>
    <ul class="types">
      <li :class="type==='-'&&'selected'"
      @click="selectType('-')">支出</li>
      <li  :class="type==='+'&&'selected'"
           @click="selectType('+')">收入</li>
    </ul>
  </div>
</template>

<script lang="ts">

import Vue from 'vue';
import {Component, Prop} from 'vue-property-decorator';
@Component
export default  class Types extends Vue {
  type = '-'// '-'表示支出，'+'表示收入
  @Prop(Number) propA: number|undefined
  //自动将下面代码转换为data、method等等
  //Number告诉vue  propA 是个number    运行时
  //@Prop是个装饰器  告诉vue  propA不是data而是prop
  //number|undefined 就是propA的类型   编译时


  selectType(type: string) {
    if (type !== '-' && type !== '+') {
      throw new Error('type id unknown')
    }
    this.type = type
  }

}


</script>

<style lang="scss" scoped>
.types {
  background: #c4c4c4;
  display: flex;
  text-align: center;
  font-size: 24px;
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
      bottom: 0;
      left: 0;
      width: 100%;
      height: 4px;
      background: #333;
    }
  }
}
</style>