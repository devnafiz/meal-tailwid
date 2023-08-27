<template>
  <div class=" p-8">
    <input v-model="keyword" @change="searchMeals" class="rounded border-2  border-gray-200 w-full justify-center" placeholder="Search for meals" type="text"/> 
  </div>

  <div class=" grid grid-cols-1 md:grid-cols-3 gap-3">
   <div v-for="meal in meals" :key="meal.idMeal"  class=" bg-white shadow rounded-xl ">
    <router-link :to="{name: 'mealDetails',params:{id: meal.idMeal}}">
      <img :src="meal.strMealThumb" :alt="strMeal" class=" rounded-t-2xl w-full object-cover h-48">
    </router-link>
     
     <div class="p-3  ">
      <h3 class="px-2  font-semibold">{{ meal.strMeal }}</h3>
      <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. </p>
     <div class="px-2 py-3 flex item-center justify-between">
       <YouTubeButton :href="meal.strYoutube"/>
      <router-link to="/" class="px-2 py-3 rounded border-2 border-purple-600 hover:bg-purple-600 hover:text-white transition-colors"> view</router-link>
     </div>

     </div>
     

   </div>
  
  </div>

</template>

<script setup>

import { ref,computed,onMounted} from 'vue'
import YouTubeButton from '../components/YouTubebutton.vue'

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