<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
import { computed } from 'vue';
import store from '../store';

const meals=computed(()=>store.state.meals)
</script>

<template>
   {{ meals }}
</template>
