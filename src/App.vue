<template>
  <div class="bg-cyan-light-gray h-screen">
    <div class="header py-5 h-[14%]">
      <h1 class="uppercase font-bold text-cyan-dark-gray tracking-[.3em] text-xl text-center">Spli<br>tter</h1>
    </div>

    <div class="card bg-white overflow-hidden h-[86%] rounded-tr-3xl rounded-tl-3xl p-6">

      <div class="bill-section mb-3">
        <h1 class="font-bold text-cyan-dark-gray text-xs">Bill</h1>
  
        <div class="mt-2 relative">
          <input type="number" class="form-control text-right font-bold text-lg rounded-sm py-0">
          <CurrencyDollarIcon class="absolute inset-2 h-4 w-4 text-cyan-dark-gray" />
        </div>
      </div>

      <div class="bill-section my-3">
        <h1 class="font-bold text-cyan-dark-gray text-xs">Select Tip %</h1>
  
        <div class="mt-2 grid grid-cols-2 gap-3">
          <button class="btn btn-primary text-lg">5%</button>
          <button class="btn btn-primary text-lg">10%</button>
          <button class="btn btn-primary text-lg">15%</button>
          <button class="btn btn-primary text-lg">25%</button>
          <button class="btn btn-primary text-lg">50%</button>
          <input type="number" class="form-control font-bold text-lg text-right rounded-lg p-1" placeholder="Custom">
        </div>
      </div>

      <div class="bill-section my-5">
        <h1 class="font-bold text-cyan-dark-gray text-xs">Number of People</h1>
  
        <div class="mt-2 relative">
          <input type="number" class="form-control text-right font-bold text-lg rounded-sm py-0">
          <UserIcon class="absolute inset-2 h-3 w-3 text-cyan-dark-gray" />
        </div>
      </div>

      <div class="card bg-cyan-dark pt-6 pb-4 px-4 rounded-lg">
        <div class="flex justify-between align-center mb-3">
          <div>
            <h1 class="text-white font-semibold text-xs">Tip Amount</h1>
            <span class="text-cyan-light-gray text-xs">/person</span>
          </div>

          <h1 class="font-bold text-xl text-primary">$4.27</h1>
        </div>

        <div class="flex justify-between align-center">
          <div>
            <h1 class="text-white font-semibold text-xs">Tip Amount</h1>
            <span class="text-cyan-light-gray text-xs">/person</span>
          </div>

          <h1 class="font-bold text-xl text-primary">$32.29</h1>
        </div>

        <button class="mt-4 btn btn-secondary w-full uppercase text-sm">Reset</button>
      </div>

    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { CurrencyDollarIcon } from "@heroicons/vue/24/outline";
import { UserIcon } from "@heroicons/vue/24/solid";

const result = ref(0);
</script>

<style scoped></style>
