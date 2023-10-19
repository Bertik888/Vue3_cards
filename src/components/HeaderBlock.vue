<template>
  <header class="header">
    <img
      src="@/assets/image/logo.svg"
      alt="logo"
      class="header__logo"
    >
    <ui-button
      title="Каталог"
      theme="primary"
      class="header__button"
    />
    <ui-input
      v-model="search"
      label="Поиск по 100 000 товаров"
      is-clear
      class="header__input"
    >
      <template v-slot:icon>
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16" fill="none">
          <g opacity="0.3">
            <path fill-rule="evenodd" clip-rule="evenodd" d="M7.33333 2.75C4.80203 2.75 2.75 4.80203 2.75 7.33333C2.75 9.86464 4.80203 11.9167 7.33333 11.9167C9.86464 11.9167 11.9167 9.86464 11.9167 7.33333C11.9167 4.80203 9.86464 2.75 7.33333 2.75ZM1.25 7.33333C1.25 3.9736 3.9736 1.25 7.33333 1.25C10.6931 1.25 13.4167 3.9736 13.4167 7.33333C13.4167 10.6931 10.6931 13.4167 7.33333 13.4167C3.9736 13.4167 1.25 10.6931 1.25 7.33333Z" fill="#333333"/>
            <path fill-rule="evenodd" clip-rule="evenodd" d="M10.5698 10.5696C10.8627 10.2768 11.3375 10.2768 11.6304 10.5696L14.5304 13.4696C14.8233 13.7625 14.8233 14.2374 14.5304 14.5303C14.2375 14.8232 13.7627 14.8232 13.4698 14.5303L10.5698 11.6303C10.2769 11.3374 10.2769 10.8625 10.5698 10.5696Z" fill="#333333"/>
          </g>
        </svg>
      </template>
    </ui-input>
    <ul class="header__menu">
      <li><a href="#">Информация о компании</a></li>
      <li><a href="#">Контакты</a></li>
      <li><a href="#">Полезные ссылки</a></li>
    </ul>
  </header>
</template>

<script>
import UiInput from '@/components/UI/ui-input.vue'
import UiButton from '@/components/UI/ui-button.vue'

export default {
  name: 'HeaderBlock',
  components: {
    UiInput,
    UiButton
  },
  data() {
    return {
      search: ''
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';
@import '@/assets/style/bootstrap/bootstrap-grid.scss';

.header {
  display: flex;
  align-items: center;
  padding-top: 12px;
  padding-bottom: 12px;

  &__logo {
    margin-right: 8px;
  }

  &__button {
    margin-right: 24px;
    height: 48px;
    border-radius: 10px;
    padding-left: 24px;
    padding-right: 24px;
    border-color: $header-border !important;
    color: $font-primary !important;
    font-weight: 500;
  }

  &__input {
    height: 48px;
    border-radius: 10px;
    border-color: $header-border;
    flex-grow: 1;
  }

  &__menu {
    margin-left: 24px;
    padding: 0;
    list-style: none;
    align-items: center;
    font-size: 14px;
    line-height: 1;
    display: none;

    @include media-breakpoint-up(lg) {
      display: flex;
    }

    li {
      &:not(:last-child) {
        margin-right: 20px;
      }
    }

    a {
      color: $font-primary;
      text-decoration: none;
      transition: color ease-in .2s;

      &:hover {
        color: $font-hover;
      }
    }
  }
}
</style>
