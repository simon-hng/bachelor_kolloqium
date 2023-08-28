<script setup lang="ts">
import { computed } from "vue";

const props = defineProps({
  color: {
    default: "blue",
  },
});

const fill = computed(() => {
  const colors = {
    blue: "fill-[#3070b3]",
    white: "fill-[#FFFFFF]",
  };
  return colors[props.color];
});
</script>

<template>
  <svg
    class="h-8"
    :class="fill"
    :style="style"
    viewBox="-16.014 -31 408.16 212.46684"
  >
    <path
      d="m 140.54052,-31 v 173.32822 h 44.72985 V -31 H 392.146 V 181.46685 H 353.00738 V 8.138629 H 308.2775 V 181.46685 H 269.13887 V 8.138629 H 224.40902 V 181.46685 H 101.4019 V 8.138629 H 62.26327 V 181.46685 H 23.12462 V 8.138629 H -16.014 V -31 Z"
      id="path6"
      style="stroke-width: 5.59123"
    />
  </svg>
</template>
