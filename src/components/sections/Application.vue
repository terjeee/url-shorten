<script setup lang="ts">
  import { ref } from "vue";
  import MaxWidth from "@/components/ux/MaxWidth.vue";

  let links: string[] = [];
  let input = ref("");

  function getShortenedUrl() {
    console.log(input);

    // fetch()
    // handle response
    // push response til linnks[]

    // input = ":)";
    $refs.input.reset();
  }
</script>

<template>
  <MaxWidth>
    <section class="application">
      <form action="">
        <input id="id" type="text" v-model="input" placeholder="Shorten link here.." />
        <button @click.prevent="getShortenedUrl">Shorten!</button>
      </form>
      <!-- <ul>
        <li></li>
      </ul> -->
    </section>
  </MaxWidth>
</template>

<style scoped lang="scss">
  @use "@//assets/variables.scss";

  .application {
    margin-top: 2rem;
    margin-bottom: 6rem;

    form {
      padding: 2.5rem 2rem;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 1.5rem;
      border-radius: variables.$radius;
      background-color: variables.$clr-violet;
      background-image: url(@/components/ux/svg/BgShortenMobile.svg);
      background-position: top right;
      background-repeat: no-repeat;
      background-size: fill;

      input {
        padding: 1.35rem;
        outline: transparent;
        font-size: 1.5rem;
        font-weight: 400;
        color: variables.$clr-grey-violet;
        letter-spacing: 1.05px;
        border-radius: variables.$radius-btn;
        border: transparent;
      }

      button {
        padding: 1.25rem;
        font-size: variables.$font-size;
        font-weight: 700;
        color: #fff;
        letter-spacing: 1.05px;
        background-color: variables.$clr-cyan;
        border-radius: variables.$radius-btn;
        border: transparent;
      }
    }
  }
</style>
