<script lang="ts">
  import Logo from "./components/svg/Logo.vue";
  import IllustrationWork from "./components/svg/IllustrationWork.vue";
  import BgShortenDesktop from "./components/svg/BgShortenDesktop.vue";
  import BgShortenMobile from "./components/svg/BgShortenMobile.vue";
  import IconBrand from "./components/svg/IconBrand.vue";
  import IconCustomizable from "./components/svg/IconCustomizable.vue";
  import IconRecords from "./components/svg/IconRecords.vue";
  import IconFacebook from "./components/svg/conFacebook.vue";
  import IconInstagram from "./components/svg/IconInstagram.vue";
  import IconPinterest from "./components/svg/IconPinterest.vue";
  import IconTwitter from "./components/svg/IconTwitter.vue";

  export default {
    name: "App",
    components: {
      BgShortenDesktop,
      BgShortenMobile,
      IconBrand,
      IconCustomizable,
      IconFacebook,
      IconInstagram,
      IconPinterest,
      IconRecords,
      IconTwitter,
      IllustrationWork,
      Logo,
    },
  };
</script>

<template>
  <h1>hei</h1>
  <BgShortenDesktop />
  <BgShortenMobile />
  <IconBrand />
  <IconCustomizable />
  <IconFacebook />
  <IconInstagram />
  <IconPinterest />
  <IconRecords />
  <IconTwitter />
  <IllustrationWork />
  <Logo />
</template>

<style lang="scss"></style>
