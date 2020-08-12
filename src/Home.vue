<template>
  <div class="home">
    <div class="btn-container">
      <UIButton @click="onClick" :xsmall="xsmall" :small="small" :large="large" :xlarge="xlarge" :tile="tile" :rounded="rounded" :circle="circle" :disabled="disabled" bgColor="red" color="yellow">1</UIButton>
    </div>
    <div class="btn-group">
      <UIButton @click="resize('xsmall')">xsmall</UIButton>
      <UIButton @click="resize('small')">small</UIButton>
      <UIButton @click="resize('normal')">normal</UIButton>
      <UIButton @click="resize('large')">large</UIButton>
      <UIButton @click="resize('xlarge')">xlarge</UIButton>
    </div>
    <div>
      <UIButton @click="changeRadius('tile')">tile</UIButton>
      <UIButton @click="changeRadius('rounded')">rouded</UIButton>
      <UIButton @click="changeRadius('circle')">circle</UIButton>
    </div>
    <div>
      <UIButton @click="changeDisabled">disabled</UIButton>
    </div>
  </div>
</template>


<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import UIButton from '@/components/uikit/UIButton.vue'
@Component({
  components: {
    UIButton,
  },
})
export default class Home extends Vue {
  private xsmall = false
  private small = false
  private large = false
  private xlarge = false
  private tile = false
  private rounded = false
  private circle = false
  private disabled = false
  // 是否禁用
  private changeDisabled() {
    this.disabled = !this.disabled
  }
  // 圆角
  private changeRadius(name: string) {
    switch (name) {
      case 'tile':
        this.tile = true
        this.rounded = false
        this.circle = false
        break
      case 'rounded':
        this.rounded = true
        this.tile = false
        this.circle = false
        break
      case 'circle':
        this.circle = true
        this.tile = false
        this.rounded = false
        break
    }
  }
  // 大小
  private resize(name: string) {
    switch (name) {
      case 'xsmall':
        this.xsmall = true
        this.small = false
        this.large = false
        this.xlarge = false
        break
      case 'small':
        this.small = true
        this.xsmall = false
        this.large = false
        this.xlarge = false
        break
      case 'normal':
        this.xsmall = false
        this.small = false
        this.large = false
        this.xlarge = false
        break
      case 'large':
        this.large = true
        this.xsmall = false
        this.small = false
        this.xlarge = false
        break
      case 'xlarge':
        this.xlarge = true
        this.xsmall = false
        this.small = false
        this.large = false
        break
    }
  }
  private onClick(event: MouseEvent) {
    // console.log(event)
  }
}
</script>


<style lang="less" scope>
.btn-container {
  width: 480px;
  height: 160px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.ui-btn {
  margin: 6px;
}
</style>
