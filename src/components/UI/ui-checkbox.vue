<template>
  <div class="ui-checkbox">
    <label>
      <input
        type="checkbox"
        :value="modelValue"
        :checked="isChecked"
        @change="updateInput"
      >
      <span class="ui-checkbox__inner">
        <svg width="12px" height="11px" viewBox="0 0 12 11">
          <polyline points="1 6.29411765 4.5 10 11 1"></polyline>
        </svg>
      </span>
      <span
        v-if="label"
        class="ui-checkbox__label"
      >
        {{ label }}
      </span>
    </label>
    <div
      v-if="counter"
      class="ui-checkbox__counter"
    >
      {{ counter }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'ui-checkbox',
  props: {
    modelValue: {
      type: String,
      default: ''
    },
    value: {
      type: [String, Number, Boolean],
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    counter: {
      type: [String, Number],
      default: ''
    }
  },
  computed: {
    isChecked() {
      if(Array.isArray(this.modelValue)) {
        return this.modelValue.includes(this.value)
      }
      return this.modelValue
    }
  },
  methods: {
    updateInput(event) {
      let isChecked = event.target.checked;

      if(Array.isArray(this.modelValue)) {
        let newValue = [...this.modelValue];

        if(isChecked) {
          newValue.push(this.value)
        } else {
          newValue.splice(newValue.indexOf(this.value), 1)
        }
        this.$emit('update:modelValue', newValue)
      } else {
        this.$emit('update:modelValue', event.target.checked)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';

.ui-checkbox {
  user-select: none;
  position: relative;
  display: flex;
  align-items: center;

  label {
    display: inline-flex;
    align-items: center;
    cursor: pointer;

    &:hover .ui-checkbox__inner {
      border-color: $brand-primary;
    }
  }

  &__inner {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 20px;
    height: 20px;
    border-radius: 3px;
    border: solid 1px $tech-borderand-others;
    transition: all ease-in .2s;

    svg {
      fill: none;
      stroke-linecap: round;
      stroke-linejoin: round;
      stroke: $tech-white;
      stroke-width: 2;
    }

    + span {
      margin-left: 12px;
    }
  }

  &__label {
    font-size: 14px;
    font-weight: 400;
    line-height: 1;
    color: $font-primary;
  }

  &__counter {
    color: $font-secondary;
    font-size: 12px;
    font-weight: 400;
    line-height: 1px;
    position: absolute;
    right: 16px;
  }

  input[type="checkbox"] {
    display: none;
    visibility: hidden;
  }

  input[type="checkbox"]:checked + .ui-checkbox__inner {
    background-color: $brand-primary;
    border-color: $brand-primary;
  }

  input[type="checkbox"]:checked + .ui-checkbox__inner svg {
    transition: all 0.15s ease;
  }
}
</style>
