<script setup>
import {ref, reactive, computed} from 'vue'


const props = defineProps({
  slikar: {
    type: String,
  },
  godina: {
    type: Number,
  },
  naslov: {
    type: String
  },
  slika: {
    type: String
  }
})

const starost = (godinaSlike) => {
const datum = new Date()
const godinaTrenutno = datum.getFullYear()

return godinaTrenutno - godinaSlike
}


</script>





<template>

<div>


  <img  @click="$emit('povecaj', slika)"  :src="slika" class="h-[100px]"/>
  <p>Naslov: {{ naslov }}</p>
  <p>Slikar: {{ slikar }}</p>
  <p :class="starost(godina) > 136 ? 'line-through' : ''" >Starost: {{ starost(godina) }}</p>


</div>





</template>