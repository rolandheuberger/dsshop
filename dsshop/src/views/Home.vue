<template>
  <div id="home">
    <Shop v-bind:items="items" v-on:add-item="addItem" />
  </div>
</template>

<script>
import Shop from '../components/Shop';

export default {
  name: 'Home',
  components: {
    Shop
  },
  data() {
    return {
      items: [
        {
          id: 1,
          title: "Schuhe",
          price: "90",
          imageurl: "https://i.picsum.photos/id/21/320/240.jpg"
        },
         {
          id: 2,
          title: "Uhr",
          price: "22",
          imageurl: "https://i.picsum.photos/id/175/320/240.jpg"
        },
         {
          id: 3,
          title: "Dreirad",
          price: "50",
          imageurl: "https://i.picsum.photos/id/146/320/240.jpg"
        },
        {
          id: 4,
          title: "Tasse",
          price: "8",
          imageurl: "https://i.picsum.photos/id/30/320/240.jpg"
        },
        {
          id: 5,
          title: "Kamera",
          price: "250",
          imageurl: "https://i.picsum.photos/id/250/320/240.jpg"
        },
        {
          id: 6,
          title: "Skateboard",
          price: "22",
          imageurl: "https://i.picsum.photos/id/157/320/240.jpg"
        },
        {
          id: 7,
          title: "Boot",
          price: "1250",
          imageurl: "https://i.picsum.photos/id/124/320/240.jpg"
        },
        {
          id: 8,
          title: "Erdbeeren",
          price: "5",
          imageurl: "https://i.picsum.photos/id/1080/320/240.jpg"
        },
        {
          id: 9,
          title: "Auto",
          price: "500",
          imageurl: "https://i.picsum.photos/id/1072/320/240.jpg"
        }
      ],
      cart: []
    }
  },
  methods: {
    addItem(item) {
      // check if cart is empty
      let itemExist = false;
      if (this.cart.length) {
        for (let cartitem in this.cart) {
          if (this.cart[cartitem].id === item.id) {
            // only iterate amount
            this.cart[cartitem].amount++;
            itemExist = true;
          }
        }
        if (itemExist === false) {
          this.cart = [...this.cart, {...item, ...{amount:1}} ];
        }
      } else {
          // add first item and init amount key/value
          this.cart = [...this.cart, {...item, ...{amount:1}} ];
      }
    }
  },
  mounted() {
      // load cart from local storage
      if (localStorage.getItem('cart')) {
        this.cart = JSON.parse(localStorage.getItem('cart'));
      } else {
        // prefill cart with demo products on first load
        this.cart = JSON.parse('[{"id":4,"title":"Tasse","price":"8","imageurl":"https://i.picsum.photos/id/30/320/240.jpg","amount":3},{"id":2,"title":"Uhr","price":"22","imageurl":"https://i.picsum.photos/id/175/320/240.jpg","amount":2},{"id":1,"title":"Schuhe","price":"90","imageurl":"https://i.picsum.photos/id/21/320/240.jpg","amount":1}]');
      }
  },
  watch: {
    cart: {
      handler() {
        // upddate cart
        localStorage.setItem('cart', JSON.stringify(this.cart));
      },
      deep: true,
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  border: none;
  background-color: hsl(200, 100%, 45%);
  color: #fff;
  padding: 0.5em 1em;
  transition: background-color 0.3s ease-in-out;
  cursor: pointer;
}

.btn:hover {
  background-color: hsl(200, 100%, 25%);
}
</style>
