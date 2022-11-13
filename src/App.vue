<template>
  <header>
    <div>
      <CalculatorApp />
    </div>
  </header>

  <RouterView />
</template>

<script setup>
import { RouterLink, RouterView } from "vue-router";

import CalculatorApp from "@/components/CalculatorApp.vue";
</script>
