<template>
    <button v-on:click="sendValue(value)"> {{value}} </button>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    value:{
      type: [String, Number],
      default: 0
    },
  },  
  emits: ['button-data'],
  methods: {
    sendValue(data) {
      this.$emit('button-data', data);
    }
  },
});
</script>


<style scoped>
button {
  width: 50px;
}
</style>