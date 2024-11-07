<script setup>
const props = defineProps({
  categoryTitle: {
    type: String,
    default: 'categorie',
  },
  subCategories: {
    type: Array,
    required: false,
  },
});
</script>

<template>
  <h3><router-link to="/">{{ props.categoryTitle }}</router-link></h3>
  <ul>
    <li
      v-for="subCategory in props.subCategories"
      :key="subCategory"
    >
      <router-link to="/">{{ subCategory }}</router-link>
    </li>
  </ul>
</template>

<style scoped lang="scss">
@import '@/assets/variables';
a {
  text-decoration: none;
  color: inherit;
  line-height: 1.2rem;
}
a:hover {
  text-decoration: underline;
}
h3 {
  padding-bottom: .75rem;
  padding-top: 1.25rem;
  font-size: 1.2rem;
  text-decoration: underline;
}
</style>
