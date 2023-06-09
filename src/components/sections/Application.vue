<script setup lang="ts">
  import { onBeforeMount } from "vue";
  import MaxWidth from "@/components/ux/MaxWidth.vue";

  import type { ReactiveVariable } from "@vue-macros/reactivity-transform/macros";

  interface Link {
    id: number;
    original: string;
    short: string;
  }

  let links: ReactiveVariable<Link[]> = $ref([]);
  let input = $ref("");
  let inputValid = $ref(true);

  onBeforeMount(() => {
    const localData = localStorage.getItem("localLinks");
    if (localData) links = JSON.parse(localData);
  });

  const randomId = () => {
    return Math.floor(Math.random() * 100000) + 1;
  };

  const setLocalStorageItem = (key: string, data: any) => {
    localStorage.setItem(key, JSON.stringify(data));
  };

  function getShortenedUrl() {
    const regexUrl = /^(https?:\/\/)?[a-zA-Z0-9]+(\.[a-zA-Z0-9]+)*(\.[a-z]{2,})(:[0-9]+)?(\/.*)?$/;
    const inputUrl = input.replace(/https?:\/\//g, "").replace(/^www\./i, "");
    if (!regexUrl.test(inputUrl)) return (inputValid = false);
    if (links.length > 0) {
      const indexDuplicate = links.findIndex((el) => el.original.replace(/https?:\/\//g, "") === inputUrl);
      if (indexDuplicate >= 0) {
        const [linkRemoved] = links.splice(indexDuplicate, 1);
        links.unshift(linkRemoved);
        setLocalStorageItem("localLinks", links);
        input = "";
        inputValid = true;
        return;
      }
    }

    fetch(`https://api.shrtco.de/v2/shorten?url=${inputUrl}`)
      .then((response) => response.json())
      .then((data) => {
        if (!data.ok) throw new Error(data.error);
        const urlOriginal = data.result["original_link"];
        const urlShort = data.result["short_link"];
        links.unshift({ id: randomId(), original: urlOriginal.replace("http://", "https://"), short: urlShort });
        setLocalStorageItem("localLinks", links);
        input = "";
        inputValid = true;
      })
      .catch((error) => console.log(error));
  }

  function copyClipboardUrl(event: Event, url: string) {
    navigator.clipboard.writeText(url);
    (event.target as HTMLElement).innerText = "Copied!";
  }

  function deleteUrl(urlId: number) {
    const link = links.findIndex((el) => el.id === urlId);
    links.splice(link, 1);
    setLocalStorageItem("localLinks", links);
  }
</script>

<template>
  <MaxWidth px="800">
    <section class="application">
      <form action="">
        <div class="form-input">
          <input
            id="id"
            type="text"
            v-model="input"
            placeholder="Shorten link here.."
            autocomplete="off"
            :class="{ error: inputValid }"
          />
        </div>
        <button @click.prevent="getShortenedUrl">Shorten!</button>
      </form>
      <p v-if="!inputValid" style="color: black; padding-top: 1rem; font-size: 13px">⛔ Please enter a valid url.</p>
      <ul v-if="links.length > 0">
        <li v-for="url in links" :key="url.id">
          <div class="text">
            <p>{{ url.original }}</p>
            <p>{{ url.short }}</p>
          </div>
          <div class="btns">
            <button id="btn-copy" @click="copyClipboardUrl($event, url.short)">Copy</button>
            <button id="btn-delete" @click="deleteUrl(url.id)">❌</button>
          </div>
        </li>
      </ul>
    </section>
  </MaxWidth>
</template>

<style scoped lang="scss">
  @use "@/assets/variables.scss";
  @use "@/assets/breakpoint.scss";

  .application {
    margin-top: 2rem;
    margin-bottom: 4rem;

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

      @include breakpoint.width(laptop) {
        display: flex;
        flex-direction: row;
      }

      .form-input {
        display: flex;
        flex-direction: column;

        @include breakpoint.width(laptop) {
          width: 80%;
        }

        input {
          padding: 1.35rem;
          outline: transparent;
          font-size: 1.5rem;
          font-weight: 400;
          color: variables.$clr-grey-violet;
          letter-spacing: 1.05px;
          border-radius: variables.$radius-btn;
          border: transparent;

          &inputValid {
            border: 2px solid red;
          }
        }
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

        &:hover {
          background-color: hsl(180, 66%, 55%);
        }
      }
    }

    ul {
      margin: 1.5rem 0;
      display: flex;
      flex-direction: column;
      gap: 1.5rem;

      @include breakpoint.width(laptop) {
        margin: 2rem 0;
        gap: 2rem;
      }

      li {
        padding: 0.75rem 2rem;
        display: flex;
        justify-content: space-between;
        gap: 2.5rem;
        background-color: variables.$clr-grey;
        border-radius: variables.$radius-btn;

        .text {
          width: 100%;
          padding: 0.75rem 0;
          overflow-x: scroll;
          color: variables.$clr-cyan;

          @include breakpoint.width(laptop) {
            overflow-x: hidden;
          }

          p {
            font-size: 1.2rem;
            color: variables.$clr-dark-violet;

            @include breakpoint.width(laptop) {
              font-size: 1.4rem;
              word-wrap: normal;
            }
          }

          p:nth-child(2) {
            font-size: 1.6rem;
            color: variables.$clr-cyan;

            @include breakpoint.width(laptop) {
              font-size: 1.8rem;
            }
          }
        }

        .btns {
          display: flex;
          justify-content: center;
          align-items: center;
          gap: 1rem;

          button {
            font-size: 1.5rem;
            border-radius: variables.$radius-btn;
            border: transparent;
            cursor: pointer;

            @include breakpoint.width(laptop) {
              font-size: 1.7rem;
            }
          }

          #btn-copy {
            padding: 0.75rem 1.25rem;
            background-color: variables.$clr-cyan;
            font-weight: 700;
            color: #fff;

            &:hover {
              background-color: hsl(180, 66%, 55%);
            }
          }

          #btn-delete {
            background-color: transparent;
            transition: all ease-in-out;

            &:hover {
              transform: scale(1.25);
            }
          }
        }
      }
    }
  }
</style>
