<template>
    <a :href="href" :traget="_blank" class="px-2 py-3 rounded border-2 text-white border-red-600 bg-red-600 hover:bg-red-600 hover:text-white transition-colors"> 
     <slot></slot></a>
</template>

<script setup>
const props =defineProps({
    href: String
})
</script>