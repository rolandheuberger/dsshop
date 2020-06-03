<template>
    <div class="item" :id="item.id">
        <picture class="item__image">
            <img :src="item.imageurl" :alt="item.title" />
            <div class="item__price">{{item.price}} €</div>
        </picture>
        <h2 class="item__title">{{item.title}}</h2>
        <button class="btn item__add" @click="$emit('add-item', item)">kaufen</button>
    </div>
</template>

<script>
export default {
    name:"ShopItem",
    props: ["item"]
}
</script>

<style scoped>
.item {
    margin-bottom: 2em;
}
.item__image { 
    position: relative;
    display: block;
}
.item__image img { display: block; }

.item__price {
    position: absolute;
    bottom: 1em;
    right: 0;
    font-size: 2em;
    padding: 0 0.25em;
    line-height: 1.2;
    background-color: red;
    color: white;
}
.item__title {
    margin: 0.125em 0;
}
 
.item__add {
    margin: 0 auto;
    text-align: center;
    text-transform: uppercase;
}
</style>