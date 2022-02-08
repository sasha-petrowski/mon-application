<template>
    <div>
    <input v-model="km" placeholder="km">
    <span>km</span>
    <div>
        <p>{{this.m}}</p>

        <p>{{this.cm}}</p>

        <p>{{this.mm}}</p>
    </div>
    </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  data: () => {
        return {
            km: 1,
        };
  },
  computed: {
      m(){
          return this.km * 100
      },
      cm(){
          return this.m * 100
      },
      mm(){
          return this.cm * 10
      }
  }  

})
</script>