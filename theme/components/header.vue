<script setup lang="ts">
import Logo from "./logo.vue";
</script>

<template>
  <header class="flex justify-end absolute top-0 left-0 right-0 py-10 px-14">
    <Logo :color="$slidev.nav.currentLayout === 'section' ? 'white' : 'blue'" />
  </header>
</template>
