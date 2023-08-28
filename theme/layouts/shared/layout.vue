<script setup lang="ts">
import Header from "./header.vue";
</script>

<template>
  <div class="slidev-layout" :class="class">
    <Header />
    <slot />
    <footer class="absolute bottom-0 left-0">
      <p class="text-sm mx-14">
        Simon Huang, Lucas Welscher | Learning Analytics of Grading Programming
        Exercises | 01/09/2023
      </p>
      <p>{{ $slidev.nav.currentPage.value }}</p>
    </footer>
  </div>
</template>
