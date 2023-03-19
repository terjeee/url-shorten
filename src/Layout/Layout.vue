<script setup lang="ts">
  import Logo from "@/components/svg/Logo.vue";
  import IconBrand from "@/components/svg/IconBrand.vue";
  import IconInstagram from "@/components/svg/IconInstagram.vue";
  import IconTwitter from "@/components/svg/IconTwitter.vue";
</script>

<template>
  <nav class="nav">
    <Logo />
  </nav>
  <slot></slot>
  <footer class="footer">
    <Logo fill="white" />
    <div>
      <IconBrand />
      <IconInstagram />
      <IconTwitter />
    </div>
  </footer>
</template>

<style scoped lang="scss">
  @use "@/assets/variables.scss";

  .nav {
    padding: 1rem 0;
    width: 100%;
  }

  .footer {
    background-color: variables.$clr-dark-violet;
  }
</style>
