<template>
  <div class=" p-8">
    <input v-model="keyword" @change="searchMeals" class="rounded border-2  border-gray-200 w-full justify-center" placeholder="Search for meals" type="text"/> 
  </div>

  <div class=" grid grid-cols-1 md:grid-cols-3 gap-3">
    <MealItem   v-for="meal in meals"  :key="meal.idMeal" :meal="meal"/>

  
  </div>

</template>

<script setup>

import { ref,computed,onMounted} from 'vue'
import YouTubeButton from '../components/YouTubebutton.vue'
import MealItem from '../components/MealItem.vue'

import store from '../store'
import { useRoute} from 'vue-router'
const keyword= ref('');
const route = useRoute();
const meals =computed(()=> store.state.searchedMeals);

function searchMeals() {
 store.dispatch('searchMeals',keyword.value)
}

onMounted(()=>{

 keyword.value =route.params.name
 if(keyword.value){
  searchMeals();
 }
})
</script>