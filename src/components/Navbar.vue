<template>
  <nav
    class="flex shadow-lg items-center justify-between sm:justify-start px-4 sm:px-8 py-4"
  >
    <a href="/"
      ><img src="/logo.png" alt="logo" class="w-20 sm:w-40 md:w-52 mx-8"
    /></a>
    <div class="hidden sm:flex sm:gap-8">
      <a
        href="/collections/new-arrival"
        class="border-b border-b-white hover:border-b-slate-900 hover:transition-all"
        >New Arrival</a
      >
      <a
        href="/collections/women"
        class="border-b border-b-white hover:border-b-slate-900 hover:transition-all"
        >Women</a
      >
      <a
        href="/collections/men"
        class="border-b border-b-white hover:border-b-slate-900 hover:transition-all"
        >Men</a
      >
      <a
        href="/about"
        class="border-b border-b-white hover:border-b-slate-900 hover:transition-all"
        >About</a
      >
    </div>
    <div>
      <i
        class="fa-solid fa-bars p-2 mx-4 sm:hidden"
        @click="isDropdown = !isDropdown"
      ></i>
    </div>
  </nav>
  <div
    class="absolute top-15 w-screen bg-white transition-opacity duration-1000 flex flex-col gap-5 px-8 py-4"
    v-show="isDropdown"
  >
    <a
      href="/collections/new-arrival"
      class="border-b border-b-white hover:border-b-slate-900 hover:transition-all"
      >New Arrival</a
    >
    <a
      href="/collections/women"
      class="border-b border-b-white hover:border-b-slate-900 hover:transition-all"
      >Women</a
    >
    <a
      href="/collections/men"
      class="border-b border-b-white hover:border-b-slate-900 hover:transition-all"
      >Men</a
    >
    <a
      href="/about"
      class="border-b border-b-white hover:border-b-slate-900 hover:transition-all"
      >About</a
    >
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const isDropdown = ref(false);
</script>
