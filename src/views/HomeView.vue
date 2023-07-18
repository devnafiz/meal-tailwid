<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import { computed } from 'vue';
import store from '../store';



const letters ='ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
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
