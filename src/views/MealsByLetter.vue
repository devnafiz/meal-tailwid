<template>
  <div class=" flex justify-center gap-2 mt-3">
    <router-link :to="{name:'byLetter', params:{letter}}" v-for="letter of letters" :key="letter">
           {{ letter }}

       </router-link>
  </div>
  <div>
    <pre>{{ meals }}</pre>
  </div>

</template>

<script setup>

import { computed, onMounted,ref } from 'vue';
import store from '../store';
import axiosClient from '../axiosClient.js';
import { useRoute } from 'vue-router'

const route =useRoute();


const letters ='ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
const ingradients =ref([])

const meals =computed(()=>store.state.mealsByLetter)

onMounted(()=>{

  store.dispatch('searchMealsByLetter',route.params.letter)
})

</script>