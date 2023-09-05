<template>

 <div>
    <div class=" grid grid-cols-1 md:grid-cols-3 gap-3">
    <MealItem   v-for="meal in meals"  :key="meal.idMeal" :meal="meal"/>

  
  </div>
  </div>
  <div v-if="!meals.length" class="flex justify-center bg-gray-100">

    <h3> no meal here</h3>

  </div>

</template>


<script setup>

const {meals}=defineProps({
	
	meals:{
	   required:true,
	   type:Object
	}
})

</script>