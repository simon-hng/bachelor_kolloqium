<!--
  Usage:

```md
---
layout: two-cols
---

# Left

This shows on the left

::right::

# Right

This shows on the right
```

-->

<script setup lang="ts">
import Layout from "./shared/layout.vue";
const props = defineProps({
  class: {
    type: String,
  },
  layoutClass: {
    type: String,
  },
});
</script>

<template>
  <Layout class="w-full h-full">
    <div class="grid grid-cols-2" :class="props.layoutClass">
      <div class="col-left" :class="props.class">
        <slot />
      </div>
      <div class="col-right" :class="props.class">
        <slot name="right" />
      </div>
    </div>
  </Layout>
</template>
