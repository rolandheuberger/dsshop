<template>
    <div class="cart__total">
        <span class="cart__totaltext">Subtotal:</span><span id="totalprice" class="cart__subtotal">0 €</span> 
    </div>
</template>

<script>
export default {
    name:"CartTotal"
}
</script>

<style scoped>
  .cart__total {
    border-top: 4px double #ccc;
    padding: 0.5em;
    font-size: 1.5em;
    font-weight: bold;
  }
  .cart__totaltext {
    display: inline-block;
    width: 50%;
  }
  .cart__subtotal {
      display: inline-block;
      width: 50%;
      text-align: right;
  }
</style>