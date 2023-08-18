<template>
  <div class=" p-8">
    <input v-model="keyword" @change="searchMeals" class="rounded border-2  border-gray-200 w-full justify-center" placeholder="Search for meals" type="text"/> 
  </div>

</template>

<script setup>

import { ref} from 'vue'
import axiosClient from '../axiosClient'

const keyword= ref('');

function searchMeals() {
  axiosClient.get(`search.php?s=${keyword.value}`)
}
</script>