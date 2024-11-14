<script setup>

</script>

<template>
  <nav>
    <ul>
      <li v-for="n in 10" :key="n"><router-link to="/">Test</router-link></li>
    </ul>
<!--    <button class="overlay" @click="$emit('toggleMenu')"/>-->
  </nav>
</template>

<style scoped lang="scss">
@import '@/assets/variables';
  nav {
    display: flex;
    flex-direction: row;
    position: fixed;
    height: 100%;
    width: 80%;
    z-index: 10;
    ul {
      width: 100%;
      height: 100%;
      background-color: $cornsilk;
      padding-top: 2rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      z-index: 20;
      li {
        padding: .5rem;
        font-family: $body-font;
        a {
          text-decoration: none;
          color: inherit;
        }
        a:hover {
          text-decoration: underline;
        }
      }
    }
    .overlay {
      position: absolute;
      border: none;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
    }
  }
</style>
