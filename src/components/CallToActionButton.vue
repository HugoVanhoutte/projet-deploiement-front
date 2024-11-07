<template>
    <div class="container-cta" :style="{ backgroundColor: props.backgroundColor }">
        <div class="container-text">{{ props.title }}</div>
        <div class="container-button"><button>
            <span class="material-symbols-outlined">
                add_circle</span>{{ props.name }}
            </button>
            </div>
    </div>
</template>
<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  title: {
    type: String,
    default: 'Titre du Call',
  },
  name: {
    type: String,
    default: 'Nom du bouton',
  },
  backgroundColor: {
    type: String,
    default: '$cornsilk',
  },
});

</script>
<style scoped lang="scss">
@import '../assets/variables.scss';

.container-cta {
    margin: 2.5rem 2dvw;
    background-color: #DEB887;
    height: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    padding: 1rem;
    gap: 0.5rem;
    border-radius: 0.25em;
    box-shadow: 2px 2px 3px 1px #cccccc;
    letter-spacing: -0.1px;

    @media (min-width: 769px) {
        flex-direction: row;
        justify-content:space-evenly;
    }

    @media (min-width: 1025px) {
        flex-direction: row;
        justify-content:center;
        gap: 15rem;
        max-width: 1280px;
        margin: 2.5rem auto;
    }

    .container-text {
        font-family: $body-font;
        font-weight: 500;
        font-size: 18px;
        padding: 0.8rem;
    }

    .container-button{
        padding: 0.8rem;
        background-color: $cornsilk;
        border-radius: 0.25em;
        transition: .5s ease;
    }
    .container-button:hover {
        transform: scale(1.1);
        box-shadow: $materialShadow;
    }
    button {
        border: none;
        background-color: transparent;
        display: inline-flex;
        align-items: center;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI',
        Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        font-size: 16px;
        gap: 0.8rem;
        font-weight: 400;
        cursor: pointer;
    }
}
</style>
