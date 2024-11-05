<script setup>
import { ref } from 'vue';

const isMenuDisplayed = ref(false);

const toggleMenu = () => {
  isMenuDisplayed.value = !isMenuDisplayed.value;
};
</script>

<template>
<header>
  <div class="buttons">
    <button class="material-symbols-outlined menu" @click="toggleMenu">menu</button>
    <button class="logo"></button>
    <button class="material-symbols-outlined search">search</button>
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
