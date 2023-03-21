<script setup lang="ts">
  import MaxWidth from "@/components/ux/MaxWidth.vue";
  import Logo from "@/components/ux/svg/Logo.vue";
  import IconFacebook from "@/components/ux/svg/IconFacebook.vue";
  import IconPinterest from "@/components/ux/svg/IconPinterest.vue";
  import IconTwitter from "@/components/ux/svg/IconTwitter.vue";
  import IconInstagram from "@/components/ux/svg/IconInstagram.vue";
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
      <div class="logo">
        <Logo fill="white" />
      </div>
      <section class="socials">
        <a href="https://www.facebook.com" target="_blank">
          <IconFacebook />
        </a>
        <a href="https://www.twitter.com" target="_blank">
          <IconTwitter />
        </a>
        <a href="https://www.pinterest.com" target="_blank">
          <IconPinterest />
        </a>
        <a href="https://www.instagram.com" target="_blank">
          <IconInstagram />
        </a>
      </section>
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
    background-color: variables.$clr-dark-blue;

    .logo {
      padding-bottom: 4rem;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .socials {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 2rem;
    }
  }
</style>
