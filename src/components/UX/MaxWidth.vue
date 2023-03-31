<script setup lang="ts">
  const width = defineProps({ px: { type: String, default: "960" } });
</script>

<template>
  <div class="max--width" :style="{ 'max-width': `${width.px}px` }">
    <slot></slot>
  </div>
</template>

<style scoped lang="scss">
  .max--width {
    padding: 0 2rem;
    margin: auto;
  }
</style>
