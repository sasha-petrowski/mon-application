<template>
  <div class="calculator">
    <EcranCalculatrice
      :left-operator="leftOperator"
      :right-operator="rightOperator"
      :operation="operation"
      :result="result"
    />
    <div class="buttons">
      <BoutonCalculatrice
        v-for="operator in operators"
        :key="operator"
        :value="operator"
        @button-data="handleButtonClick"
      />
      
      <BoutonCalculatrice
        v-for="value in values"
        :key="value"
        :value="value"
        @button-data="handleButtonClick"
      />
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue';
import BoutonCalculatrice from './Calculatrice/BoutonCalculatrice.vue';
import EcranCalculatrice from './Calculatrice/EcranCalculatrice.vue';

export default defineComponent({
  data: () => {
        return {
            operators: ["+", "-", "=", "/", "*",'C'],
            values: Array.from({ length: 10 }, (index, number) => number),
            leftOperator: null,
            rightOperator: null,
            operation: "+",
            operatorClicked: false,
            result: 0,
        };
    },
    components: {
        BoutonCalculatrice,
        EcranCalculatrice,
    },
    methods: {
    handleButtonClick(buttonData) {
        if(buttonData === 'C') {
            this.reset();
            this.result = 0;
            return;
        }
      if (buttonData === "=") {
        this.result = this.calculateResult(
          this.leftOperator,
          this.operation,
          this.rightOperator
        );
        this.reset();
        this.leftOperator = this.result;
        return;
      }
      if (this.operators.includes(buttonData)) {
        this.operation = buttonData;
        this.operatorClicked = true;
      } else {
        if (!this.operatorClicked) {
          if (this.leftOperator === null) {
            this.leftOperator = buttonData;
          } else {
            this.leftOperator = parseInt(
              this.leftOperator.toString() + buttonData
            );
          }
        } else {
          if (this.rightOperator === null) {
            this.rightOperator = buttonData;
          } else {
            this.rightOperator = parseInt(
              this.rightOperator.toString() + buttonData
            );
          }
        }
      }
    },
    reset() {
      this.leftOperator = null;
      this.rightOperator = null;
      this.operation = '+';
      this.operatorClicked = false;
    },
    calculateResult(leftOperand, operation, rightOperand) {
      const left = leftOperand === null ? 0 : leftOperand;
      const right = rightOperand === null ? 0 : rightOperand;
      switch (operation) {
        case "+":
          return left + right;
        case "-":
          return left - right;
        case "*":
          return left * right;
        case "/":
          return left / right;
      }
    },
  },    
})
</script>


<style scoped>
.calculator {
  background-color: rgba(15, 26, 75, 0.911);
  /* margin: 1em; */
  padding: 1em;
  width: 200px;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
}
.buttons {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}
</style>