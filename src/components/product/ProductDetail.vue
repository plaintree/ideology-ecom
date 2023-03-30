<template>
  <section
    class="flex flex-col sm:flex-row justify-center sm:justify-between m-4 sm:m-16"
  >
    <img
      :src="product.image"
      :alt="product.title"
      class="mb-4 sm:w-[500px] sm:mx-10 my-5 sm:my-0"
    />
    <div class="flex flex-col sm:px-8">
      <h5 class="text-lg mb-2">{{ product.title }}</h5>
      <h5 class="mb-2">${{ product.price }}</h5>
      <p class="text-sm tracking-normal leading-5">{{ product.description }}</p>
      <button
        class="px-6 sm:px-4 py-2 my-4 max-w-sm rounded-none bg-black hover:bg-white border border-black text-white hover:text-black transition duration-300"
      >
        Add to Bag
      </button>
    </div>
  </section>
</template>

<script setup lang="ts">
import type { ProductProps } from "../collection/CollectionList.vue";

const { product } = defineProps<{ product: ProductProps }>();
</script>
