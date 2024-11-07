<script setup>

import CallToActionButton from '@/components/CallToActionButton.vue';
import CardComponent from '@/components/CardComponent.vue';
import HacheDeux from '@/components/HacheDeux.vue';
</script>

<template>
  <div>
    <CallToActionButton/>
    <HacheDeux title="Top Annonces"/>
  </div>
</template>

<style scoped lang="scss">
div {
  max-width: 1280px;
  margin: 0 auto;
}
</style>
