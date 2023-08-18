<template>
  <div class=" p-8">
    <input v-model="keyword" @change="searchMeals" class="rounded border-2  border-gray-200 w-full justify-center" placeholder="Search for meals" type="text"/> 
  </div>

  <div>
   <pre>{{ meals }}</pre>
  
  </div>

</template>

<script setup>

import { ref,computed} from 'vue'
import axiosClient from '../axiosClient'
import store from '../store'
const keyword= ref('');
const meals =computed(()=> store.state.searchedMeals);

function searchMeals() {
 store.dispatch('searchMeals',keyword.value)
}
</script>