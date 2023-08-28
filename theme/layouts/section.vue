<script setup lang="ts">
import Header from "./shared/header.vue";
</script>

<template>
  <div class="slidev-layout section w-full h-full grid bg-[#0065bd] text-white">
    <header class="absolute w-full slidev-layout flex justify-end">
      <img class="h-8" src="assets/tum_logo.png" />
    </header>
    <div class="my-auto text-center">
      <slot />
    </div>
  </div>
</template>
