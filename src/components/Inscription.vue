<template>
    <form v-if="isFormActive" class="formulaire">
        <span>Nom</span>
        <input v-model="nom" placeholder="Nom" />

        <span>Prénom</span>
        <input v-model="prenom" placeholder="Prénom" />

        <span>Date de naissance</span>
        <input type="date" v-model="date" />

        <span>Adresse mail</span>
        <input v-model="mail" placeholder="Jeanfrancois@gmail.com" />

        <button v-on:click="sendForm" type="button">Envoyer</button>
    </form>

    <div v-else="isFormActive" class="message">Félicitations, vous êtes inscrits</div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    data: () => {
        return {
            nom: '',
            prenom: '',
            date: new Date(),
            mail: '',
            isFormActive: true,
        }

    },
    methods: {
        sendForm(){
            if(this.nom && this.prenom && this.date && this.mail){
                this.isFormActive = false;
            }
        }
    }
})
</script>

<style>
    .formulaire {
        background-color: rgba(15, 26, 75, 0.911);
        color: rgba(255, 255, 255, 1);
        /* margin: 1em; */
        padding: 1em;
        width: 500px;
        border-radius: 5px;
        display: flex;
        flex-direction: column;
    }

    .message {
        background-color: rgba(15, 26, 75, 0.911);
        color: rgba(255, 255, 255, 1);
        padding: 1em;
    }
</style>