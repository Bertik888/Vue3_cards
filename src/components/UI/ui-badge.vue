<template>
  <div class="ui-badge">
    {{ title }}
    <slot name="icon"></slot>
  </div>
</template>

<script>
export default {
  name: 'ui-badge',
  props: {
    title: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';

.ui-badge {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 32px;
  padding: 0px 8px;
  color: $font-primary;
  background-color: $tech-white;
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
  border-radius: 4px;
  border: solid 1px $tech-scroll-bar;
}
</style>

<style lang="scss">
.ui-badge {
  > svg {
    height: 20px;
    width: 20px;
    margin-left: 4px;
  }
}
</style>
