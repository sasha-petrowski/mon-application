<template>
  <div class="screen">{{ screen }}</div>
  <div class="screen">{{ result }}</div>
</template>

<script>
import { defineComponent } from "vue";
export default defineComponent({
  props: {
    result: {
      type: Number,
      default: 0,
    },
    leftOperator: {
      type: Number,
      default: 0,
    },
    rightOperator: {
      type: Number,
      default: 0,
    },
    operation: {
      type: String,
      default: "+",
    },
  },
  computed: {
    screen() {
      return `${this.leftOperatorScreen} ${this.operation} ${this.rightOperatorScreen} =`;
    },
    leftOperatorScreen() {
      return this.leftOperator === null ? 0 : this.leftOperator;
    },
    rightOperatorScreen() {
      return this.rightOperator === null ? 0 : this.rightOperator;
    },
  },
});
</script>

<style scoped>
.screen {
  /* background-color: gray; */
  color: white;
  background-color: rgba(255, 255, 255, 0.4);
  margin: 1em;
  vertical-align: middle;
}
</style>