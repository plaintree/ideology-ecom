<template>
  <a class="link-card" href="#">
    <img
      :src="image"
      :alt="title"
      class="w-[150px] h-[200px] sm:h-[250px] sm:w-[200px] mb-4"
    />
    <h5 class="uppercase tracking-wider">{{ title }}</h5>
  </a>
</template>

<script setup lang="ts">
export interface Props {
  title?: string;
  image: string;
}

const { title, image } = defineProps(["title", "image"]);
</script>
