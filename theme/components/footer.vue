<template>
  <footer
    class="absolute bottom-0 left-0 right-0 text-sm px-14 py-2 duration-500"
    :class="$slidev.nav.currentLayout === 'section' && 'color-white'"
  >
    <div class="flex justify-between">
      <p>
        {{ $slidev.configs.author }} | {{ $slidev.configs.title }} | 01/09/2023
      </p>
      <SlideCurrentNo />
    </div>
  </footer>
</template>
