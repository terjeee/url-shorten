<script setup lang="ts">
  import MaxWidth from "@/components/ux/MaxWidth.vue";
  import IllustrationWork from "@/components/ux/svg/IllustrationWork.vue";
</script>

<template>
  <header>
    <IllustrationWork />
    <MaxWidth>
      <div class="text">
        <h2>More than just shorter links</h2>
        <p>Build your brand's recognition and get detailed insights on how your links are performing.</p>
      </div>
    </MaxWidth>
  </header>
</template>

<style scoped lang="scss">
  @use "@/assets/variables.scss";
  @use "@/assets/breakpoint.scss";

  header {
    .text {
      padding: 4rem 0;
      text-align: center;

      h2 {
        font-size: 4rem;
        line-height: 1.2;
      }

      p {
        padding-top: 1.5rem;
        font-size: variables.$font-size;
      }
    }
  }

  @include breakpoint.width(laptop) {
    header {
      background-color: red;
    }
  }
</style>
