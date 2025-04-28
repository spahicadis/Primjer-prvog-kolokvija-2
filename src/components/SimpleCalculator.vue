<script setup>
import { ref, computed } from 'vue'

const broj1 = ref()
const broj2 = ref()
const operacija = ref("")

const provjeraOperacije = computed(() => {

  if(operacija.value === 'zbrajanje') {
    return true
  }

  if(operacija.value === 'oduzimanje') {
    return true
  }

  if(operacija.value === 'mnozenje') {
    return true
  }

  if(operacija.value === 'dijeljenje') {
    return true
  }

  return false

})
//Razlika izmedu computed funkije i obicne u kontekstu ovog koda je ta sto se obicna funkcija koja je prije bila pozvila uvijek kada bi se neko stanje promjenilo neovisno da li je ono za nju bitno ili ne. Dok sada computed funkcija ce se pozivati samo kada se njezini dependency promjene odnosno varijabla operacija
</script>




<template>
<div class="max-w-md flex gap-3">
<input 
class="border"
v-model="broj1"
/>
<input 
class="border"
v-model="broj2"
/>
<input 
class="border"
v-model="operacija"
/>
</div>
<p v-if="!provjeraOperacije">Nepoznata operacija!</p>
<p v-if="provjeraOperacije && operacija === 'zbrajanje'">{{ Number(broj1) + Number(broj2) }}</p>
<p v-if="provjeraOperacije && operacija === 'oduzimanje'">{{ Number(broj1) - Number(broj2) }}</p>
<p v-if="provjeraOperacije && operacija === 'mnozenje'">{{ Number(broj1) * Number(broj2) }}</p>
<p v-if="provjeraOperacije && operacija === 'dijeljenje' && Number(broj2) !== 0">{{ Number(broj1) / Number(broj2) }}</p>
<p v-if="provjeraOperacije && operacija === 'dijeljenje' && Number(broj2) === 0">Dijeljenje s 0 nije moguće!</p>
</template>