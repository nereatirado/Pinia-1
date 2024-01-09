<script setup>
import TheHeader from "@/components/TheHeader.vue";
import ProductCard from "@/components/ProductCard.vue";
// import products from "@/data/products.json";
import { useProductStore } from "./stores/ProductStore";
import { storeToRefs } from "pinia";
// const productStore=useProductStore();
const {products} = storeToRefs(useProductStore())
import {useCartStore} from "@/stores/CartStore.js";
const productStore=useProductStore();
const cartStore=useCartStore();
productStore.fill()
</script>

<template>
  <div class="container">
    <TheHeader />
    <ul class="sm:flex flex-wrap lg:flex-nowrap gap-5">
      <ProductCard
        v-for="product in productStore.products"
        :key="product.name"
        :product="product"
        @addToCart="cartStore.items.push(product)"
      />
    </ul>
  </div>
</template>
