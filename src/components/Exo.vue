<template>
    <input v-model="input" placeholder="Nom">
    <button v-on:click="list.push(input)"> Ajouter </button>
    <button v-on:click="list.shift()"> Enlever </button>
    <ul v-if=" list.length <= 3">
        <li v-for="item in list" :key ="item">
            {{ item }}
        </li>
    </ul>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  data: () => {
    return {
        input: '',
        list: [],
    }
  },
})
</script>
