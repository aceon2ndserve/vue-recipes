<template>

    <div  class="bg-white shadow rounded-xl hover:scale-105 transition">
        <router-link :to="{name: 'mealDetails', params: {id: meal.idMeal}}">
            
            <img :src="meal.strMealThumb" :alt="meal.strMeal" class="rounded-t-xl h-48 w-full object-cover">
        </router-link>
        <div class="p-3">
            <h3 class="font-bold">{{ meal.strMeal }}</h3>
            <p class="mb-4">Lorem ipsum dolor sit amet consectetur adipisicing elit. Animi dignissimos quo atque sed inventore voluptatem architecto unde consectetur laudantium omnis! Rem quas cupiditate consequatur necessitatibus aperiam, sed natus possimus totam.</p>
            <div class="flex items-center justify-between">

                <YoutubeButton :href="meal.strYoutube">Youtube</YoutubeButton>
            </div>
        </div>
        
    </div>
        </template>
<script setup>

import YoutubeButton from './YoutubeButton.vue';
const {meal} = defineProps({
meal: {
    required: true,
    type: Object
}
})
</script>