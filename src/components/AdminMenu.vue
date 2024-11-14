<script setup>

</script>

<template>
  <nav>
    <button @click="$emit('changeSelected', 'users')">Utilisateurs</button>
    <button @click="$emit('changeSelected', 'ads')">Annonces</button>
  </nav>
</template>

<style scoped lang="scss">
@import '@/assets/variables';
  nav {
    width: 100%;
    height: 50px;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    button {
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      border: 1px solid $brown;
      background-color: $blanchedalmond;
      cursor: pointer;
      font-size: 2rem;
      font-family: $body-font;
    }
  }
</style>
