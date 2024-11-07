<template>
  <div class="background">
  </div>
  <form @submit.prevent="handleSubmit">
    <div class="title">
      <h2>Bonjour !</h2>
      <p>Connectez-vous pour découvrir toutes nos fonctionnalités.</p>
    </div>

    <!-- Champ Email -->
      <label for="email">Email *
        <input type="email" id="email" v-model="email" required />
      </label>
    <!-- Champ Mot de passe -->
      <label for="password">Mot de passe *
      <input type="password" id="password" v-model="password" required />
    </label>
    <!-- Bouton de soumission -->
    <div class="button-submit">
      <button type="submit">Se connecter</button>
    </div>
    <div class="create-account">
      <p>Pas encore de compte ?
        <span><u>
          Créer un compte</u>
        </span>
      </p>
    </div>
  </form>
</template>

<script setup>

import { ref } from 'vue';

/* eslint-disable */
// Déclarer les variables pour stocker les valeurs des champs du formulaire
const email = ref('');
const password = ref('');

// Fonction de soumission du formulaire
// const handleSubmit = () => {
//   console.log('Email:', email.value);
//   console.log('Password:', password.value);

  // Logique de connexion ou validation des données à ajouter ici
// };
</script>

<style scoped lang="scss">
@import '../assets/variables.scss';

.background{
  background-image: url('../assets/loginbackground.jpg');
  height: 88vh;
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}
form {
  z-index: 0;
  position: absolute;
  opacity: 0.95;
  top:20%;
  left: 50%;
  transform: translate(-50%,0);
  max-width: 600px;
  margin: auto;
  padding: 1.5rem;
  background-color: #f9f9f9;
  border-radius: 0.25em;
  box-shadow: $materialShadow;
  font-family: $body-font;
  .title {
    display: flex;
    flex-direction: column;
    align-items: start;
    justify-content: center;
    margin: 0 auto;
    margin-bottom: 1.5rem;
    width: 80%;
  }
  h2 {
    margin-bottom: 0.5rem;
    text-align: center;
    font-size: 20px;
    font-weight: 500;
  }

  p {
    margin-bottom: 1.5rem;
    text-align: left;
    font-size: 16px;
  }

  label {
    display: flex;
    flex-direction: column;
    align-items: start;
    font-weight: 100;
    margin: 0 auto;
    margin-bottom: 1.5rem;
    width: 80%;
  }

  input[type="email"],
  input[type="password"] {
    width: 100%;
    padding: 0.5rem 0 0.5rem 0.5rem;
    margin: 0.5rem auto;
    border: 1px solid #ccc;
    border-radius: 0.25em;
    font-size: 1rem;
  }

  button[type="submit"] {
    width: 80%;
    padding: 0.7rem;
    font-size: 1rem;
    color: #fff;
    background-color: $logoColor;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
    margin: 1.5rem auto;
    margin-bottom: 1.5rem;
    &:hover {
      background-color: $burlywood;
    }
  }
  .button-submit {
    display: flex;
    justify-content: center;
  }
  .create-account p{
    text-align: center;
  }
  .create-account span {
    font-weight: 500;
  }
}
</style>
