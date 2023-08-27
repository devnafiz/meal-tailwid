<template>
 <div class="max-w-[800px] mx-auto ">
   
    <h2 class=" mb-5 font-semibold mt-3 text-xl">{{ meal.strMeal }}</h2>
    <img :src="meal.strMealThumb" :alt="meal.strMeal"/>
    <div class=" grid grid-cols-1 md:grid-cols-3 text-lg py-2">
        <div>
            Category:{{ meal.strCategory }}
        </div>
        <div>
            Area:{{ meal.strArea }}
        </div>
        <div>
            Tags:{{ meal.strTags }}
        </div>
       
    </div>
    <div class="my-3 px-3">
        {{ meal.strInstructions }}
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2">
        <div >
            <h2 class="text-2x1 font-semibold mb-3">Ingridents</h2>

            <ul>
                <template v-for="(el, ind) of new Array(20)">
                    <li  v-if="meal[`strIngredient${ind +1}`]">{{ ind+1}}.{{ meal[`strIngredient${ind +1}`] }}</li>
                </template>
                
            </ul>
        </div>
        <div >
            <h2 class="text-2xl font-semibold mb-3">Measure</h2>
            <ul>
                <template v-for="(el, ind) of new Array(20)">
                    <li  v-if="meal[`strMeasure${ind +1}`]">{{ meal[`strMeasure${ind +1}`] }}</li>
                </template>
                
            </ul>
        </div>
        <div class="mt-4 mb-4">
                <YouTubeButton :href="meal.strYoutube"> Go to Youtube</YouTubeButton>
                    <a :href="meal.strSource" 
                    :traget="_blank" 
                    class="px-2 py-3 rounded border-2 text-white border-green-600 bg-green-600 hover:bg-green-600 hover:text-white transition-colors ml-2"> 
            View Original Source</a>

        </div>

    </div>
 </div>
</template>
<script setup>

import { ref, onMounted} from 'vue'
import { useRoute } from 'vue-router'
import axiosClient from '../axiosClient'
import YouTubeButton from '../components/YouTubeButton.vue'
const route = useRoute();
const meal = ref({})

onMounted(()=>{
   
    axiosClient.get(`lookup.php?i=${route.params.id}`)
    .then(({data})=>{
       
        meal.value=data.meals[0] || {}
    })

})
</script>