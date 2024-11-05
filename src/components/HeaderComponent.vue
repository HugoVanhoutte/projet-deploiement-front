<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const isMenuDisplayed = ref(false);
const isSearchBarDisplayed = ref(false);

const toggleSearchBar = () => {
  isSearchBarDisplayed.value = !isSearchBarDisplayed.value;
};

const toggleMenu = () => {
  isMenuDisplayed.value = !isMenuDisplayed.value;
};
</script>

<template>
<header>
  <div class="buttons">
    <button class="material-symbols-outlined menu" @click="toggleMenu">menu</button>
    <button class="logo" @click="router.push('/')"></button>
    <button class="material-symbols-outlined search" @click="toggleSearchBar">search</button>
  </div>
  <div class="search-bar" v-if="isSearchBarDisplayed">
    <label for="search-bar">
      <input id="search-bar" type="text">
      <span class="material-symbols-outlined">search</span>
    </label>
  </div>
  <nav v-if="isMenuDisplayed">
    <ul>
      <li>Test</li>
      <li>Test</li>
      <li>Test</li>
      <li>Test</li>
      <li>Test</li>
      <li>Test</li>
    </ul>
  </nav>
</header>
</template>

<style scoped lang="scss">
@import '@/assets/variables';
header {
  width: 100dvw;
  height: auto;
  box-shadow: 0 3px 10px 2px #cccccc;
  margin-bottom: .5rem;
  .buttons {
    justify-content: space-between;
    align-items: center;
    display: flex;
    flex-direction: row;
    height: 100%;
    button {
      border: none;
      background: none;
      cursor: pointer;
      font-size: 3rem;
      padding: 1rem;
    }
    .logo {
      width: 60%;
      height: 100%;
      background-image: url("@/assets/color-transparent.png");
      background-repeat: no-repeat;
      background-position: center center;
      background-size: contain;
    }
  }
  .search-bar {
    width: 100%;
    display: flex;
    justify-content: center;
    label {
      display: flex;
      flex-direction: row;
      align-items: center;
      span {
        cursor: pointer;
      }
    }
  }
  nav {
    text-align: center;
    ul {
      li {
        height: 1.2rem;
        font-family: $body-font;
      }
    }
  }
}
</style>
