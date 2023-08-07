<script setup lang="ts">

</script>

<template>
    <div class=" bg-gray-100 h-full">
        <header class=" bg-white shadow-md h-16 flex justify-center items-stretch">

            <router-link :to="{name:'home' }" class="inline-flex items-center h-full">Home</router-link>
            <div class=" flex items-center gap-2">
                <router-link to="/" class=" inline-flex items-center px-2 h-full hover:bg-slate-300">Search Meal</router-link>
                <router-link to="/"  class="inline-flex items-center px-2">Search Meal by Letter</router-link>
                <router-link to="/"  class="inline-flex items-center px-2"> Meals By Ingradients</router-link>
            </div>

        </header>
        <main>
            <router-view/>
        </main>
    </div>

</template>

<style scoped>

</style>
