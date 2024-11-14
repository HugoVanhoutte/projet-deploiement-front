<script setup>
import AdminMenu from '@/components/AdminMenu.vue';
import UsersList from '@/components/UsersList.vue';
import { ref } from 'vue';
import AdsList from '@/components/AdsList.vue';

const selected = ref('users');

const changeSelected = (value) => {
  selected.value = value;
};
</script>

<template>
  <admin-menu @change-selected='changeSelected'/>
  <users-list v-if="selected === 'users'"/>
  <ads-list v-if="selected === 'ads'"/>
</template>

<style scoped lang="scss">

</style>
