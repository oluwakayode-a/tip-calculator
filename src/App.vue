<template>
  <div class="bg-cyan-light-gray h-screen">
    <div class="header py-6 h-1/6">
      <h1 class="uppercase font-bold text-cyan-dark-gray tracking-widest text-2xl text-center">Spli<br>tter</h1>
    </div>

    <div class="card bg-white overflow-hidden h-5/6 rounded-tr-3xl rounded-tl-3xl p-6">

      <div class="bill-section my-4">
        <h1 class="font-bold text-cyan-dark-gray">Bill</h1>
  
        <div class="mt-2 relative">
          <input type="number" class="form-control text-right font-bold text-lg">
          <CurrencyDollarIcon class="absolute inset-3 h-6 w-6 text-cyan-dark-gray" />
        </div>
      </div>

      <div class="bill-section my-6">
        <h1 class="font-bold text-cyan-dark-gray">Select Tip %</h1>
  
        <div class="mt-2 grid grid-cols-2 gap-3">
          <button class="btn">5%</button>
          <button class="btn">10%</button>
          <button class="btn">15%</button>
          <button class="btn">25%</button>
          <button class="btn">50%</button>
          <input type="number" class="form-control font-bold text-lg" placeholder="Custom">
        </div>
      </div>

    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { CurrencyDollarIcon } from "@heroicons/vue/24/outline";

const result = ref(0);
</script>

<style scoped></style>
