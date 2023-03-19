<template>
  <nav>
    <Logo />
  </nav>
  <slot />
  <footer></footer>
</template>

<script setup lang="ts">
  import Logo from "@/components/svg/Logo.vue";
</script>
