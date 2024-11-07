<template>
  <div class="background">
  </div>
  <form @submit.prevent="handleSubmit">
    <div class="title">
      <h2>Bonjour !</h2>
      <p>Connectez-vous pour découvrir toutes nos fonctionnalités.</p>
    </div>
    <div class="name-container">
      <label for="name">Nom *
        <input type="text" id="name" v-model="formData.nom" required />
      </label>
      <label for="prenom">Prénom *
        <input type="text" id="prenom" v-model="formData.prenom" required />
      </label>
    </div>

    <!-- Champ Username-->
    <label for="username">Nom d'utilisateur
      <input type="text" id="username" v-model="formData.username" />
      <span v-if="errors.username">{{ errors.username }}</span>
    </label>
    <!-- Champ Numero de telephone -->
    <label for="phone">Téléphone
      <input type="text" id="phone" v-model="formData.phone" />
      <span v-if="errors.phone">{{ errors.phone }}</span>
    </label>
    <!-- Champ Email -->
    <label for="email">Email *
      <input type="email" id="email" v-model="formData.email" required />
      <span v-if="errors.email">{{ errors.email }}</span>
    </label>
    <!-- Champ Mot de passe -->
     <div class="labelpassword">
      <label for="password">Mot de passe *
        <div class="" style="position: relative; width: 100%;">
          <input :type="show[0] ? 'text' : 'password'" id="confirmPassword"
          v-model="formData.password" required>
          <div>
            <span
            @click="isShowed(0)"
            @keydown.enter="isShowed(0)"
            class="material-symbols-outlined icon"
          >
            {{ show[0] ? 'visibility_off' : 'visibility' }}
          </span>
          </div>
        </div>
        <span v-if="errors.password">{{ errors.password }}</span>
      </label>
     </div>
     <div class="labelpassword">
       <!-- Champ Confirmer le mot de passe -->
       <label for="confirmPassword">Confirmer le mot de passe *
         <div class="" style="position: relative; width: 100%;">
           <input :type="show[1] ? 'text' : 'password'" id="confirmPassword"
           v-model="formData.confirmPassword" required>
           <div>
            <span
            @click="isShowed(1)"
            @keydown.enter="isShowed(1)"
            class="material-symbols-outlined icon"
          >
            {{ show[1] ? 'visibility_off' : 'visibility' }}
          </span>
          </div>
          </div>
          <span v-if="errors.confirmPassword">{{ errors.confirmPassword }}</span>
          </label>
      </div>
    <!-- Bouton de soumission -->
    <div class="button-submit">
      <button type="submit">Se connecter</button>
    </div>
    <div class="create-account">
      <p>Pas encore de compte ?
        <span><u>Créer un compte</u></span>
      </p>
    </div>
  </form>
</template>

<script setup>
import { ref } from 'vue';
import validator from 'validator';

const show = ref([false, false]);

const isShowed = (index) => {
  show.value[index] = !show.value[index];
};

// Données réactives pour le formulaire
const formData = ref({
  nom: '',
  prenom: '',
  username: '',
  phone: '',
  email: '',
  password: '',
  confirmPassword: '',
});

// Objet pour stocker les erreurs
const errors = ref({
  phone: '',
  email: '',
  username: '',
  password: '',
  confirmPassword: '',
});

// Fonction de soumission du formulaire avec validation
const handleSubmit = () => {
  // Réinitialiser les erreurs
  errors.value = {
    phone: '',
    email: '',
    password: '',
    confirmPassword: '',
  };

  // Valider le téléphone
  if (formData.value.phone && !validator.isMobilePhone(formData.value.phone, 'fr-FR')) {
    errors.value.phone = 'Le numéro de téléphone est invalide.';
  }

  // Valider l'email
  if (!validator.isEmail(formData.value.email)) {
    errors.value.email = "L'email est invalide.";
  }

  // Vérifier que les mots de passe correspondent
  if (formData.value.password !== formData.value.confirmPassword) {
    errors.value.confirmPassword = 'Les mots de passe ne correspondent pas.';
  }

  // Valider le mot de passe avec des critères spécifiques
  if (!/[a-z]/.test(formData.value.password)) {
    errors.value.password = 'Le mot de passe doit contenir au moins 1 lettre minuscule.';
  } else if (!/[A-Z]/.test(formData.value.password)) {
    errors.value.password = 'Le mot de passe doit contenir au moins 1 lettre majuscule.';
  } else if (!/\d/.test(formData.value.password)) {
    errors.value.password = 'Le mot de passe doit contenir au moins 1 chiffre.';
  } else if (!/[@$!%*?&]/.test(formData.value.password)) {
    errors.value.password = 'Le mot de passe doit contenir au moins 1 caractère spécial (@, $, !, %, *, ?, &).';
  } else if (formData.value.password.length < 12) {
    errors.value.password = 'Le mot de passe doit contenir au moins 12 caractères.';
  }

  // Si aucune erreur, soumettre le formulaire
  if (!errors.value.phone && !errors.value.email
  && !errors.value.password && !errors.value.confirmPassword) {
    // console.log('Données du formulaire:', formData.value);
    // Logique de connexion ou autre traitement
  } else {
    // un commentaire
  }
};
</script>

<style scoped lang="scss">
@import '../assets/variables.scss';

.background{
  background-image: url('../assets/subscribeBackGround.jpg');
  height: 88vh;
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}
form {
  z-index: 0;
  position: absolute;
  opacity: 0.92;
  top:10.5%;
  left: 50%;
  transform: translate(-50%,0);
  max-width: 600px;
  width: 80%;
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

  .name-container {
    display: flex;
    flex-direction: row;
    width: 80%;
    margin: 0 auto;
    gap: 1.5rem;
  }

  label {
    display: flex;
    flex-direction: column;
    align-items: start;
    font-weight: 400;
    margin: 0 auto;
    margin-bottom: 1.5rem;
    width: 80%;
  }

  .labelpassword {
    display: flex;
    flex-direction: row;
  }

  .icon {
    position: absolute;
    top: 28%;
    right: 0;
    cursor: pointer;
    color: black;
  }

  input[type="email"],
  input[type="password"],
  input[type="text"] {
    width: 100%;
    padding: 0.5rem 0 0.5rem 0.5rem;
    margin: 0.5rem auto;
    border: 1px solid #ccc;
    border-radius: 0.25em;
    font-size: 1rem;
    font-weight: 100;
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
    transition: transform 0.6s ease;
    &:hover {
      background-color: $burlywood;
      transform: scale(1.02);
    }
    &:active {
      transform: scale(0.95);
    }
  }

  .button-submit {
    display: flex;
    justify-content: center;
  }

  .create-account p {
    text-align: center;
  }

  .create-account span {
    font-weight: 500;
    color: #000;
  }

  span {
    color: #ff0000;
    font-weight: 400
  }
}

@media (max-width: 768px) {
  .background {
    background-size: cover;
  }
}
</style>
