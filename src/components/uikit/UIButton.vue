<template>
  <!-- <button class="ui-btn" v-on="$listeners"> -->
  <button class="ui-btn" @click="onClickBtn" :class="{
    'ui-btn-large':large,
    'ui-btn-small':small,
    'ui-btn-xsmall':xsmall,
    'ui-btn-xlarge':xlarge,
    'ui-btn-tile':tile,
    'ui-btn-rounded':rounded,
    'ui-btn-circle':circle,
    'ui-btn-disabled':disabled,
    }" :style="`--color-bg-tine:${TintBgColor};`+ `--color-tine:${TintColor};`">
    <slot>Button</slot>
  </button>
</template>


<script lang="ts">
import { Component, Vue, Emit, Prop } from 'vue-property-decorator'

@Component
export default class UIButton extends Vue {
  @Prop(Boolean) private xsmall: boolean | undefined
  @Prop(Boolean) private small: boolean | undefined
  @Prop(Boolean) private large: boolean | undefined
  @Prop(Boolean) private xlarge: boolean | undefined
  @Prop(Boolean) private tile: boolean | undefined
  @Prop(Boolean) private rounded: boolean | undefined
  @Prop(Boolean) private circle: boolean | undefined
  @Prop(Boolean) private disabled: boolean | undefined
  @Prop(String) private bgColor: string | undefined
  @Prop(String) private color: string | undefined

  @Emit('click') private emitClickEmit(event: MouseEvent) {
    if (!this.disabled) console.log(1)
  }

  // 计算属性
  private get TintColor() {
    if (this.color) {
      return this.color
    } else {
      return '#333'
    }
  }
  private get TintBgColor() {
    if (this.bgColor) {
      return this.bgColor
    } else {
      return '#2D8CF0'
    }
  }

  private onClickBtn(event: MouseEvent) {
    this.emitClickEmit(event)
  }
}
</script>


<style lang="stylus" scope>
resize(minWidth, height, paddingLR, fontSize) {
  min-width: minWidth;
  height: height;
  padding: paddingLR;
  font-size: fontSize;

  &.ui-btn-rounded, &.ui-btn-circle {
    radius((@height / 2));
  }

  &.ui-btn-circle {
    width: @height;
    min-width: 0;
    padding: 0;
  }
}

radius(num) {
  border-radius: num;
}

.ui-btn {
  resize(64px, 36px, 0 16px, 0.875em);
  border: 0 solid black;
  radius(4px);
  outline: none;
  letter-spacing: 0.09em;
  font-weight: 500;
  color: var(--color-tine);
  background-color: var(--color-bg-tine);
  cursor: pointer;
  user-select: none;

  &:hover {
    filter: brightness(120%);
  }

  &:active {
    filter: brightness(80%);
  }

  &.ui-btn-xsmall {
    resize(36px, 20px, 0 9px, 0.625em);
  }

  &.ui-btn-small {
    resize(50px, 28px, 0 12px, 0.75em);
  }

  &.ui-btn-large {
    resize(78px, 44px, 0 19px, 0.875em);
  }

  &.ui-btn-xlarge {
    resize(92px, 52px, 0 23px, 1em);
  }

  &.ui-btn-tile {
    radius(0px);
  }

  &.ui-btn-disabled {
    background-color: #eee;
    color: #666;
    cursor: not-allowed;
  }
}
</style>
