<script setup>
import { ref, computed, reactive } from 'vue'
import Slika from '@/components/Slika.vue'
const galerija = [
{
slikar: "Pablo Picasso",
godina: 1903,
naslov: "The Old Guitarist",
slika: "/src/assets/slike/The Old Guitarist.png"
},
{
slikar: "Vincent van Gogh",
godina: 1886,
naslov: "Le Moulin de Blute-Fin",
slika: "/src/assets/slike/Le Moulin de Blute-Fin.png"
},
{
slikar: "Hokusai",
godina: 1890,
naslov: "Courtesan Asleep",
slika: "/src/assets/slike/Courtesan Asleep.png"
},
];

let povecanaSlika = ref()

const handlePovecanaSlika = (slika) => {
  povecanaSlika.value = slika

 
}


</script>




<template>


  <Slika
  v-for="slika in galerija"
  :slika="slika.slika"
  :naslov="slika.naslov"
  :slikar="slika.slikar"
  :godina="slika.godina"
  @povecaj="handlePovecanaSlika"
  />
  <div>
  <img :src="povecanaSlika">

</div>

</template>