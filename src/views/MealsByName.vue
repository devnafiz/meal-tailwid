<template>
  <div class=" p-8">
    <input v-model="keyword" @change="searchMeals" class="rounded border-2  border-gray-200 w-full justify-center" placeholder="Search for meals" type="text"/> 
  </div>

  <div>
   <div v-for="meal in meals" :key="meal.idMeal">
     <img :src="meal.strMealThumb" :alt="strMeal">
     <h3>{{ meal.strMeal }}</h3>
     <div>
      <a :href="meal.strYoutube" :traget="_blank"> youtube</a>
      <router-link to="/"> view</router-link>
     </div>

   </div>
  
  </div>

</template>

<script setup>

import { ref,computed} from 'vue'

import store from '../store'
const keyword= ref('');
const meals =computed(()=> store.state.searchedMeals);

function searchMeals() {
 store.dispatch('searchMeals',keyword.value)
}
</script>