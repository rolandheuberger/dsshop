<template>
    <section class="shop">
        <div class="shop__item" v-bind:key="item.id" v-for="item in items">
            <ShopItem v-bind:item="item" v-on:add-item="$emit('add-item',item)" />
        </div>
    </section>
</template>

<script>
import ShopItem from "./ShopItem.vue";

export default {
    name: "Shop",
    components: {
        ShopItem
    },
    props: ["items"]
}
</script>

<style scoped>
    .shop {
        margin: 0 auto;
        display: flex;
        flex-direction: row;
        justify-content: space-around;
        flex-wrap: wrap;
        width: 64rem;
    }
</style>