<template>
<div
  class='el-caption'
  @click="click"
  :class="{
    'el-caption--light' : light === true,
    'el-caption--danger' : danger === true,
    'el-caption--clickable': clickable,
    'el-margin--right': marginRight,
    'el-margin--top': marginTop,
    'el-margin--left': marginLeft,
    'el-margin--bottom': marginBottom
  }"
  >

  <slot />
</div>
</template>

<script>

export default {
  name: 'ElCaption',
  props: {
    light: Boolean,
    danger: Boolean,
    marginRight: Boolean,
    marginTop: Boolean,
    marginBottom: Boolean,
    marginLeft: Boolean
  },
  computed: {
    clickable () {
      return this.$listeners && this.$listeners.click
    }
  },
  methods: {
    click () {
      this.$emit('click')
    }
  }
}

</script>

<style scoped lang="less">
  @import '~el-style/variables';

  .el-caption {
    position: relative;
    width: 100%;
    height: auto;
    font-size: @font-size-small;
    text-align: left;
    margin-top: @top-margin-element;
    color: @color-font-dark;
    font-style: italic;

    &--light {
      color: @color-font-light;
    }

    &--danger {
      color: @color-danger-7;
    }

    &--clickable {
      cursor: pointer;

      &:hover {
        text-decoration: underline;
      }
    }
  }
</style>
