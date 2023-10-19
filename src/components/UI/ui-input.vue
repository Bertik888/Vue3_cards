<template>
  <div
    class="ui-input"
    :class="{ '_notEmpty': modelValue }"
  >
    <div
      v-if="prefix"
      class="ui-input__prefix"
    >
      {{ prefix }}
    </div>
    <slot name="icon"></slot>
    <input
      type="text"
      :value="modelValue"
      :placeholder="label"
      @input="$emit('update:modelValue', $event.target.value)"
    />
    <svg
      v-if="isClear && modelValue"
      xmlns="http://www.w3.org/2000/svg"
      width="24"
      height="24"
      viewBox="0 0 24 24"
      fill="none"
      class="ui-input__clear"
      @click="$emit('update:modelValue', '')"
    >
      <path fill-rule="evenodd" clip-rule="evenodd" d="M22.0001 12C22.0001 17.5228 17.5229 22 12.0001 22C6.47721 22 2.00006 17.5228 2.00006 12C2.00006 6.47715 6.47721 2 12.0001 2C17.5229 2 22.0001 6.47715 22.0001 12ZM15.7072 9.70711C16.0977 9.31658 16.0977 8.68342 15.7072 8.29289C15.3166 7.90237 14.6835 7.90237 14.293 8.29289L12.0001 10.5858L9.70717 8.29289C9.31664 7.90237 8.68348 7.90237 8.29295 8.29289C7.90243 8.68342 7.90243 9.31658 8.29295 9.70711L10.5858 12L8.29295 14.2929C7.90243 14.6834 7.90243 15.3166 8.29295 15.7071C8.68348 16.0976 9.31664 16.0976 9.70717 15.7071L12.0001 13.4142L14.293 15.7071C14.6835 16.0976 15.3166 16.0976 15.7072 15.7071C16.0977 15.3166 16.0977 14.6834 15.7072 14.2929L13.4143 12L15.7072 9.70711Z" fill="#333333"/>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'ui-input',
  props: {
    modelValue: {
      type: String,
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    prefix: {
      type: String,
      default: ''
    },
    isClear: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';

.ui-input {
  display: flex;
  align-items: center;
  border-radius: 4px;
  border: solid 1px $tech-borderand-others;
  background-color: $tech-white;
  padding: 10px 8px;

  &._notEmpty {
    border-color: $brand-primary;
  }

  input {
    display: flex;
    align-items: center;
    border: none;
    width: 100%;
    min-width: 0;
    height: 22px;
    outline: 0 !important;
    user-select: auto;
    font-size: 14px;
    font-weight: 400;
    line-height: 1;
    padding: 0;

    &::placeholder {
      color: $font-secondary;
    }
  }

  &__prefix {
    font-size: 12px;
    font-weight: 400;
    line-height: 1;
    color: $font-secondary;
    margin-right: 8px;
  }

  &__clear {
    height: 22px;
    width: 22px;
    margin: 0 0 0 8px;
    cursor: pointer;
    opacity: .3;
    transition: opacity ease-in .2s;

    &:hover {
      opacity: 1;
    }
  }
}
</style>

<style lang="scss">
.ui-input {
  > svg {
    height: 16px;
    width: 16px;
    margin-right: 8px;
  }
}
</style>
