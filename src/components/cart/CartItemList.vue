<template>
  <section class="flex flex-col sm:flex-row">
    <div class="m-6 sm:my-6 sm:mx-4">
      <h1 class="text-2xl mb-6">Item</h1>
      <div
        v-for="product in cartProductList"
        :key="product.id"
        class="flex items-start px-4 my-8 sm:my-16"
      >
        <img
          :src="product.image"
          :alt="product.title"
          class="w-[100px] sm:w-[160px] pr-4 sm:pr-8"
        />
        <div>
          <h5 class="mb-6">{{ product.title }}</h5>
          <h5>Qty: {{ product.quantity }}</h5>
          <h5>Price: {{ product.quantity * product.price }}</h5>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import type { ProductProps } from "../collection/CollectionList.vue";

export interface CartProductProps {
  productId: number;
  quantity: number;
}

export interface CartProductListProps extends ProductProps {
  quantity: number;
}

const cartProductList: CartProductListProps[] = [];
const { products } = defineProps<{ products: CartProductProps[] }>();
for (let product of products) {
  const data = await fetch(
    `https://fakestoreapi.com/products/${product.productId}`
  ).then((res) => res.json());
  cartProductList.push({ ...data, quantity: product.quantity });
}
console.log(cartProductList);
</script>
