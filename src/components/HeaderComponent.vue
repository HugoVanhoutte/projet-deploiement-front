<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import SearchBar from '@/components/SearchBar.vue';

const router = useRouter();
const isMenuDisplayed = ref(false);
const isSearchBarDisplayed = ref(false);

const toggleSearchBar = () => {
  isSearchBarDisplayed.value = !isSearchBarDisplayed.value;
};

const toggleMenu = () => {
  isMenuDisplayed.value = !isMenuDisplayed.value;
};

// Transitions
const beforeEnter = (el) => {
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 0;
};

const enter = (el, done) => {
  // eslint-disable-next-line no-unused-expressions
  el.offsetHeight; // Trigger reflow
  // eslint-disable-next-line no-param-reassign
  el.style.transition = 'opacity .3s';
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 1;
  done();
};

const leave = (el, done) => {
  // eslint-disable-next-line no-param-reassign
  el.style.transition = 'opacity .3s';
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 0;
  done();
};
</script>

<template>
  <transition name="fade" @before-enter="beforeEnter" @enter="enter" @leave="leave">
    <Search-bar v-if='isSearchBarDisplayed' @toggleSearchBar="toggleSearchBar"/>
  </transition>
<header>
  <div class="buttons">
    <button class="material-symbols-outlined menu" @click="toggleMenu">menu</button>
    <button class="logo" @click="router.push('/')"></button>
    <button class="material-symbols-outlined search" @click="toggleSearchBar">search</button>
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
  width: 100%;
  height: fit-content;
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
      padding: 0;
      height: 5rem;
      width: 10rem;
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
/* CSS transitions */
.fade-enter-active, .fade-leave-active {
  transition: opacity .3s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
