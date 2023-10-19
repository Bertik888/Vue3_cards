<template>
  <button
    type="button"
    class="ui-button"
    :class="classes"
    :disabled="disabled"
    @click.prevent="$emit('click')"
  >
    {{ title }}
  </button>
</template>

<script>
export default {
  name: 'ui-button',
  props: {
    title: {
      type: String,
      default: ''
    },
    theme: {
      type: String,
      default: 'default',
      validator(value) {
        return ['primary', 'secondary', 'default'].indexOf(value) !== -1;
      }
    },
    isFullWidth: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    classes() {
      return {
        ['_full-width']: this.isFullWidth,
        [`_${this.theme}`]: true
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';

.ui-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 12px 16px;
  font-size: 14px;
  font-weight: 700;
  line-height: 1;
  border-radius: 4px;
  border-width: 1px;
  border-style: solid;
  transition: all ease-in .2s;
  outline: none;
  background-color: $tech-white;
  cursor: pointer;
  white-space: nowrap;

  &._full-width {
    width: 100%
  }

  &._default {
    color: $font-secondary;
    border-color: $font-secondary;
  }

  &._primary {
    color: $brand-primary;
    border-color: $brand-primary;
  }

  &._secondary {
    color: $tech-white;
    background-color: $brand-primary;
    border-color: $brand-primary;
  }

  &:disabled {
    cursor: not-allowed;
    opacity: .8;
  }
}
</style>
