<template>
  <section class="cart">
    <h1 class="cart__headline">Warenkorb</h1>
    <div class="cart__list">
        <div class="cart__item" v-bind:key="item.id" v-for="item in basket"> 
            <CartItem v-bind:item="item" v-on:remove-item="removeItem" />
        </div>
    </div>
     <CartTotal />
     <CartDiscount v-on:add-discount="totalPrice" />
  </section>
</template>

<script>
import CartItem from "../components/CartItem.vue";
import CartTotal from "../components/CartTotal.vue";
import CartDiscount from "../components/CartDiscount.vue";

export default {
    name: "Cart",
    components: {
        CartItem,
        CartTotal,
        CartDiscount
    },
    data() {
      return {
        basket: []
      }
    },
    methods: {
      updateCart() {
        if (localStorage.getItem('cart')) this.basket = JSON.parse(localStorage.getItem('cart'));
        this.totalPrice();
      },
      removeItem(basketitem) {
        for (let cartitem in this.basket) {
          if (this.basket[cartitem].id === basketitem.id && this.basket[cartitem].amount > 1) {
            // remove 1 from amount
            this.basket[cartitem].amount--;
            // save to local storage
            localStorage.setItem('cart', JSON.stringify(this.basket));
          } else if (this.basket[cartitem].id === basketitem.id && this.basket[cartitem].amount === 1) {
            // filter out item and save to local storage
            localStorage.setItem('cart', JSON.stringify(this.basket.filter(item => item.id !== basketitem.id)));
          }
        }
        // load updated cart from local storage
        this.updateCart();
      },
      totalPrice(debate) {
        let total = 0;
        let totalElement = document.getElementById('totalprice');
        debate = debate || 1;

        if (this.basket.length) {
            this.basket.forEach((ele) => {
                total = total + (ele.amount * ele.price);
            });

            if (debate !== 1) {
             total = this.discount(total, debate);
            }
        }
        
        totalElement.innerText = total + ' €';
      },
      discount(total, debate) {
        // calc discount of total
        let reducedTotal = 0;

        if ( debate > 1) { // absolute
          reducedTotal = total - debate;
        } else { // percent
          reducedTotal = Number.parseFloat(total * (1 - debate)).toFixed(2); 
        }

        return reducedTotal;
      }
    },
    mounted() {
      this.updateCart();
    }
}
</script>

<style scoped>
  .cart {
    margin: 0 auto;
    min-width: 320px;
    max-width: 768px;
  }
  .cart__headline { margin: 0 0.5em 1.5em; }
  .cart__item {
    padding: 0.25em 0.5em;
    border-top: 1px solid #ccc;
  }
</style>