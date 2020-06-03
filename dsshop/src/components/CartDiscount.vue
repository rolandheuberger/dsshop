<template>
    <div>
        <form @submit="discountCart">
            <input type="text" name="discounttext" v-model="discounttext" placeholder="Rabat in Prozent = 0.xx, Absolut in € > 1 ">
            <input type="submit" value="berechne" class="btn">
        </form>
    </div>
</template>
<script>
export default {
    name: "CartDiscount",
    data() {
        return {
            discounttext: ''
        }
    },
    methods: {
        discountCart(e) {
            e.preventDefault();
            this.$emit('add-discount', this.discounttext);
        }
    }
}
</script>
<style scoped>
    form {
        margin-top: 2em;
        display: flex;
    }
    input[type="text"] {
        flex: 10;
        padding: 0.25em;
    }
</style>