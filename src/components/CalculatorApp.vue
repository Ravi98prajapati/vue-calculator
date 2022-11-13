<template>
  <div
    class="p-3"
    style="max-width: 400px; margin: 50px auto; background: #234"
  >
    <!-- Calculator Result -->
    <div
      class="w-full rounded m-1 p-3 text-right lead font-weight-bold text-white bg-black"
    >
      {{ calculatorValue || 0 }}
    </div>
    <!-- CALCULATOR  BUTTON -->
    <div class="row no-gutters">
      <div class="col-3" v-for="n in calculatorElement" :key="n">
        <div
          class="lead text-white text-center m-1 py-3 rounded hover-class"
          :class="{
            'bg-vue-green': ['C', '*', '/', '-', '+', '%', '.', '='].includes(
              n
            ),
          }"
          @click="action(n)"
        >
          {{ n }}
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
const calculatorValue = ref("");
const operator = ref(null);
const previousCalculatorValue = ref("");
const calculatorElement = [
  "C",
  "*",
  "/",
  "-",
  7,
  8,
  9,
  "+",
  4,
  5,
  6,
  "%",
  1,
  2,
  3,
  "=",
  0,
  ".",
];

const action = (n) => {
  console.log(n + "input");
  // APPEND VALUE
  if (!isNaN(n) || n === ".") {
    calculatorValue.value += n + "";
  }
  // CLEAR VALUE
  if (n === "C") {
    calculatorValue.value = "";
  }
  if (n === "%") {
    calculatorValue.value = calculatorValue.value / 100 + "";
  }
  if (["+", "-", "*", "/"].includes(n)) {
    operator.value = n;
    previousCalculatorValue.value = calculatorValue.value;
    calculatorValue.value = "";
  }
  if (n === "=") {
    calculatorValue.value = eval(
      previousCalculatorValue.value + operator.value + calculatorValue.value
    );
    previousCalculatorValue.value = "";
    operator.value = null;
  }
};
</script>
<style scoped>
.hover-class {
  cursor: pointer;
  background: #3d5875;
}
.bg-vue-green {
  background: green;
}
</style>
