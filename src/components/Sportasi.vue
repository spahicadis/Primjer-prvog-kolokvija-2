<script setup>
import {ref, reactive, computed, watch} from 'vue'

const sportasi = ref([
{
ime: 'Ivan',
disciplina: 'plivanje',
godine: 25,
natjecanja: ['Olimpijske igre', 'Svjetsko prvenstvo']
},
{
ime: 'Ana',
disciplina: 'atletika',
godine: 30,
natjecanja: ['Svjetsko prvenstvo', 'Europsko prvenstvo', 'Olimpijske igre']
},
{
ime: 'Marko',
disciplina: 'odbojka',
godine: 22,
natjecanja: ['Europsko prvenstvo']
}
])



watch(sportasi, () => {
  sportasi.value = sportasi.value.sort((a, b) => b.natjecanja.length - a.natjecanja.length)
}, {deep: true})



const novo_natjecanje = ref("")


const dodaj_natjecanje = (sportasIndex) => {
sportasi.value[sportasIndex].natjecanja.push(novo_natjecanje.value);
novo_natjecanje.value = "";
}

const ukloni_natjecanje = (sportasIndex, natjecanjeIndex) => {
  sportasi.value[sportasIndex].natjecanja.splice(natjecanjeIndex, 1)
}

</script>



<template>

<input
class="border"
v-model="novo_natjecanje"
/>
<div v-for="(sportas, indexSportas) in sportasi" class="w-[200px]">
  
 <p v-if="indexSportas === 0"><strong>🥇Ime:</strong> {{ sportas.ime }}</p>
 <p v-if="indexSportas === 1"><strong>🥈Ime:</strong> {{ sportas.ime }}</p>
 <p v-if="indexSportas === 2"><strong>🥉Ime:</strong> {{ sportas.ime }}</p>
 <p><strong>Godine:</strong> {{ sportas.godine }}</p>
 <p><strong>Disciplina:</strong> {{ sportas.disciplina }}</p>
 <div class="flex gap-2"><span><strong>Natjecanja:</strong></span><button v-on:click="dodaj_natjecanje(indexSportas)" class="border rounded-full">+</button></div> 
 <TransitionGroup name="list">
 <p v-for="(natjecanje, indexNatjecanje) in sportas.natjecanja" :key="indexNatjecanje">
  <button class="border p-1" @click="ukloni_natjecanje(indexSportas, indexNatjecanje)">-</button>  <span>{{ natjecanje }}</span>
 </p>
 </TransitionGroup>
 <hr/>


</div>



</template>


<style scoped>

.list-enter-active,
.list-leave-active {
transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
opacity: 0;
transform: translateX(30px);
}



</style>