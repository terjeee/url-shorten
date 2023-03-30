<script setup lang="ts" />

<template>
  <div class="max--width">
    <slot></slot>
  </div>
</template>

<style scoped lang="scss">
  .max--width {
    padding: 0 2rem;
    margin: auto;
    max-width: 960px;
  }
</style>
