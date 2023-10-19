<template>
  <div class="container-max">
    <div class="row gy-24">
      <div class="col-12">
        <header-block/>
      </div>
      <div class="col-12 col-md-4 col-lg-3">
        <sidebar/>
      </div>
      <div class="col-12 col-md-8 col-lg-9">
        <div class="row gx-12 gy-16 g-lg-24">
          <div
            v-for="item in items"
            :key="item.id"
            class="col-6 col-lg-4 col-xl-3"
          >
            <card :item="item"/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import HeaderBlock from '@/components/HeaderBlock.vue'
import Card from '@/components/Card.vue'
import Sidebar from '@/components/Sidebar.vue'

export default {
  name: 'App',
  components: {
    HeaderBlock,
    Card,
    Sidebar
  },
  data() {
    return {
      items: [
        {
          id: 1,
          description: 'Полное название товара в несколько строк для вида с обрывом в конце (этот фрагмент обрежится)',
          sale: 25,
          price: 5990,
          isHit: true,
          brand: 'Бренд 1',
          inStock: true
        },
        {
          id: 2,
          description: 'Полное название товара',
          sale: 30,
          price: 6990,
          isHit: false,
          brand: 'Бренд 1',
          inStock: true
        },
        {
          id: 3,
          description: 'Полное название товара в несколько строк для вида с обрывом в конце (этот фрагмент обрежится)',
          sale: 0,
          price: 6990,
          isHit: true,
          brand: 'Бренд 2',
          inStock: false
        },
        {
          id: 4,
          description: 'Полное название товара в несколько строк для вида с обрывом в конце (этот фрагмент обрежится)',
          sale: 25,
          price: 5990,
          isHit: true,
          brand: 'Бренд 3',
          inStock: true
        },
        {
          id: 5,
          description: 'Полное название товара в несколько строк для вида с обрывом в конце (этот фрагмент обрежится)',
          sale: 0,
          price: 6990,
          isHit: false,
          brand: 'Бренд 4',
          inStock: true
        },
        {
          id: 6,
          description: 'Полное название товара в несколько строк для вида с обрывом в конце (этот фрагмент обрежится)',
          sale: 0,
          price: 6990,
          isHit: true,
          brand: 'Бренд 5',
          inStock: false
        },
        {
          id: 6,
          description: 'Полное название товара в несколько строк для вида с обрывом в конце (этот фрагмент обрежится)',
          sale: 0,
          price: 6990,
          isHit: true,
          brand: 'Бренд 4',
          inStock: true
        },
        {
          id: 7,
          description: 'Полное название товара в несколько строк для вида с обрывом в конце (этот фрагмент обрежится)',
          sale: 10,
          price: 6990,
          isHit: true,
          brand: 'Бренд 5',
          inStock: true
        }
      ]
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/style/variables.scss';

#app {
  font-family: 'PT Sans', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: $font-primary;
  font-size: 14px;
  font-weight: 400;
  line-height: 16px;
}
</style>
