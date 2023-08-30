<template>
  <div class=" flex justify-center gap-2 mt-3">
    <router-link :to="{name:'byLetter', params:{letter}}" v-for="letter of letters" :key="letter">
           {{ letter }}

       </router-link>
  </div>
  <div>
    <div class=" grid grid-cols-1 md:grid-cols-3 gap-3">
    <MealItem   v-for="meal in meals"  :key="meal.idMeal" :meal="meal"/>

  
  </div>
  </div>

</template>

<script setup>

import { computed, onMounted,ref,watch } from 'vue';
import store from '../store';
import axiosClient from '../axiosClient.js';
import { useRoute } from 'vue-router'
import MealItem from '../components/MealItem.vue'

const route =useRoute();


const letters ='ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
const ingradients =ref([])

const meals =computed(()=>store.state.mealsByLetter)

watch(route,()=>{
  store.dispatch('searchMealsByLetter',route.params.letter)

})

onMounted(()=>{

  store.dispatch('searchMealsByLetter',route.params.letter)
})

</script>