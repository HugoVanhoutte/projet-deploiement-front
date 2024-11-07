<script setup>

import CategoriesList from '@/components/CategoriesList.vue';
</script>

<template>
  <footer>
    <div>
      <h1>La Meublerie</h1>
      <categories-list
        v-for="n in 10"
        :key="n"
        categoryTitle="test"
        :subCategories="['tes1', 'tes2', 'tes3']"
      />
    </div>
    <div>
      <h1>Informations</h1>
      <ul>
        <li><router-link to="/">Conditions d'utilisations</router-link></li>
        <li><router-link to="/">Politique de confidentialité</router-link></li>
        <li><router-link to="/">Informations légales</router-link></li>
      </ul>
    </div>
  </footer>
</template>

<style scoped lang="scss">
@import '@/assets/variables';
footer {
  width: 100%;
  background-color: $darkmaroon;
  color: $cornsilk;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  font-family: $body-font;
  div {
    display: flex;
    flex-direction: column;
    h1 {
      font-size: 1.5rem;
      font-weight: 500;
      padding: 1rem 0;
    }
    ul {
      li {
        padding: .25rem;
        a {
          color: inherit;
          text-decoration: none;
          i {
            font-size: 2rem;
          }
        }
        a:hover {
          text-decoration: underline;
        }
      }
    }
  }
}
</style>
