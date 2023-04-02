<template>
  <section class="flex flex-col sm:flex-row sm:justify-center">
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
          <!-- <div class="my-4">
            <i
              class="fa-solid fa-plus p-2 cursor-pointer border border-slate-900 rounded-sm"
              @click="handleQuantityClick(product.id, product.quantity, 1)"
            ></i>
            <i
              class="fa-solid fa-minus p-2 cursor-pointer border border-slate-900 rounded-sm"
              @click="handleQuantityClick(product.id, product.quantity, -1)"
            ></i>
          </div> -->
          <h5>Price: {{ product.quantity * product.price }}</h5>
        </div>
      </div>
    </div>
    <div class="m-6 sm:my-6 sm:min-w-[400px]">
      <h1 class="text-2xl mb-6">Summary</h1>
      <div class="flex justify-between items-center">
        <h3>Subtotal</h3>
        <h3>GBP: 2,340</h3>
      </div>
      <div class="flex justify-between items-center">
        <h3>Shipping cost</h3>
        <h3>Calulate at next page</h3>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";
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
// const handleQuantityClick = async (
//   id: number,
//   qty: number,
//   n: number
// ): Promise<void> => {
//   const data = await fetch("https://fakestoreapi.com/carts/1", {
//     method: "PATCH",
//     body: JSON.stringify({
//       products: [{ productId: id, quantity: qty + n }],
//     }),
//   }).then((res) => res.json());
//   cartProductList.filter((p) => p.id !== id).push(data);
//   console.log(cartProductList);
// };
</script>
