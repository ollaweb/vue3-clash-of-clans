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
import CardStats from '@/components/UI/CardStats.vue'

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
    const item = items.find(el => el.alias === alias)
    this.item = item

    // this.item = this.checkAlias(items, alias)
    // this.redirectToNotFound(item)
    // console.log(this.item) //Не понимаю почему здесь после выполнения функции всегда undefined
    //хотя если выводить шаги в функции, то она возвращает или объект el или null
    //не понимаю, почему тогда item в data не становится тем, чем должен по результату функции
  },
  methods: {
    checkAlias(items, alias) {
      items.find(el => {
        if (el.alias === alias) {
          return el
        }
        return null
      })
    },
    redirectToNotFound(item) {
      if (item === null) {
        this.$router.push({ name: '404' })
      }
    }
  }
}
</script>
