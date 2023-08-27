<template>
    
   <div  class=" bg-white shadow rounded-xl ">
    <router-link :to="{name: 'mealDetails',params:{id: meal.idMeal}}">
      <img :src="meal.strMealThumb" :alt="strMeal" class=" rounded-t-2xl w-full object-cover h-48">
    </router-link>
     
     <div class="p-3  ">
      <h3 class="px-2  font-semibold">{{ meal.strMeal }}</h3>
      <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. </p>
     <div class="px-2 py-3 flex item-center justify-between">
       <YouTubeButton :href="meal.strYoutube">You Tube</YouTubeButton>
      <router-link to="/" class="px-2 py-3 rounded border-2 border-purple-600 hover:bg-purple-600 hover:text-white transition-colors"> view</router-link>
     </div>

     </div>
     

   </div>
  
 
</template>
<script setup>
const {meal} =defineProps({
    meal:{
        required:true,
        type:Object
    }
})
</script>