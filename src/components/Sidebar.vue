<template>
  <div class="sidebar">
    <ui-list
      v-model="categoriesModel"
      :items="categories"
    />
    <div class="sidebar__filter-block">
      <div
        class="sidebar__filter-block_title"
        :class="{ '_center': !(price.from || price.to) }"
      >
        Цена
        <span
          v-if="price.from || price.to"
          class="sidebar__filter-block_clear"
          @click="price = { from: '', to: '' }"
        >
          Очистить
        </span>
      </div>
      <div class="sidebar__filter-block_wrap">
        <ui-input
          v-model="price.from"
          prefix="от"
          class="sidebar__filter-block_grow"
        />
        <span>-</span>
        <ui-input
          v-model="price.to"
          prefix="до"
          class="sidebar__filter-block_grow"
        />
      </div>
    </div>
    <div class="sidebar__filter-block">
      <div
        class="sidebar__filter-block_title"
        :class="{ '_center': !brandsModel.length }"
      >
        Бренд
        <span
          v-if="brandsModel.length"
          class="sidebar__filter-block_clear"
          @click="brandsModel = [], searchBrands = ''"
        >
          Очистить
        </span>
      </div>
      <ui-input
        v-model="searchBrands"
        label="Поиск"
        is-clear
        class="sidebar__filter-block_input"
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
      <ui-checkbox
        v-for="(item, idx) in brands"
        :key="idx"
        v-model="brandsModel"
        :value="item.value"
        :label="item.label"
        :counter="item.counter"
        :class="{ 'sidebar__checkbox_mb': idx < brands.length - 1 }"
      />
    </div>
    <div class="sidebar__filter-block">
      <div
        class="sidebar__filter-block_title"
        :class="{ '_center': !sizesModel.length }"
      >
        Размер
        <span
          v-if="sizesModel.length"
          class="sidebar__filter-block_clear"
          @click="sizesModel = []"
        >
          Очистить
        </span>
      </div>
      <ui-checkbox
        v-for="(item, idx) in sizes"
        :key="idx"
        v-model="sizesModel"
        :value="item.value"
        :label="item.label"
        :counter="item.counter"
        :class="{ 'sidebar__checkbox_mb': idx < sizes.length - 1 }"
      />
    </div>
  </div>
</template>

<script>
import UiInput from '@/components/UI/ui-input.vue'
import UiCheckbox from '@/components/UI/ui-checkbox.vue'
import UiList from '@/components/UI/ui-list.vue'

export default {
  name: 'Sidebar',
  components: {
    UiInput,
    UiCheckbox,
    UiList
  },
  data() {
    return {
      brands: [
        { label: 'Атрибут', value: 'attr1', counter: 3 },
        { label: 'Атрибут', value: 'attr2', counter: 5 },
        { label: 'Атрибут', value: 'attr3', counter: 3 },
        { label: 'Атрибут', value: 'attr4', counter: 7 },
        { label: 'Атрибут', value: 'attr5', counter: 13 },
        { label: 'Атрибут', value: 'attr6', counter: 1 }
      ],
      brandsModel: ['attr1'],
      searchBrands: '',
      sizes: [
        { label: 'Атрибут', value: 'attr1', counter: 4 },
        { label: 'Атрибут', value: 'attr2', counter: 35 },
        { label: 'Атрибут', value: 'attr3', counter: 5 },
        { label: 'Атрибут', value: 'attr4', counter: 8 },
        { label: 'Атрибут', value: 'attr5', counter: 9 },
        { label: 'Атрибут', value: 'attr6', counter: 4 }
      ],
      sizesModel: ['attr2', 'attr5'],
      price: {
        from: '',
        to: ''
      },
      categories: [
        {
          label: 'Название категории',
          key: 'cat-1',
          counter: 13,
          items: [
            {
              label: 'Название категории',
              key: 'cat-2',
              counter: 5
            },
            {
              label: 'Название категории',
              key: 'cat-3',
              counter: 7
            },
            {
              label: 'Название категории',
              key: 'cat-4',
              counter: 10
            },
            {
              label: 'Название категории',
              key: 'cat-5',
              counter: 3
            }
          ]
        }
      ],
      categoriesModel: 'cat-2'
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variables.scss';

.sidebar {
  display: flex;
  flex-direction: column;
  padding-right: 12px;

  &__filter-block {
    display: flex;
    flex-direction: column;
    margin-top: 28px;

    &_title {
      color: $font-primary;
      font-size: 16px;
      font-weight: 700;
      line-height: 20px;
      margin-bottom: 16px;
      display: flex;
      justify-content: space-between;
      align-items: center;

      &._center {
        justify-content: center;
      }
    }

    &_clear {
      color: $font-secondary;
      font-size: 12px;
      font-weight: 400;
      line-height: 1;
      cursor: pointer;
      text-decoration-line: underline;
      transition: color ease-in .2s;

      &:hover {
        color: $font-primary;
      }
    }

    &_input {
      margin-bottom: 16px;
    }

    &_wrap {
      display: flex;
      align-items: center;
      justify-content: space-between;

      span {
        margin: 0 16px;
        color: $font-secondary;
      }
    }

    &_grow {
      flex-grow: 1;
    }
  }

  &__checkbox {
    &_mb {
      margin-bottom: 12px;
    }
  }
}
</style>
