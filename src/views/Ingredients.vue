<template>
  <div>
    
    <div class=" grid grid-cols-1 md:grid-cols-3 gap-3">
      <router-link :to="{ 
      name: 'byIngredient',
      params:{ingredient:ingredient.idIngredient},
      }"
       v-for="ingredient of ingredients" :key="ingredient.idIngredient" class="bg-white rounded p-3">
        <h2 class=" text-2xl font-semibold pt-2">{{ ingredient.strIngredient }}</h2>
        <p>{{ ingredient.strDescription }}</p>
      

      </router-link>

  
  </div>
  </div>

</template>

<script setup>

import { onMounted, ref } from 'vue'
import axiosClient from '../axiosClient.js'


const ingredients= ref([])

onMounted(()=>{

  axiosClient.get('list.php?i=list')
  .then(({data})=>{
      
    ingredients.value=data.meals;
  })
})
</script>