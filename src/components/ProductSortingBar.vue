<template>
  <section class="flex justify-around">
    <select v-model="sorted">
      <option disabled value="">Please select</option>
      <option value="asc">Ascending</option>
      <option value="desc">Descending</option>
    </select>
  </section>
</template>

<script setup lang="ts">
import { ref } from "vue";
const sorted = ref("");
</script>

<style lang="scss" scoped></style>
