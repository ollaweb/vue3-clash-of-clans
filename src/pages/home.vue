<template>
  <carousel :settings="settings" :breakpoints="breakpoints">
    <slide class="card__wrapp" v-for="item in items" :key="item.id">
      <Card
        :name="`${item.lvl} lvl`"
        :title="item.title"
        :imgUrl="item.img"
        :link="`/${item.alias}`"
      >
        <template v-slot:body>
          {{ item.descr }}
        </template>
        <template v-slot:footer>
          <CardStats :item="item" />
        </template>
      </Card>
    </slide>
    <template #addons>
      <navigation />
    </template>
  </carousel>
</template>

<script>
import items from '@/seeders/items'
import Card from '@/components/UI/Card'
import CardStats from '@/components/UI/CardStats.vue'

import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
export default {
  components: {
    Card,
    CardStats,
    Carousel,
    Slide,
    Navigation
  },
  data() {
    return {
      items,
      settings: {
        itemsToShow: 2,
        wrapAround: true,
        snapAlign: 'center'
      },
      breakpoints: {
        320: {
          itemsToShow: 1
        },
        768: {
          itemsToShow: 2
        }
      }
    }
  }
}
</script>
