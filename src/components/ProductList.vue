<template>
  <ProductSortingBar />
  <section class="flex gap-3 flex-wrap">
    <div
      class="flex flex-col justify-center items-center w-[200px] h-[200px] sm:w-[300px] sm:h-[300px] shadow-md p-8"
      v-for="product in props.products"
      :key="product.id"
    >
      <img :src="product.image" alt="" class="w-[175px] h-5/6" />
      <h5>{{ product.title }}</h5>
      <h5>${{ product.price }}</h5>
    </div>
  </section>
</template>

<script setup lang="ts">
import ProductSortingBar from "./ProductSortingBar.vue";

export interface IProps {
  products: {
    id: number;
    title: string;
    price: number;
    description: string;
    category: string;
    image: string;
    rating?: Object;
  }[];
}

const props = defineProps<IProps>();
</script>

<style lang="scss" scoped></style>
