<script setup>
</script>

<template>
  <main id="search-bar">
    <button
      class="close-button material-symbols-outlined"
      @click="$emit('toggleSearchBar')"
    >
      close
    </button>
    <div class="search-form">
      <h2>Que cherchez-vous ?</h2>
      <label for="category">
        <select name="category" id="category">
          <option value="test" selected>Toutes les catégories</option>
        </select>
      </label>
      <label for="location">
        <select name="location" id="location">
          <option value="test" selected>Toute la France</option>
        </select>
      </label>
      <button>
        Rechercher
      </button>
    </div>
  </main>
</template>

<style scoped lang="scss">
@import '@/assets/variables';
#search-bar {
  height: 100%;
  width: 100%;
  margin: 0;
  display: flex;
  position: fixed;
  background-color: $cornsilk;
  overflow: clip;
  justify-content: center;
  align-items: center;
  transition: 1s;
  z-index: 5;
  .close-button {
    position: absolute;
    top: .5rem;
    right: .5rem;
    font-size: 4rem;
    cursor: pointer;
    border: none;
    background: none;
  }
  .search-form {
    display: flex;
    flex-direction: column;
    height: 25rem;
    width: 15rem;
    align-items: center;
    justify-content: space-around;
    h2 {
      font-size: 1.5rem;
      font-family: $body-font;
    }
    label, button {
      width: 100%;
      font-family: $body-font;
      font-size: 1.2rem;
      select {
        width: 100%;
        padding: 1rem;
        text-align: center;
        cursor: pointer;
        border-radius: 0;
        border: none;
        background-color: $saddlebrown;
        color: $cornsilk;
        font-size: 1.2rem;
      }
    }
    button {
      padding: 1rem;
      text-align: center;
      cursor: pointer;
      border-radius: 0;
      border: none;
      background-color: $goldenrod;
      color: $cornsilk;
      transition: .3s;
    }
    button:hover {
      transform: scale(1.1)
    }
  }
}
</style>
