<template>
    <div  class="card-container">
        <div v-for="(card, key) in categorie"
            :key="key"
            :style="`background-image:url('${card.image}')`"
            class="card">
            <p>{{ card.name }}</p>
        </div>
    </div>
</template>
<script setup>
import { ref } from 'vue';

const categorie = ref({
  meubles: {
    name: 'Meubles',
    image: 'https://www.atmosphera.com/img/home/9/1_1_b57112cb84a86eee66d49853324d2c6d.1686061227.jpeg',
  },
  luminaires: {
    name: 'Luminaires',
    image: 'https://www.atmosphera.com/img/home/9/1_1_f0311753196a138bae8d711243b6dc67.1686061227.jpeg',
  },
  canape: {
    name: 'Canapé',
    image: 'https://www.atmosphera.com/img/home/9/1_1_c21f7423b24da559c733da0d07744fcf.1686061227.jpeg',
  },
  fauteuils: {
    name: 'Fauteuils',
    image: 'https://www.atmosphera.com/img/home/9/1_1_3067e314e238222163806773933eb466.1686061227.jpeg',
  },
  tables: {
    name: 'Tables',
    image: 'https://www.atmosphera.com/img/home/9/1_1_3aa9d45c5715d18844f7d0bd619cdfc2.1686061227.jpeg',
  },
  chaises: {
    name: 'Chaises',
    image: 'https://www.atmosphera.com/img/home/9/1_1_e545c820b6c200021ec7c71b8eba0c11.1686061227.jpeg',
  },
  decoration: {
    name: 'Décoration',
    image: 'https://www.atmosphera.com/img/home/9/1_1_8c3c12b696764bdaea8043025c4a386e.1686061227.jpeg',
  },
  enfant: {
    name: 'Enfant',
    image: 'https://www.atmosphera.com/img/home/9/1_1_47143ba74ff717c8d179e4aedd26aa63.1686061227.jpeg',
  },
});
</script>

  <style scoped lang="scss">
  @import '@/assets/variables';
  .card-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    margin: 0 auto;
    width: 70%;
    justify-content: center;
    gap: 0.5rem;
    cursor: pointer;

    .card {
      box-sizing: border-box;
      position: relative;
      width: 165px;
      height: 165px;
      text-align: center;
      background-position: center;
      background-size: 106%;
      transition: .3s;

      p {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        font-size: 24px;
        font-family: $body-font;
        font-weight: 400;
        color: #fff;
        padding: 0.2rem 0.5rem;
      }
    }
    .card:hover {
        background-size: 120%;
        width: 165px;
        height: 165px;
    }
  }

  @media (max-width: 1025px) {
    .card-container{
        width: 100%;
    }
  }

</style>
