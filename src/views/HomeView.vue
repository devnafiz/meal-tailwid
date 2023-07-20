<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import { computed, onMounted } from 'vue';
import store from '../store';
import axiosClient from '../axiosClient.js';



const letters ='ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
onMounted( async()=>{
 const response= axiosClient.get('list.php?i=list');
  console.log(response.data);
 
})
</script>

<template>
  <div class="flex flex-col items-center ">

     <input class="rounded border-2  border-gray-200 w-full justify-center" placeholder="Search for meals" type="text"/> 

     <div class="flex gap-2 mt-2 justify-center">
       <router-link :to="{name:'byLetter', params:{letter}}" v-for="letter of letters" :key="letter">
           {{ letter }}

       </router-link>

     </div>
    

  </div>
</template>
