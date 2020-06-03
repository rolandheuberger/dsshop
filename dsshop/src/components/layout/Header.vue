<template>
    <header class="shop__header">
        <h1 class="shop__title">dotSource Shop</h1>
        <nav>
        <router-link to="/">Shop</router-link> |
        <router-link to="/cart">Warenkorb</router-link>
        </nav>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .shop__header {
        margin: 3em auto;
        text-align: center;
    }

    .shop__title {
            display: inline-block;
    }

</style>