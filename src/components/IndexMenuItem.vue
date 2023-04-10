<template>
  <a
    class=""
    v-for="menu in listMenu"
    :key="menu.title"
    :href="`/collections/${menu.title}`"
  >
    <img
      :src="menu.image"
      :alt="menu.title"
      class="w-[150px] h-[200px] sm:h-[250px] sm:w-[200px] mb-4"
    />
    <h5 class="uppercase tracking-wider">{{ menu.title }}</h5>
  </a>
</template>

<script setup lang="ts">
import { ref } from "vue";
import clothing1 from "../images/potriait-clothing-1.jpeg";
import clothing2 from "../images/potriait-clothing-2.jpeg";
import clothing3 from "../images/potriait-clothing-3.jpeg";
import jewellery1 from "../images/potriait-jewellery-1.jpeg";
import shoe from "../images/potriait-shoe-1.jpeg";

const listMenu = ref([
  { title: "women", image: clothing1 },
  { title: "men", image: clothing2 },
  { title: "shirt", image: clothing3 },
  { title: "jewellery", image: jewellery1 },
  { title: "shoes", image: shoe },
]);
</script>
