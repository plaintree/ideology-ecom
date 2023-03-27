<template>
  <section class="flex justify-around mt-4">
    <select
      v-model="sortBy"
      @change="$emit('sortBy', sortBy)"
      class="p-2 outline-none border-b border-b-white hover:border-b-black"
    >
      <option disabled value="">Sort</option>
      <option value="asc">Ascending</option>
      <option value="desc">Descending</option>
    </select>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";

const sortBy = ref("");
</script>

<style lang="scss" scoped></style>
