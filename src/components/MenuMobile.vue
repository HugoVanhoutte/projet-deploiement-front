<script setup>

</script>

<template>
  <nav>
    <ul>
      <li v-for="n in 10" :key="n"><router-link to="/">Test</router-link></li>
    </ul>
    <button class="overlay" @click="$emit('toggleMenu')"/>
  </nav>
</template>

<style scoped lang="scss">
@import '@/assets/variables';
  nav {
    display: flex;
    flex-direction: row;
    position: fixed;
    height: 100%;
    width: 100%;
    ul {
      width: 80%;
      height: 100%;
      background-color: $cornsilk;
      padding-top: 2rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      li {
        padding: .5rem;
        font-family: $body-font;
        a {
          text-decoration: none;
          color: inherit;
        }
      }
    }
    .overlay {
      border: none;
      width: 20%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
    }
  }
</style>
