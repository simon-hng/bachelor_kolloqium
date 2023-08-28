<script setup lang="ts">
import { computed } from "vue";
import { handleBackground } from "../layoutHelper";
import Header from "./shared/header.vue";

const props = defineProps({
  background: {
    default: "",
  },
});

const style = computed(() => handleBackground(props.background, true));
</script>

<template>
  <div class="slidev-layout cover" :style="style">
    <header class="flex justify-end">
      <img class="h-8" src="assets/tum_logo.png" />
    </header>

    <div class="my-auto w-full">
      <slot />
    </div>
  </div>
</template>
