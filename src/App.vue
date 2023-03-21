<script setup lang="ts">
  import Layout from "@/layout/Layout.vue";
  import Introduction from "./components/sections/Introduction.vue";
  import Application from "./components/sections/Application.vue";
  import Information from "./components/sections/Information.vue";
</script>

<template>
  <Layout>
    <Introduction />
    <Application />
    <Information />
  </Layout>
</template>

<style scoped lang="scss">
  @use "@/assets/variables.scss";

  .application {
    color: red;
  }
</style>
