<script setup>
const props = defineProps(['title', 'image', 'id']);

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
</script>

<template>
  <section class="ad">
    <main class="image">
      <h1>{{ props.title }}</h1>
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
  display: flex;
  flex-direction: column;
  width: 15rem;
  height: 15rem;
  box-shadow: 2px 2px 3px 1px #cccccc;
  margin: 1rem;
  transition: .3s;
  .image {
    display: flex;
    flex-direction: column;
    background-image: url('../assets/test.jpg');
    // background-image: v-bind('props.image');
    // TODO: gérer les images
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    height: 80%;
    width: 100%;
    justify-content: flex-end;
    align-items: flex-start;
    transition: .3s ease;
    h1 {
      margin: .5rem;
      background-color: #00000075;
      color: white;
      padding: .15rem;
      max-width: 100%;
      word-break: break-word;
      font-size: 1.3rem;
    }
    h1:first-letter {
      text-transform: uppercase;
    }
  }
  aside {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    width: 100%;
    height: 20%;
    .buttons {
      width: 45%;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      button {
        border: none;
        background: none;
        cursor: pointer;
        transition: .5s ease;
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
