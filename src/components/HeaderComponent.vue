<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import SearchBar from '@/components/SearchBar.vue';
import MenuMobile from '@/components/MenuMobile.vue';

const router = useRouter();
const isMenuDisplayed = ref(false);
const isSearchBarDisplayed = ref(false);

const toggleSearchBar = () => {
  isSearchBarDisplayed.value = !isSearchBarDisplayed.value;
  isMenuDisplayed.value = false;
};

const toggleMenu = () => {
  isMenuDisplayed.value = !isMenuDisplayed.value;
  isSearchBarDisplayed.value = false;
};

// Transitions
const beforeEnterFade = (el) => {
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 0;
};
const enterFade = (el, done) => {
  // eslint-disable-next-line no-unused-expressions
  el.offsetHeight; // Trigger reflow
  // eslint-disable-next-line no-param-reassign
  el.style.transition = 'opacity .3s';
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 1;
  done();
};
const leaveFade = (el, done) => {
  // eslint-disable-next-line no-param-reassign
  el.style.transition = 'opacity .3s';
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 0;
  el.addEventListener('transitionend', done);
};

const beforeEnterFadeSlow = (el) => {
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 0;
};
const enterFadeSlow = (el, done) => {
  // eslint-disable-next-line no-unused-expressions
  el.offsetHeight; // Trigger reflow
  // eslint-disable-next-line no-param-reassign
  el.style.transition = 'opacity .3s';
  // eslint-disable-next-line no-param-reassign
  el.style.transitionDelay = '.2s';
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 1;
  done();
};
const leaveFadeSlow = (el, done) => {
  // eslint-disable-next-line no-param-reassign
  el.style.transition = 'opacity .3s';
  // eslint-disable-next-line no-param-reassign
  el.style.transitionDelay = '.1s';
  // eslint-disable-next-line no-param-reassign
  el.style.opacity = 0;
  el.addEventListener('transitionend', done);
};

const beforeEnterSlide = (el) => {
  // eslint-disable-next-line no-param-reassign
  el.style.transform = 'translateX(-100%)';
};
const enterSlide = (el, done) => {
  // eslint-disable-next-line no-unused-expressions
  el.offsetHeight; // Trigger reflow
  // eslint-disable-next-line no-param-reassign
  el.style.transition = 'transform .3s';
  // eslint-disable-next-line no-param-reassign
  el.style.transform = 'translateX(0)';
  done();
};
const leaveSlide = (el, done) => {
  // eslint-disable-next-line no-param-reassign
  el.style.transition = 'transform .3s';
  // eslint-disable-next-line no-param-reassign
  el.style.transform = 'translateX(-100%)';
  el.addEventListener('transitionend', done);
};
</script>

<template>
  <transition name="fade" @before-enter="beforeEnterFade" @enter="enterFade" @leave="leaveFade">
    <Search-bar v-if='isSearchBarDisplayed' @toggleSearchBar="toggleSearchBar"/>
  </transition>
  <transition name="slide" @before-enter="beforeEnterSlide" @enter="enterSlide" @leave="leaveSlide">
    <MenuMobile v-if="isMenuDisplayed" @toggleMenu="toggleMenu"/>
  </transition>
  <transition
    name="fade_slow"
    @before-enter="beforeEnterFadeSlow"
    @enter="enterFadeSlow"
    @leave="leaveFadeSlow"
  >
    <button class="overlay" v-if="isMenuDisplayed" @click="isMenuDisplayed = false"/>
  </transition>
<header>
  <div class="buttons">
    <button class="material-symbols-outlined menu" @click="toggleMenu">menu</button>
    <button class="logo" @click="router.push('/')"></button>
    <button class="material-symbols-outlined search" @click="toggleSearchBar">search</button>
  </div>
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
    transform: translateX(-100%);
  }
}
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  border: none;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}
/* CSS transitions */
.fade-enter-active, .fade-leave-active {
  transition: opacity .3s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.slide-enter-active, .slide-leave-active {
  transition: transform .3s;
}

.slide-enter, .slide-leave-to {
  transform: translateX(0);
}
.fade_slow-enter-active, .fade_slow-leave-active {
  transition: opacity .3s;
}
.fade_slow-enter, .fade_slow-leave-to {
  opacity: 0;
}
</style>
