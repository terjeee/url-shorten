<script setup lang="ts">
  import MaxWidth from "@/components/ux/MaxWidth.vue";
  import IconBrand from "@/components/ux/svg/IconBrand.vue";
  import IconRecords from "@/components/ux/svg/IconRecords.vue";
  import IconCustomizable from "@/components/ux/svg/IconCustomizable.vue";
</script>

<template>
  <section class="info">
    <MaxWidth>
      <div class="header">
        <h4>Advanced Statistics</h4>
        <p>Track how your links are performing across the web with our advanced statistics dashboard.</p>
      </div>
      <div class="cards">
        <article>
          <span class="circle">
            <IconBrand />
          </span>
          <div class="text">
            <h3>Brand Recognition</h3>
            <p>
              Boost your brand recognition with each click. Generic links don't mean a thing. Branded links help instil
              confidence in your content
            </p>
          </div>
        </article>
        <article>
          <span class="circle">
            <IconRecords />
          </span>
          <div class="text">
            <h3>Detailed Records</h3>
            <p>
              Gain insights into who is clicking your links. Knowing when and where people engage with your content helps
              inform better decisions.
            </p>
          </div>
        </article>
        <article>
          <span class="circle">
            <IconCustomizable />
          </span>
          <div class="text">
            <h3>Fully Customizable</h3>
            <p>
              Improve brand awareness and content discoverability through customizable links, supercharging audience
              engagement.
            </p>
          </div>
        </article>
      </div>
    </MaxWidth>
  </section>
</template>

<style scoped lang="scss">
  @use "@/assets/variables.scss";

  .info {
    padding: 8rem 0;
    background-color: variables.$clr-grey;

    .header {
      margin-bottom: 10rem;
      display: flex;
      flex-direction: column;
      gap: 1rem;
      text-align: center;

      h4 {
        font-size: 2.4rem;
      }
    }

    .cards {
      display: flex;
      flex-direction: column;
      gap: 8rem;
      text-align: center;

      article {
        padding: 0 3rem 4.5rem 3rem;
        background-color: #fff;
        border-radius: variables.$radius;

        .circle {
          display: inline-block;
          padding: 1.75rem;
          border-radius: 50%;
          background-color: variables.$clr-dark-blue;
          transform: translateY(-50%);

          svg {
            display: block;
          }
        }

        .text {
          margin-top: -2rem;
          display: flex;
          flex-direction: column;
          gap: 1rem;
        }
      }
    }
  }
</style>
