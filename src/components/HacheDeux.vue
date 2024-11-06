<template>
    <h2>{{ props.title }}</h2>
  </template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  title: {
    type: String,
    required: true,
    default: 'Subtitle',
  },
});
</script>

<style scoped>
h2 {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    margin: 2rem 0;
    margin-left: 2dvw; /* Même marge à gauche que la Card */
    font-weight: 500;
    font-size: 20px
  }
  </style>
