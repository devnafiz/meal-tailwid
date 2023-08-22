<template>
 <div>
      {{ meal }}
 </div>
</template>
<script setup>

import { ref, onMounted} from 'vue'
import { useRoute } from 'vue-router'
import axiosClient from '../axiosClient'
const route = useRoute();
const meal = ref([])

onMounted(()=>{
    axiosClient.get(`lookup.php?i =${route.params.id}`)
    .then(({data})=>{
        //debugger;
        meal.value=data
    })

})
</script>