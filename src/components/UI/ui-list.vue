<template>
  <ul
    v-if="items.length"
    class="ui-list"
  >
    <template
      v-for="item in items"
      :key="item.key"
    >
      <li
        class="ui-list__item"
        :class="{ '_child': isChildren, '_active': item.key === modelValue }"
        @click="$emit('update:modelValue', item.key)"
      >
        {{ item.label }}
        <span
          v-if="item.counter"
          class="ui-list__item_counter"
        >
          {{ item.counter }}
        </span>
      </li>
      <ui-list
        :model-value="modelValue"
        v-if="item.items"
        :items="item.items"
        is-children
        @update:modelValue="$emit('update:modelValue', $event)"
      />
    </template>
  </ul>
</template>

<script>
export default {
  name: 'ui-list',
  props: {
    items: {
      type: Array,
      default: () => ([])
    },
    modelValue: {
      type: String,
      default: ''
    },
    isChildren: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';

.ui-list {
  display: flex;
  flex-direction: column;
  margin: 0;
  padding: 0;
  list-style: none;

  &__item {
    font-size: 14px;
    font-weight: 400;
    line-height: 1;
    color: $font-primary;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-radius: 5px;
    padding: 8px 16px 8px 8px;
    cursor: pointer;
    transition: background-color ease-in .2s;

    &:hover {
      background-color: $font-background-hover;

      .ui-list__item_counter {
        color: $font-primary;
      }
    }

    &._child {
      padding-left: 32px;
    }

    &._active {
      color: $brand-primary;
    }

    &_counter {
      color: $font-secondary;
      font-size: 12px;
      font-weight: 400;
      line-height: 1;
      transition: color ease-in .2s;
    }
  }
}
</style>
