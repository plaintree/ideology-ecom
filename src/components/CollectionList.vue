<template>
  <ProductSortingBar v-show="!isEmpty && !isLoading" @sort-by="handleSorting" />
  <section
    class="flex flex-col sm:flex-row gap-3 flex-wrap justify-start items-center sm:items-start m-4 sm:m-16"
    v-show="!isEmpty && !isLoading"
  >
    <a
      class="flex flex-col justify-center items-start w-[350px] h-[350px] sm:w-[400px] sm:h-[400px] shadow-md p-8"
      v-for="product in products"
      :key="product.id"
      :href="`/products/${product.id}`"
    >
      <img
        :src="product.image"
        alt=""
        class="w-[175px] sm:w-[200px] h-5/6 self-center mb-4"
      />
      <h5 class="text-sm sm:text-md mb-2">{{ product.title }}</h5>
      <h5 class="mb-2">${{ product.price }}</h5>
    </a>
  </section>
  <section v-show="isEmpty && !isLoading" class="h-[50vh]">
    <h1 class="text-center text-3xl font-bold">Coming out soon</h1>
  </section>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";
import ProductSortingBar from "./CollectionSortingBar.vue";

export interface ProductProps {
  id: number;
  title: string;
  price: number;
  description: string;
  category: string;
  image: string;
  rating?: Object;
}
export interface CategoryProps {
  category: string | undefined;
}

const { category } = defineProps<CategoryProps>();
const products = ref<ProductProps[]>([]);
const isEmpty = ref(true);
const isLoading = ref(false);

onMounted(async () => {
  isLoading.value = true;
  const res = await fetch(
    `https://fakestoreapi.com/products/category/${category}`
  );
  const data = await res.json();
  if (data.length === 0) {
    isEmpty.value = true;
    isLoading.value = false;
  } else {
    products.value = data;
    isEmpty.value = false;
    isLoading.value = false;
  }
});

const handleSorting = async (s: string) => {
  isLoading.value = true;
  const res = await fetch(
    `https://fakestoreapi.com/products/category/${category}?sort=${s}`
  );
  products.value = await res.json();
  isLoading.value = false;
};
</script>

<style lang="scss" scoped></style>
