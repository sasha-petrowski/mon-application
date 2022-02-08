<template>
  <form class="Formulaire">
    <span>Nom</span>
    <input v-model="nom" placeholder="Nom">
    <span>Prénom</span>
    <input v-model="prenom" placeholder="Prénom">
    <span>Date de naissance</span>
    <input type="date" v-model="date">
    <span>Adresse mail</span>
    <input v-model="mail" placeholder="Jeanfrancois@gmail.com">
    
    <button value = "submit">Envoyer</button>
  </form>

  <div class = "confirmation">
      
  </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  data: () => {
      nom = "",
      prenom = "",
      date = "",
      mail = ""
  },
  computed: {
      
  }  

})
</script>