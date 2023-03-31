<script setup lang="ts">
  import MaxWidth from "@/components/ux/MaxWidth.vue";
  import IllustrationWork from "@/components/ux/svg/IllustrationWork.vue";
</script>

<template>
  <div class="container">
    <MaxWidth>
      <header>
        <IllustrationWork />
        <div class="text">
          <h2>More than just shorter links</h2>
          <p>Build your brand's recognition and get detailed insights on how your links are performing.</p>
        </div>
      </header>
    </MaxWidth>
  </div>
</template>

<style scoped lang="scss">
  @use "@/assets/variables.scss";
  @use "@/assets/breakpoint.scss";

  header {
    display: flex;
    flex-direction: column;
    align-items: center;

    @include breakpoint.width(laptop) {
      padding: 4rem 0;
      flex-direction: row-reverse;
      margin-bottom: 5rem;
    }

    .text {
      padding: 4rem 0;
      text-align: center;

      @include breakpoint.width(laptop) {
        width: 80%;
        margin-right: auto;
        text-align: left;
      }

      h2 {
        font-size: 4rem;
        line-height: 1.2;

        @include breakpoint.width(laptop) {
          font-size: 4.75rem;
        }
      }

      p {
        padding-top: 1rem;
        padding-right: 4rem;
        font-size: variables.$font-size;
        line-height: 1.5;
      }
    }
  }
</style>
