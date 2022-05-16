<template>
  <div style="text-align: center" class="wrapper">
    <div v-if="item">
      <img :src="item.img" :alt="item.descr" />
      <h1 style="color: #ffffff" class="title">{{ item.title }}</h1>
      <p>{{ item.descr }}</p>
      <CardStats :item="item" style="margin: 20px 0; border-radius: 14px" />
      <div>
        <router-link to="/" class="btn btnPrimary">Back to Home</router-link>
      </div>
    </div>
  </div>
</template>

<script>
import items from '@/seeders/items'
import CardStats from '@/components/UI/Card/CardStats.vue'

export default {
  components: {
    CardStats
  },
  data() {
    return {
      item: null
    }
  },
  created() {
    const alias = this.$route.params.itemAlias
    const item = alias && items.find(el => el.alias === alias)
    if (!item) {
      this.$router.push({ name: '404' })
    }
    this.item = item
  }
}
</script>
