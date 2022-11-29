<script setup>
import { reactive, ref } from "vue";
import socksGreenImage from "./assets/images/socks_green.jpeg";
import socksBlueImage from "./assets/images/socks_blue.jpeg";

const product = ref("Socks");
const image = ref(socksGreenImage);
const inStock = ref(true);
const details = ref(["50% cotton", "30% wool", "20% polyester"]);
const variants = ref([
  { id: 2234, color: "green", image: socksGreenImage },
  { id: 2235, color: "blue", image: socksBlueImage },
]);

const otherProduct = reactive({
  name: "Shoes",
});

const cart = ref(0);

setTimeout(() => {
  product.value = "New Socks";
  otherProduct.name = "New Shoes";
}, 1000);
</script>

<template>
  <div class="nav-bar"></div>
  <div class="cart">🛒 ({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img v-bind:src="image" />
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details" :key="detail">{{ detail }}</li>
        </ul>
        <div v-for="variant in variants" :key="variant.id">
          {{ variant.color }}
        </div>
        <button class="button">Add to Cart</button>
      </div>
    </div>
  </div>
</template>
