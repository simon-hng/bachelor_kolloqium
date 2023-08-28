<script setup lang="ts">
import Logo from "./shared/logo.vue";
</script>

<template>
  <div class="slidev-layout section w-full h-full grid bg-[#0065bd] text-white">
    <header class="absolute w-full slidev-layout flex justify-end">
      <Logo color="white" />
    </header>
    <div class="my-auto text-center">
      <slot />
    </div>
  </div>
</template>
