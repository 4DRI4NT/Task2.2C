<template>
    <h2>Product Catalogue</h2>
    <div class="flex-container">
        <div v-for="product in products" :key="product.id" class="productTile">
            <h3>{{ product.fruit }}</h3>
            <p>○ {{ product.price }} <br> ○ {{ product.stock }} kg in store</p>
            <img :src="product.image" :alt="product.fruit">
            <br>
            <button @click="addToCart(product)">Add to Cart</button>
            <br>
            <br>
        </div>
    </div>

    <br>
    <h2>Cart</h2>
    <p v-show="getTotalItems()==0">Your cart is currently empty</p>
    <p v-show="getTotalItems()!=0">Total Items: {{ getTotalItems() }}</p>

    <div class="flex-container">
        <ul class="cartList">
            <li v-for="item in cart" :key="item.id" v-show="item.quantity!=0">
                {{ item.quantity }} {{ item.fruit }}
                <button @click="incrementItem(item)">+</button>
                <button @click="decrementItem(item)">-</button>
                <br>
                <br>
            </li>
        </ul>
    </div>

</template>

<script>
  export default {
    data () {
      return {
        cart: [ {
            //hidden cart item model
            id: 0,
            fruit: "",
            quantity: 0
            }
        ],
        products: [
          {
            id: 10,
            fruit: "Apples",
            price: "$3.00 per kg",
            stock: 120,
            image: "https://cdn.icon-icons.com/icons2/2451/PNG/512/apple_fruit_food_icon_148896.png"
          },
          {
            id: 11,
            fruit: "Bananas",
            price: "$4.50 per kg",
            stock: 180,
            image: "https://cdn.icon-icons.com/icons2/2451/PNG/512/banana_fruit_food_icon_148897.png"
          },
          {
            id: 12,
            fruit: "Oranges",
            price: "$2.50 per kg",
            stock: 90,
            image: "https://cdn.icon-icons.com/icons2/2451/PNG/512/orange_fruit_food_icon_148893.png"
          }
        ]
      }
    },
    methods: {
      addToCart(product) {
        for(let i=1; i<this.cart.length; i++) {
            if(product.id == this.cart[i].id) {
            this.cart[i].quantity++;
            return
            };
        };
        this.cart.push({
            id: product.id,
            fruit: product.fruit,
            quantity: 1
            });
      },
      incrementItem(product) {
        for(let i=1; i<this.cart.length; i++) {
            if(product.id == this.cart[i].id) {
            this.cart[i].quantity++;
            return
            };
        }
      },
      decrementItem(product) {
        for(let i=1; i<this.cart.length; i++) {
            if(product.id == this.cart[i].id) {
            this.cart[i].quantity--;
            return
            };
        }
      },
      getTotalItems() {
        let total = 0;
        for(let i=1; i<this.cart.length; i++) {
            total += this.cart[i].quantity;
        }
        return total
      }
    }
  }
</script>