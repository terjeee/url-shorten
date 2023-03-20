<script setup lang="ts">
  import MaxWidth from "@/components/UX/MaxWidth.vue";
  import Logo from "@/components/svg/Logo.vue";
  import IconFacebook from "@/components/svg/IconFacebook.vue";
  import IconTwitter from "@/components/svg/IconTwitter.vue";
  import IconInstagram from "@/components/svg/IconInstagram.vue";
</script>

<template>
  <nav class="nav">
    <MaxWidth>
      <Logo fill="hsl(255, 11%, 22%)" />
    </MaxWidth>
  </nav>

  <slot></slot>

  <footer class="footer">
    <MaxWidth>
      <Logo fill="white" />
      <div>
        <IconInstagram />
        <IconTwitter />
      </div>
    </MaxWidth>
  </footer>
</template>

<style scoped lang="scss">
  @use "@/assets/variables.scss";

  .nav {
    padding: 2.5rem 0;
  }

  .footer {
    padding: 4rem 0;
    display: flex;
    justify-content: center;
    background-color: variables.$clr-dark-violet;
  }
</style>
