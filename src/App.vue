<template>
  <div class="bg-cyan-light-gray h-screen lg:flex lg:items-center lg:justify-center lg:flex-col">
    <div class="header py-5 h-[14%] lg:h-fit lg:py-0 lg:pb-8">
      <h1 class="uppercase font-bold text-cyan-dark-gray tracking-[.3em] text-xl text-center">Spli<br>tter</h1>
    </div>

    <div class="card bg-white overflow-hidden h-[86%] lg:h-fit lg:w-4/6 lg:mx-auto rounded-tr-3xl rounded-tl-3xl p-6
    lg:flex lg:justify-between lg:rounded-3xl
    ">
      
      <div class="left-side lg:w-1/2">
        <div class="bill-section mb-3">
          <h1 class="font-bold text-cyan-dark-gray text-xs">Bill</h1>
    
          <div class="mt-2 relative">
            <input type="number" v-model="bill" class="form-control text-cyan-dark-gray text-right font-bold text-lg rounded-sm py-0 lg:py-1">
            <CurrencyDollarIcon class="absolute inset-2 h-4 w-4 lg:h-6 lg:w-6 text-cyan-dark-gray" />
          </div>
        </div>
  
        <div class="bill-section my-3 lg:my-5">
          <h1 class="font-bold text-cyan-dark-gray text-xs">Select Tip %</h1>
    
          <div class="mt-2 grid grid-cols-2 lg:grid-cols-3 gap-3">
            <button class="btn btn-primary text-lg" @click="calculateBill(5)">5%</button>
            <button class="btn btn-primary text-lg" @click="calculateBill(10)">10%</button>
            <button class="btn btn-primary text-lg" @click="calculateBill(15)">15%</button>
            <button class="btn btn-primary text-lg" @click="calculateBill(25)">25%</button>
            <button class="btn btn-primary text-lg" @click="calculateBill(50)">50%</button>
            <input v-model="custom" @change="calculateBill(custom)" type="number" class="form-control font-bold text-lg lg:text-xs text-right rounded-lg p-1" placeholder="Custom">
          </div>
        </div>
  
        <div class="bill-section my-5 lg:my-6">
          <h1 class="font-bold text-cyan-dark-gray text-xs">Number of People</h1>
    
          <div class="mt-2 relative">
            <small v-if="error" class="text-xs text-red-500 absolute right-0 -top-4">Can't be zero</small>
            <input type="number" v-model="numberOfPeople" :class="{'ring-1 ring-red-500 animate__animated animate__headShake': error}" class="form-control text-cyan-dark-gray text-right font-bold text-lg rounded-sm py-0 lg:py-2">
            <UserIcon class="absolute inset-2 lg:inset-3 h-3 w-3 lg:h-6 lg:w-6 text-cyan-dark-gray" />
          </div>
        </div>
      </div>

      <div class="card bg-cyan-dark pt-6 pb-4 px-4 lg:px-6 lg:ml-5 rounded-lg lg:w-1/2 lg:flex lg:flex-col">

        <div>
          <div class="flex justify-between align-center mb-3 lg:mb-8">
            <div>
              <h1 class="text-white font-semibold text-xs lg:text-md">Tip Amount</h1>
              <span class="text-cyan-light-gray text-xs lg:text-md">/person</span>
            </div>
  
            <h1 class="font-bold text-xl text-primary lg:text-2xl">${{ tipAmount.toFixed(2) }}</h1>
          </div>
  
          <div class="flex justify-between align-center">
            <div>
              <h1 class="text-white font-semibold text-xs lg:text-md">Total</h1>
              <span class="text-cyan-light-gray text-xs lg:text-md">/person</span>
            </div>
  
            <h1 class="font-bold text-xl text-primary lg:text-2xl">${{ total.toFixed(2) }}</h1>
          </div>
        </div>

        <button @click="reset" class="mt-auto btn btn-secondary w-full uppercase text-sm lg:text-lg">Reset</button>
      </div>

    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import type { Ref } from 'vue';
import { CurrencyDollarIcon } from "@heroicons/vue/24/outline";
import { UserIcon } from "@heroicons/vue/24/solid";

const bill = ref(0)
const custom: Ref<null | number> = ref(null)
const numberOfPeople = ref(1)
const tip = ref(0)
const tipAmount = ref(0)
const total = ref(0)
const error = ref(false)


function reset() {
  bill.value = 0;
  custom.value = null;
  numberOfPeople.value = 0
  tip.value = 0
  total.value = 0
}


function calculateBill(tipValue: number | null) {
  tip.value = tipValue ?? 0 // nullish coalescence.

  error.value = false

  if (!numberOfPeople.value) {
    error.value = true
    return
  }

  // Take amount; divide by number of people; add the tip (in percent.)
  let totalTip = (tip.value / 100) * bill.value
  let totalBill = bill.value + totalTip

  let totalPerPerson = totalBill / numberOfPeople.value
  let tipPerPerson = totalTip / numberOfPeople.value

  total.value = totalPerPerson
  tipAmount.value = tipPerPerson

}
</script>

<style scoped></style>
