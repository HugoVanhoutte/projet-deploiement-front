<script setup>
import { ref } from 'vue';

const props = defineProps(['title', 'image', 'id']);
const isTitleFull = ref(false);

const copyLinkToClipBoard = () => {
  navigator.clipboard.writeText(`${window.location.origin}/ads/${props.id}`);
  // TODO: add "text copied" tooltip
};

const addAdToFavorites = () => {
  // TODO
};

const reportAd = () => {
  // TODO
};

const toggleTitle = () => {
  isTitleFull.value = !isTitleFull.value;
};

</script>

<template>
  <section class="ad">
    <main class="image">
      <div
        class="overlay"
        @mouseenter="toggleTitle"
        @focusin="toggleTitle"
        @mouseleave="toggleTitle"
        @focusout="toggleTitle"
      >
        <h1 :class="isTitleFull ? 'big' : 'small' ">{{ props.title }}</h1>
      </div>
    </main>
    <aside>
      <div class="buttons">
        <button class="material-symbols-outlined share" @click="copyLinkToClipBoard">
          share
        </button>
        <button class="material-symbols-outlined favorite" @click="addAdToFavorites">
          favorite
        </button>
        <button class="material-symbols-outlined report" @click="reportAd">
          report
        </button>
      </div>
    </aside>
  </section>
</template>

<style scoped lang="scss">
@import '@/assets/variables';
.ad {
  font-family: $body-font;
  display: flex;
  flex-direction: column;
  width: 45dvw;
  max-width: 25rem;
  min-width: 15rem;
  height: 15rem;
  box-shadow: $materialShadow;
  margin: 2dvw;
  transition: .3s;
  overflow: hidden;
  border-radius: .25em;
  @media (min-width: 1025px) {
    margin: 2dvw 0;
  }
  .image {
    display: flex;
    flex-direction: column;
    background-image: url('../assets/test.jpg');
    // background-image: v-bind('props.image');
    // TODO: gérer les images
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    object-fit: contain;
    height: 80%;
    width: 100%;
    justify-content: flex-end;
    align-items: flex-start;
    transition: .3s ease;
    .overlay {
      background-color: #00000075;
      width: 100%;
      height: 15%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      transition: .3s ease;
      h1 {
        color: white;
        padding: .5rem;
        max-width: 100%;
        word-break: break-word;
        font-size: 1.2rem;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
      }
    }
    .overlay:hover {
      height: 100%;
    }
    h1.small {
      overflow: clip;
      white-space: nowrap;
    }
    h1.big {
      overflow: hidden;
      white-space: wrap;
    };
    h1:first-letter {
      text-transform: uppercase;
    }
  }
  aside {
    display: flex;
    flex-direction: row;
    width: 100%;
    height: 20%;
    .buttons {
      width: 100%;
      display: flex;
      flex-direction: row;
      justify-content: flex-end;
      button {
        font-size: 2.25rem;
        border: none;
        background: none;
        cursor: pointer;
        transition: .5s ease;
        margin: 0 2dvw;
      }
      button:hover {
        transform: scale(1.1);
      }
      .share:hover {
        color: rgb(0, 0, 255);
      }
      .favorite:hover {
        color: rgb(255, 0, 128);
      }
      .report:hover {
        color: rgb(255, 0, 0);
      }
    }
  }
}
.ad:hover {
  transform: scale(1.05);
  box-shadow:  5px 5px 5px 2px #cccccc;
}
</style>
