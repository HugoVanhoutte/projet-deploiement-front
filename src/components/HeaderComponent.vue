<script setup>

</script>

<template>
<header>
  <button class="material-symbols-outlined menu">menu</button>
  <button class="logo"></button>
  <button class="material-symbols-outlined search">search</button>
</header>
</template>

<style scoped lang="scss">
header {
  display: flex;
  flex-direction: row;
  width: 100dvw;
  height: 10rem;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 3px 10px 2px #cccccc;
  margin-bottom: .5rem;
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
</style>
