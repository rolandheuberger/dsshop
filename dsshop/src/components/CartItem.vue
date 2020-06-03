<template>
    <div class="item" :id="item.id">
        <button class="btn item__remove" @click="$emit('remove-item', item)">x</button>
        <picture class="item__image">
            <img :src="item.imageurl" :alt="item.title" />
        </picture>
        <div class="item__title">{{item.title}}</div>
        <div class="item__amount">{{item.amount}} x</div>
        <div class="item__price">{{item.price}} €</div>
    </div>
</template>

<script>
export default {
    name:"CartItem",
    props: ["item"]
}
</script>

<style scoped>
.item { 
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    align-items: center;
}
.item__remove {
    height: 1.5em;
    width: 1.5em;
    font-size: 1em;
    text-align: center;
    line-height: 1em;
    padding: 0 0.5em 0.15em;
    background-color: #ccc;
    color: #333;
    border-radius: 50%;
    margin-right: 1em;
}
.item__image {
    display: inline-block; 
    margin-right: 1em;
    width: 60px;
}
.item__image img { 
    display: block;
    width: 100%;
}
.item__title {
    margin: 0.125em 0;
}
.item__amount {
    flex-grow: 2;
    text-align: right;
}
.item__price { 
    text-align: right;
    min-width: 60px;
}

</style>