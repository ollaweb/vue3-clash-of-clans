<template>
    <div class="card__wrapp" v-for="item in items" :key="item.id">
        <Card :name="`${item.lvl} lvl`" :title="item.title" :imgUrl="item.img">
            {{item.descr}}
        </Card>
    </div>
</template>

<script>
import items from "@/seeders/items.json";
import Card from "@/components/UI/Card";
export default{
    components: {Card},
    data() {
        return {
           items
        }
    }
}
</script>
