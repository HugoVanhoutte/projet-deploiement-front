<template>
    <h2>{{ props.title }}</h2>
  </template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  title: {
    type: String,
    default: 'Subtitle',
  },
});
</script>

<style scoped>
h2 {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  /* Même marge à gauche que la Card */
  margin: 2rem 0 2rem 2dvw;
  font-weight: 500;
    font-size: 20px;

    @media (min-width: 1025px) {
        margin-left: 0; /* Même marge à gauche que la Card */
    }
  }
  </style>
